# memcached VS redis #

	OpenSource122：
  	刘健 ticnic
	崔灿 finecci
	石占伟 szw007
	任峰杰

## 项目介绍 ##
### memcached ###
#### 简介 ####
memcached是一套分布式的高速缓存系统，由LiveJournal的Brad Fitzpatrick开发，目前被许多网站使用。这是一套开放源代码软件，以BSD license授权发布。
memcached缺乏认证以及安全管制，这代表应该将memcached服务器放置在防火墙后。
memcached的API使用三十二比特的循环冗余校验（CRC-32）计算键值后，将数据分散在不同的机器上。当表格满了以后，接下来新增的数据会以LRU机制替换掉。由于memcached通常只是当作高速缓存系统使用，所以使用memcached的应用程序在写回较慢的系统时（像是后端的数据库）需要额外的代码更新memcached内的数据。

#### 客户端支持 ####
Memcached的客户端软件实现非常多，包括C/C++, PHP, Java, Python, Ruby, Perl, Erlang, Lua等。

#### 安装方法 ####
在Window系统下，Memcached的安装非常方便，只需从以上给出的地址下载可执行软件然后运行memcached.exe –d install即可完成安装。在Linux等系统下，我们首先需要安装libevent，然后从获取源码，make && make install即可。默认情况下，Memcached的服务器启动程序会安装到/usr/local/bin目录下。在启动Memcached时，我们可以为其配置不同的启动参数。

#### 使用单位 ####
* Digg
* Facebook（同时也回馈了许多代码）
* Meetup.com（提供memcached对Java的连接库）
* Slashdot
* Wikipedia

### redis ###
#### 简介 ####
Redis是一个开源、支持网络、基于内存、键值对存储数据库，使用ANSI C编写。其开发由VMware主持。Redis使用C语言开发，在大多数像Linux、BSD和Solaris等POSIX系统上无需任何外部依赖就可以使用。
Redis是一个key-value存储系统。和Memcached类似，它支持存储的value类型相对更多，包括string(字符串)、list(链表)、set(集合)、zset(sorted set --有序集合)和hash（哈希类型）。这些数据类型都支持push/pop、add/remove及取交集并集和差集及更丰富的操作，而且这些操作都是原子性的。在此基础上，redis支持各种不同方式的排序。与memcached一样，为了保证效率，数据都是缓存在内存中。区别的是redis会周期性的把更新的数据写入磁盘或者把修改操作写入追加的记录文件，并且在此基础上实现了master-slave(主从)同步。

#### 客户端支持 ####
Redis支持的客户端语言非常丰富，常用的计算机语言如C、C#、C++、Object-C、PHP、Python、Java、Perl、Lua、Erlang等均有可用的客户端来访问Redis服务器。

#### 安装方法 ####
Redis的安装非常方便，只需从[http://redis.io/download](http://redis.io/download)获取源码，然后make && make install即可。默认情况下，Redis的服务器启动程序和客户端程序会安装到/usr/local/bin目录下。在启动Redis服务器时，我们需要为其指定一个配置文件，缺省情况下配置文件在Redis的源码目录下，文件名为redis.conf。

#### 使用单位 ####
* 新浪
* 淘宝
* GitHub
* Pinterest
* Stack Overflow
* Flickr
* Instagram
* Twitter

## 功能比较 ##

1. 网络IO模型
  -  Memcached是多线程，非阻塞IO复用的网络模型，分为监听主线程和worker子线程，监听线程监听网络连接，接受请求后，将连接描述字pipe 传递给worker线程，进行读写IO, 网络层使用libevent封装的事件库，多线程模型可以发挥多核作用，但是引入了cache coherency和锁的问题，比如，Memcached最常用的stats 命令，实际Memcached所有操作都要对这个全局变量加锁，进行计数等工作，带来了性能损耗。
  -  Redis使用单线程的IO复用模型，自己封装了一个简单的AeEvent事件处理框架，主要实现了epoll、kqueue和select，对于单纯只有IO操作来说，单线程可以将速度优势发挥到最大，但是Redis也提供了一些简单的计算功能，比如排序、聚合等，对于这些操作，单线程模型实际会严重影响整体吞吐量，CPU计算过程中，整个IO调度都是被阻塞住的。

2. 内存管理方面
  - Memcached使用预分配的内存池的方式，使用slab和大小不同的chunk来管理内存，Item根据大小选择合适的chunk存储，内存池的方式可以省去申请/释放内存的开销，并且能减小内存碎片产生，但这种方式也会带来一定程度上的空间浪费，并且在内存仍然有很大空间时，新的数据也可能会被剔除，原因可以参考Timyang的文章：http://timyang.net/data/Memcached-lru-evictions/
  - Redis使用现场申请内存的方式来存储数据，并且很少使用free-list等方式来优化内存分配，会在一定程度上存在内存碎片，Redis跟据存储命令参数，会把带过期时间的数据单独存放在一起，并把它们称为临时数据，非临时数据是永远不会被剔除的，即便物理内存不够，导致swap也不会剔除任何非临时数据（但会尝试剔除部分临时数据），这点上Redis更适合作为存储而不是cache。

3. 数据一致性问题
  - Memcached提供了cas命令，可以保证多个并发访问操作同一份数据的一致性问题。 
  - Redis没有提供cas 命令，并不能保证这点，不过Redis提供了事务的功能，可以保证一串 命令的原子性，中间不会被任何操作打断。

4. 存储方式及其它方面
  - Memcached基本只支持简单的key-value存储，不支持枚举，不支持持久化和复制等功能
  - Redis除key/value之外，还支持list,set,sorted set,hash等众多数据结构，提供了KEYS进行枚举操作，但不能在线上使用，如果需要枚举线上数据，Redis提供了工具可以直接扫描其dump文件，枚举出所有数据，Redis还同时提供了持久化和复制等功能。

5. 关于不同语言的客户端支持   
   在不同语言的客户端方面，Memcached和Redis都有丰富的第三方客户端可供选择，不过因为Memcached发展的时间更久一些，目前看在客户端支持方面，Memcached的很多客户端更加成熟稳定，而Redis由于其协议本身就比Memcached复杂，加上作者不断增加新的功能等，对应第三方客户端跟进速度可能会赶不上，有时可能需要自己在第三方客户端基础上做些修改才能更好的使用。
根据以上比较不难看出，当我们不希望数据被踢出，


## 其他比较 ##

## 结合自身需要评估后的结论 ##
* 没有必要过多的关心性能，因为二者的性能都已经足够高了。由于Redis只使用单核，而Memcached可以使用多核，所以在比较上，平均每一 个核上Redis在存储小数据时比Memcached性能更高。而在100k以上的数据中，Memcached性能要高于Redis，虽然Redis最近 也在存储大数据的性能上进行优化，但是比起Memcached，还是稍有逊色。说了这么多，结论是，无论你使用哪一个，每秒处理请求的次数都不会成为瓶 颈。（比如瓶颈可能会在网卡）

* 如果要说内存使用效率，使用简单的key-value存储的话，Memcached的内存利用率更高，而如果Redis采用hash结构来做key-value存储，由于其组合式的压缩，其内存利用率会高于Memcached。当然，这和你的应用场景和数据特性有关。

* 如果你对数据持久化和数据同步有所要求，那么推荐你选择Redis，因为这两个特性Memcached都不具备。即使你只是希望在升级或者重启系统后缓存数据不会丢失，选择Redis也是明智的。

* 当然，最后还得说到你的具体应用需求。Redis相比Memcached来说，拥有更多的数据结构和并支持更丰富的数据操作，通常在 Memcached里，你需要将数据拿到客户端来进行类似的修改再set回去。这大大增加了网络IO的次数和数据体积。在Redis中，这些复杂的操作通 常和一般的GET/SET一样高效。所以，如果你需要缓存能够支持更复杂的结构和操作，那么Redis会是不错的选择。

* 个人认为,memcached只是缓存系统,它适合用于,从数据库调数据写入memcached,客户从memcached读取数据的操作,要求key值比较稳定,value 最好大小不一. 适合作搜索这种纯读操作.

* redis有写的操作,但是有些问题,如果只用一台服务器的话,还好说,可以将内存快照当成本地数据库,但多台服务器呢,就要有分库策略,但redis为快速读写提供了实现可能,适合用于论坛应用.

* 个人总结一下，有持久化需求或者对数据结构和处理有高级要求的应用，选择redis，其他简单的key/value存储，选择memcache。

## 组员贡献 ##
* 刘健 ticnic 参与章节：整体结构、项目介绍
* 崔灿 finecci 参与章节：功能比较
* 石占伟 szw007 参与章节：结合自身需要评估后的结论
* 任峰杰 参与章节：                                                            

## 参考资料 ##
* [百度百科](http://baike.baidu.com/)
* [维基百科](http://zh.wikipedia.org/)
* [谈谈Memcached与Redis(一)](http://blog.sina.com.cn/s/blog_48c95a1901016903.html)
* [谈谈Memcached与Redis(二)](http://blog.sina.com.cn/s/blog_48c95a190101693p.html)
