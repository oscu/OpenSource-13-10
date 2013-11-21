# 云计算中的分布式文件系统GFS与TFS #

    小组成员： 
    	张琦 zhangqi-gy4  
    	马晓明   mxm1123 
    	张剑  jianzhangup
    	路帅 lushuai2013 
# 摘要 #
云计算是一种基于互联网提供服务的网络应用模式，它能够实现IT基础设施以及服务的资源化和服务化，用户可以按需进行定制和付费，从而彻底改变了传统IT基础设施的交付和使用模式，有效解决了无限增长的海量信息存储和计算问题，并仅需为此付出廉价的购买成本。分布式作为云计算两大核心技术之一，被广泛应用于网络架构中。本文给出了云计算分布式文件系统的主要类型，着重分析了Google文件系统（GFS)和淘宝分布式文件系统（TFS)的工作原理。

----------

# 1.分布式文件系统（DFS，Distributed File System） #
大数据在今天吸引了大量关注，个人、企业和政府机构之间的互动创造了数据的海洋，通过有效识别、访问、筛选和分析其中部分数据能带来新的见解和益处。大数据需要大量的储存空间，先进的存储基础设施必不可少，需要能在多台服务器上伸缩自如的存储解决方案。而分布式文件系统为整个企业网络上的文件系统资源提供了一个逻辑树结构。用户可以抛开文件的实际物理位置，仅通过一定的逻辑关系就可以查找和访问网络的共享资源。用户能够像访问其他本地文件一样，访问分布在网络上多个服务器上的文件。这其中有许多优秀的分布式文件系统，本文以GFS和TFS为例进行介绍：


- ## GFS ##
        
	GFS文件系统（Google File System，GFS）是构建在便宜的服务器之上的大型散布式系统。它为Google云计算提供海量存储，并且与Chubby、MapReduce以及Bigtable等技术结合十分紧密，处于所有核心技术的底层,是google公司为了存储海量搜索数据而设计的专用文件系统。   

- ## TFS ##
    
 	TFS（Taobao !FileSystem）是一个高可扩展、高可用、高性能、面向互联网服务的分布式文件系统，主要针对海量的非结构化数据，它构筑在普通的Linux机器集群上，可为外部提供高可靠和高并发的存储访问。TFS为淘宝公司提供的海量小文件存储系统，通常文件大小不超过1M，满足了淘宝对小文件存储的需求，是构筑在普通的Linux机器集群上，可为外部提供高可靠和高并发的的存储访问。

----------

# 2.分布式文件系统的工作原理 #
**2.1 架构设计**


- GFS  
      GFS的系统架构如图所示。GFS将整个系统的节点分为三个角色：Client（客户端）、Master（主服务器）和Chunk Server（数据块服务器）。 
     
     
	 **1.Client**是GFS提供给应用程序的访问接口。
      
     **2.Master**是GFS的管理节点，在逻辑上只有一个，保存了系统的元数据，负责整个文件系统的管理
     
     **3.Chunk Server**负责具体的存储工作，Chunk Server的个数直接决定了GFS的规模。GFS将文件按照固定大小进行分块，默认是64MB，每一块称为一个Chunk（数据块），每个Chunk都有一个对应的索引号（Index）   
        
对于Master来说，每一个Chunk Server只是一个存储空间。Client发起的所有操作都需要通过Master才能执行。Chunk Server之间没有任何关系。Master维护了一个统一的命名空间，掌控了所有的Chunk Server的情况。但这样由一个Master来管理会带来相应的问题，比如在Master上可能会出现情况问题和单点问题，因此需要对Master做远程备份、控制信息和数据分流等操作。
        

   ![](http://d.hiphotos.baidu.com/baike/c0%3Dbaike92%2C5%2C5%2C92%2C30/sign=3513d1f13c6d55fbd1cb7e740c4b242f/8cb1cb1349540923ced0de519358d109b2de9c82d158515f.jpg)  

   - TFS  
       一个TFS集群由两个NameServer节点(一主一备)和多个DataServer节点组成。
       - NameServer节点负责维护block与DataServer节点的关系，包括DataServer节点的加入、退出、心跳信息、Block和DataServer的对应关系的建立与解除。
       - DataServera节点存储真正的Block,会有多个独立DataServer进程存在，每个进程负责管理一个挂载点，这个挂载点一般就是一个独立磁盘上的文件目录，以降低单个磁盘损坏带来的影响。
         
        在TFS中，将大量的小文件合并成一个大文件，这个大文件称为Block,每个Block拥有在集群内唯一的编号(Block Id),Block的大小可以通过配置项来决定，通常使用的块大小为64M。
        每一个block中存储许多不同的小文件，DataServer进程会给Block中的每个小文件分配一个File Id,并将每个文件在Block中的信息存放和Block对应的Index文件中。  
 ![](http://c.hiphotos.baidu.com/baike/c0%3Dbaike80%2C5%2C5%2C80%2C26/sign=30818442bf096b63951456026d5aec21/fc1f4134970a304e1fd8e397d0c8a786c8177f3e66097cd8.jpg)  

**2.2 存储机制**

   - GFS  
     GFS将文件按照固定的大小进行分块管理，默认为64MB,每一块称为一个chunk,每一个chunk都有一个索引号。这样GFS就实现了控制流和数据流的分离。Client和Master之间只有控制流而无数据流，降低了Master的负载。Client和Chunk Server之间直接传输数据流，Client可以同时访问多个Chunk Server,从而提高了I/O性能。

   - TFS   
     在TFS中，将大量的小文件(实际用户文件)合并成为一个大文件，这个大文件称为块(Block)。TFS以Block的方式组织文件的存储。每一个Block在整个集群内拥有唯一的编号，这个编号是由NameServer进行分配的，而DataServer上实际存储了该Block。  
     在NameServer节点中存储了所有的Block的信息，一个Block存储于多个DataServer中以保证数据的冗余。所有的请求，均先由NameServer节点选择合适的DataServer节点返回给客户端，再在对应的DataServer节点上进行数据操作。
  
**2.3 缓存机制**  

   - GFS   
     GFS根据应用的特点不实现缓存功能，由于客户端不存在大量的重复读写，因此这部分数据对系统整体的提升做用不大。对于Master服务器来说，Master需要对其元数据进行频繁操作，为了操作效率，这些元数据直接全部保存在内存中进行操作。对于Chunk Servere服务器来说，由于Chunk Server服务器数量较多，并且在GFS中各个Chunk Server和稳定性是无法确保的，如果将数据放到内存当中进行管理，会使得数据之间具有较为复杂的一致性问题。
   - TFS
     在这里写写

**2.4 容错机制**

   - GFS
     - Master容错  
       - Master上保存整个文件系统的目录结构、Chunk与文件名的映射表以及Chunk副本的位置。
       - 通过操作日志加checkpoint的方式进行，并且有一台实时热备
	   - Master的修改操作遵循先记录操作日志，后修改内存，并执行实时热备，所有的元数据修改操作都必须保证发送到实时热备才算成功。
     - Chunk Server容错  
       - GFS采用多个副本的方式实现Chunk Server的容错，每一个Chunk默认有三个副本，分布在不同的Chunk Server上，所有副本全部写入成功，才能视为真正的成功。如果副本出现丢失情况，Master会自动将该副本复制到其他的Chunk Server上。
       - Chunk Server会对存储的数据维持校验和。当读取一个chunk副本时，Chunk Server会将读取的数据和校验和进行比较，如果不匹配，就会返回错误，客户端将选择其他Chunk Server上的副本。
   - TFS
     - 集群容错
       - TFS可以配置主辅集群，分别放在两个不同的机房。主集群提供所有的功能，辅集群只提供读。当主集群的每个数据变更都会重新放到辅集群。这样既提供了负载均衡，又可以在主集群机房出现异常的情况不会中断或者丢失数据。
     - NameServer容错
       - NameServer采用了HA结构，即两台机器互为热备，同时运行，一主一备，主机绑定到对外vip，提供服务；主NameServer上的操作会重放到备NameServer上，一但主机宕机，迅速将vip绑定至备NameServer，对外提供服务。
     - DataServer容错
       - TFS采用Block存储多分的方式来实现DataServer容错。每个Block会存在多份，一般为3份，并且是分布在不同的DataServer上。每一个写入，必须在所有的Block写入成功才算成功。
       
**2.5 负载均衡**
	
- GFS
	- GFS会避免同一个chunk的所有副本都存放在同一个机架上的情况。选择chunk副本的初始位置根据如下因素：
		- 新副本所在的Chunk Server的磁盘利用率低于平均水平
		- 限制每个Chunk Server“最近”创建的数量；
		- 每个chunk的所有副本不能在同一个机架；
	- 当Chunk的副本数量小于一定的数量后，Master会尝试重新复制一个chunk副本
	- Master会定期扫描当前副本的分布情况，如发现磁盘使用量或机器负载不均衡，将执行重新平衡操作
- TFS
	- NameServer会根据DataServer容量的比率和DataServer的负载决定新数据写往哪台DataServer的服务器。根据写入策略，容量较小，负载较轻的服务器新数据写入的概率比较高。同时，NameServer会对DataServer上的Block进行均衡，使之尽早达到均衡。
	- 均衡计划，根据每台机器拥有的blocks平均数量，将其划分为移动源和移动目的：
		- 移动目的的选择：1.一个block的移动源和目的，应保持在同一网段内，也就是与另外的block不同网段；2.在作为目的的一定机器内，优先选择同机器的源到目的之间移动，也就是同台DataServer服务器中的不同DataServer进程。
	 
----------

# 3.社区 #
> - TFS：  
>   [TaoBao http://code.taobao.org/p/tfs/wiki/index/](http://code.taobao.org/p/tfs/wiki/index/)  
>   [GitHub https://github.com/alibaba/tfs](https://github.com/alibaba/tfs)  

> - GFS：  
> [http://en.wikipedia.org/wiki/Google_File_System](http://en.wikipedia.org/wiki/Google_File_System "Google File System")


----------

# 4.成功案例 #
>    - TFS  
>         [淘宝 http://www.taobao.com](http://www.taobao.com "淘宝")
>         
>    - GFS  
>         [谷歌 http://www.google.com](http://www.google.com)  
> 	  [Gmail http://gmail.google.com](http://gmail.google.com)   
> 	  [YouTube http://www.youtube.com](http://www.youtube.com)

----------

# 5.结束语 #
可以将云计算系统看作是一个服务器农场，它既包含诸多服务器，同时又要为多个用户服务。为确保高可靠性、经济性和可用性，云计算通常使用分布式文件系统来存储数据，采用冗余备份的方法来提高数据存储的可靠性。在云计算系统中,常用的数据存储系统包括 Google 公司的 GFS Google 文件系统 和 淘宝开发的TFS。可以说，分布式文件系统是整个云计算的基石，能够为上层数据库系统（如 BigTable 和 HBase）提供高效可靠的数据存储。

----------

# 6.参考资料 #
> 1.郎为民. 大话云计算 M . 北京 人民邮电出版社,2011.  
> 2.《Google 文件系统》  2003 年 10 月
> 3.Hadoop实战 机械工业出版社
> 4.淘宝技术这十年  电子工业出版
