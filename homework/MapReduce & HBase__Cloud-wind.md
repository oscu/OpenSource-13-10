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



## 其他比较 ##

## 结合自身需要评估后的结论 ##

## 组员贡献 ##

## 参考资料 ##

      
