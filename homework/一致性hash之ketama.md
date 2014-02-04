

    在缓存应用中最常规的方式莫过于Hash取模的方式。比如集群中可用机器数N，那么key值为K的数据请求应该路由到Hash(K) mod N对应的机器。的确，这种结构是简单实用的。但是随着系统访问压力的增长，缓存系统不得不通过增加机器节点的方式提高集群的响应速度和数据承载量。增加机器意味着按照Hash取模的方式，大量的缓存命不中，缓存数据需要重新建立，瞬间会给DB带来极高的负载，甚至导致DB服务器宕机。本文介绍的一致性哈希技术可以很好的解决这个问题。

## 一致性哈希(Consistent Hashing)
一致性哈希的定义除了描述一个定义或者一种想法并没有给出任何实现方面的描述。但一般的实现思路如下:
1 假定哈希的均匀Key分布在一个环上，比如所有节点都通过SHA-1或MD5进行哈希映射
2 所有的节点也都分布在同一环上（比如Server的IP地址经过SHA-1)
3 每个节点只负责一部分Key，当节点加入、退出时只影响加入退出的节点和其邻居节点或者其他节点只有少量的Key受影响
4 假如有n个节点，m个key，当节点增加时大约有O(m/n)的节点需要移动

##一般一致性哈希需要满足下面几个条件：
* 平衡性(Balance)：哈希算法要均匀分布，不能有明显的映射规律，这对一般的哈希实现也是必须的
* 单调性(Monotonicity)：有新节点加入时，已经存在的映射关系不能发生变化
* 分散性(Spread)：避免不同的内容映射到相同的位置和相同的内容映射到不同的位置
其实一致性哈希（哈希）有个明显的优点就是负载均衡，只要哈希函数设计得当，每个点就是对等的可以均匀地分布系统负载。

##Memcached中一致性哈希的运用
Memcached使用了一致性哈希，支持动态对其增减节点。 Memcached在其客户端实现哈希策略，因此不同的客户端实现也有区别，以Spymemcache、Xmemcache为例，都是使用了ketama作为其实现。

##ketama实现方式如下：
1 将服务器列表(如 1.2.3.4:11211, 5.6.7.8:11211)的每项进行MD5哈希，结果为一个160bit的数字，取其前32位作为一个整数
2 通常服务器数量比较少，通过给每项增加序列号后缀，每项再虚拟出100~200新项，再MD5哈希
3 这些MD5哈希生成的整数将均匀分布在一个0~2^32数字环上
4 把缓存对象的Key也进行MD5哈希，同样得到一个整数。用该整数去匹配应该存在那个服务器上

##详细步骤如下：
1. Hash机器节点
首先求出机器节点的Hash值，然后将其分布到0～2^32的一个圆环上（顺时针分布）。A , B, C, D, E 5台机器通过Hash算法将其分布上图环上

2. 查找机器节点，访问缓存
有一个写入缓存的请求，其Key为K，计算器Hash值Hash(K)， Hash(K) 对应于上图环中的某一个点，如果该点对应没有映射到具体的某一个机器节点，那么顺时针查找，直到第一次找到有映射机器的节点，该节点就是确定的目标节点。如果超过了2^32仍然找不到节点，则命中第一个机器节点。比如 Hash(K) 的值介于A~B之间，那么命中的机器节点应该是B节点（如上图）。

3. 新增机器节点
在原有集群的基础上欲增加一台机器F：计算机器节点的Hash值，将机器映射到环中的一个节点。增加机器节点F之后，访问策略不改变，依然按照第2步方式访问，此时缓存命不中的情况依然不可避免，不能命中的数据是Hash(K)在增加节点以前落在C～F之间的数据。尽管依然存在节点增加带来的命中问题，但是比较传统的Hash取模的方式，一致性哈希已经将不命中的数据降到了最低，最大限度地抑制了Hash键的重新分布。

4. 虚拟节点（virtual nodes）
实际应用中，为了取得比较好的负载均衡效果，往往在第1步Hash机器节点时要引入虚拟节点（virtual nodes），原因是哈希虽然是随机的，但当服务器（节点）数较少的情况下 （例如只有3台），通过Hash(key)算出节点的哈希值在圆环上并不是均匀分布的（稀疏的），仍然会出现各节点负载不均衡的问题。
绝大多数Key会映射到Server1。虚拟节点就是为每个物理节点（服务器）在圆上多分配100～200个点。这样就能抑制分布不均匀，最大限度地减小服务器增减时的缓存重新分布。有虚节点后的环如下，新增的同名节点即为虚拟节点。

##Spy Memcached中的代码为例来说明这种算法的使用
该client采用TreeMap存储所有节点，模拟一个环形的逻辑关系。在这个环中，节点之前是存在顺序关系的，所以TreeMap的key必须实现Comparator接口。 
那节点是怎样放入这个环中的呢？ 
```Java    
//对所有节点，生成nCopies个虚拟结点  
        for(Node node : nodes) {  
            //每四个虚拟结点为一组，为什么这样？下面会说到  
            for(int i=0; i<nCopies / 4; i++) {  
                //getKeyForNode方法为这组虚拟结点得到惟一名称  
                byte[] digest=HashAlgorithm.computeMd5(getKeyForNode(node, i));  
            /** Md5是一个16字节长度的数组，将16字节的数组每四个字节一组， 
                        分别对应一个虚拟结点，这就是为什么上面把虚拟结点四个划分一组的原因*/  
                for(int h=0;h<4;h++) {  
                  //对于每四个字节，组成一个long值数值，做为这个虚拟节点的在环中的惟一key  
                    Long k = ((long)(digest[3+h*4]&0xFF) << 24)  
                        | ((long)(digest[2+h*4]&0xFF) << 16)  
                        | ((long)(digest[1+h*4]&0xFF) << 8)  
                        | (digest[h*4]&0xFF);  
                      
                    allNodes.put(k, node);  
                }  
            }  
        }  
```
上面的流程大概可以这样归纳:四个虚拟结点为一组，以getKeyForNode方法得到这组虚拟节点的name，Md5编码后，每个虚拟结点对应Md5码16个字节中的4个，组成一个long型数值，做为这个虚拟结点在环中的惟一key。第12行k为什么是Long型的呢？呵呵，就是因为Long型实现了Comparator接口。 

处理完正式结点在环上的分布后，可以开始key在环上寻找节点的游戏了。 
对于每个key还是得完成上面的步骤:计算出Md5，根据Md5的字节数组，通过Kemata Hash算法得到key在这个环中的位置。 
```Java  
        final Node rv;  
        byte[] digest = hashAlg.computeMd5(keyValue);  
        Long key = hashAlg.hash(digest, 0);  
        //如果找到这个节点，直接取节点，返回  
        if(!ketamaNodes.containsKey(key)) {  
        //得到大于当前key的那个子Map，然后从中取出第一个key，就是大于且离它最近的那个key  
            SortedMap<Long, Node> tailMap=ketamaNodes.tailMap(key);  
            if(tailMap.isEmpty()) {  
                key=ketamaNodes.firstKey();  
            } else {  
                key=tailMap.firstKey();  
            }  
            //在JDK1.6中，ceilingKey方法可以返回大于且离它最近的那个key  
            //For JDK1.6 version  
//          key = ketamaNodes.ceilingKey(key);  
//          if (key == null) {  
//              key = ketamaNodes.firstKey();  
//          }  
        }   
        rv = allNodes.get(key);  
```
取节点逻辑:在环上顺时针查找，如果找到某个节点，就返回那个节点;如果没有找到，则取整个环的第一个节点。








ketama项目地址：https://github.com/RJ/ketama

参考地址：
http://blog.csdn.net/icycolawater/article/details/7255109
http://blog.csdn.net/is0501xql/article/details/8212098
http://www.iteye.com/topic/684087
