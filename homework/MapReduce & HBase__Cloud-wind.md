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




## 其他比较 ##

## 结合自身需要评估后的结论 ##

## 组员贡献 ##

## 参考资料 ##

      
