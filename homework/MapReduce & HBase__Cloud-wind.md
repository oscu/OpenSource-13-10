# MapReduce & HBase #
组名： 王兴朝
      王彬
      邱丹
      盛敏智

## 项目介绍 ##
我们知道Hadoop是一个能够对大亮数据进行分布式处理的软件框架，实现Google了的MapReduce编程模型和框架，能够把应用程序分割成许多小的工作单元，并把这些单元放到任何集群节点上执行。 

在MapReduce中，一个准备提交执行的应用程序称为“作业（job）”， 而从一个作业划分出的、运行于各个计算节点的工作单元称为“任务task”。此外，Hadoop提供的分布式各个系统（HEFS）主要负责各个节点上的数据存储，并实现了高吞吐率的数据读写， 我们小组主要介绍的是Hadoop中两个重要的技术，一个是MapReduce;另一个是HBase；

对于HBase的了解，需要先掌握HDFS的技术，接下来，我简短的说明一下HDFS的一些核心思想。

在分布式存储和分布式计算方面，Hadoop都是用主/从（Master/Slave）架构， 在一个配置完整的集群上想让Hadoop这头大象奔跑起来， 需要在集群中运行一系列后台的程序。在不同的后台程序扮演不同的角色， 这些角色有NameNode、DataNode、 Seconary NameNode、 JobTracker、 TaskTracker组成。
其中NameNode、DataNode、 Seconary NameNode、运行在Master节点上，而在每个Slave节点上，部署一个DataNode和TaskTracker,以便这个Slave服务器上运行的数据处理程序能尽可能的直接处理本机的数据。对Master节点需要特殊的说明的是， 在小集群中，Secondary NameNode可以属于某个从节点；在大型集群中，NameNode和JobTracker被分别部署到两台不同的服务器上。

# MapReduce #

### MapReduce的前言

MapReduce是一种处理海量数据的并行编程模型和计算框架，用于对大规模数据集（通常大于1TB）的并行计算。 它最早是由Google提出的，并运行在Google的分布式文件系统GFS（Google File System）上， 为服务于全球亿万用户的搜索引擎提供后台的网页索引处理，同事也使用与Google内部数以千计的应用程序和数据处理。
Hadoop实现了Google的MapReduce编程模型和计算框架。 但与Google不同的是， Hadoop是开源的，任何人都可以使用这个模型和框架进行并行编程。

### MapReduce的基础

MapReduce采用“分久必合”的思想，把对大规模数据集的操作，分发给一个主节点管理下的各个分节点共同完成，然后通过整合各个分节点的中间结果，得到最终的结果。
简单的说，MapReduce就是“任务的分解与结果的汇总”。
上述处理过程被MapReduce高度地抽象为两个函数： map和reduce， map负责把任务分解成多个任务，reduce负责把分解后多个任务处理的结果汇总起来。至于在并行编程中的其他种种复杂的问题，如分布式存储、工作调度、负载均衡、容错处理、网络通信等， 均有MapReduce框架负责处理，可以不用程序元操心。需要注意的是，用MapoReduce来处理的数据集（或任务）必须具备这样的特点： 待处理的数据集可以分解成许多的小的数据集，而且每一个小的数据集都可以完全并行地进行处理。


####Map
在Map阶段，MapReduce框架将任务的输入数据分割成固定大小的片段（splits）， 随后将每个split进一步分解成一批键值对<K1,V1>. Hadoop为每个split创建一个Map任务， 也就是Mapper， 用于执行用户自定义的map函数， 并将对应split中的<K1,V1>对作为输入，得到计算的中间结果<K2,V2>。接着将中间结果按照K2进行排序，并将key值相同的value放在一起形成一个新列表， 形成<K2,list<V2>>元组。 最后再根据key值的范围将这些元组进行分组，对应不同的Reduce任务。

####Reduce
在Reduce阶段， Reducer吧不同Mapper接收来的数据整合在一起并进行排序，然后调用用户自定义的reduce函数， 对输入的<K2,list<V2>>对进行相应的处理，
得到键值对<K3,V3>并输出到HDFS上。既然Mapduce框架为每个split创建一个Mapper,那么谁来确定Reducers的数目呢？ 答案是用户。
mapred-site.xml配置文件中有一个表示Reducers的数目的属性 mapred.reduce.tasks, 该属性的默认值为1， 开发人员可以通过job.setNumReduceTasks()方法重新设置该值。

##MapReduce的集群行为
MapReduce运行大规模集群之上， 要完成一个并行计算， 还需要任务调度， 本地计算、 Shuffle（洗牌）过程等一系列环节共同支撑计算的过程。暂且称为MapReduce的集群行为。

#### 1 任务调度与执行
MapReduce任务由一个JobTracker和多个TaskTracker两类节点控制完成。 JobTracker主要负责调度和管理TaskTracker， 它通常情况下运行在Master节点上。
JobTracker将Mapper和Reducers分配给空闲的TaskTracker后，由TaskTracker负责这些任务的并行执行。 TaskTracker必须运行在DataNode上， 所以DataNode即是数据的存储节点， 也是计算节点。 JobTracker也负责监控任务的运行状况，如果某个TaskTracker发生故障，JobTracker就会将其负责的任务分配给其他空闲的TaskTracker重新执行。 MapReduce框架的这种设计很适合于集群上任务的调度和执行， 当然JobTracker的故障将引起整个任务失败， 在Hadoop以后的发行版本中或许会通过运行多个JobTracker解决这个问题。

#### 2 本地计算
把计算节点和数据节点置于同一台计算机上，MapReduce框架尽最大的努力保证在那些存储了数据的节点上执行计算任务。 这种方式有效的减少了数据在网络中传输，
降低了任务对网络带宽的需求， 避免了使网络带宽成为瓶颈， 所以“本地计算” 可以说是节约带宽最有效的方式，业界称为“移动计算比移动数据更经济”。 也正式如此，
split通常情况下应该小于或者等于HDFS数据块的大小（默认情况下64MB）， 从而保证split不会跨越两台计算机存储， 便于“本地计算”。

#### 3 Shuffle过程
MapReduce会将Mapper的输出结果按照key值分成R份（R是预先定义的Reducer的个数）， 划分时常使用哈希函数， 如Hash（key） mod R。 这样可以保证某一个范围内的key一定由某个Reducer来处理， 从而简化Reduce的过程。

#### 4 合并Mapper输出
正如之前所说， 带宽资源非常的宝贵， 所以MapReduce允许在Shuffle之前对结果进行合并（Combine过程）， 即将中间结果中有相同key值的多组<key,value>对合并成一对。 Combine过程和Reduce过程类似，很多情况下可以直接使用reduce函数，但Combine过程是Mapper的一部分，在map函数之后执行。 Combine过程通常情况下可以有效地减少中间结果的数量，从而减少数据传输过程中的网络流量。 值得注意的是， Hadoop并不保证其会对一个Mapper输出执行多少次Combine过程， 值得注意的是， Hadoop并不保证其会对一个Mapper输出执行多少次Combine过程， 也就是说， 开发人员必须保证不论Combine过程执行多少次，得到的结果都是一样的。

#### 5 读取中间的结果

在完成Combine和Shuffle的过程后， Mapper的输出结果被直接写到本地磁盘。 然后，通知JobTracker中间结果文件的位置， 再由JobTracker告知Reducer到哪个DataNode上去取中间结果。 注意所有的Mapper产生的中间结果均按其key值同一个哈希函数划分成R份， R个Reducer各自负责一段key值区间。 每个Reducer需要向多个Mapper节点取得落在其负责的key值区间的中间结果， 然后执行reduce函数， 形成一个最终的结果文件。






## 其他比较 ##

## 结合自身需要评估后的结论 ##

## 组员贡献 ##

## 参考资料 ##

      