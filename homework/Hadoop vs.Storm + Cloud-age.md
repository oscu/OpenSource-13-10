# Hadoop vs.Storm

> 组名：Cloud-age  
> 成员：李国芳(lili6)、陈鲁(loulou886)、柴跃立(ylchai)、王奎量(vfrankwang)

## 项目介绍

> ### Hadoop
> 一个分布式系统基础架构，由Apache基金会开发。  
用户可以在不了解分布式底层细节的情况下，开发分布式程序，  
充分利用集群的威力高速运算和存储。

> ### Storm
> Twitter将Storm正式开源了，这是一个分布式的、容错的实时计算系统。  
它被托管在GitHub上，遵循 Eclipse Public License 1.0。  
Storm是由BackType开发的实时处理系统，BackType现在已在Twitter麾下。  
GitHub上的最新版本是Storm 0.5.2，基本是用Clojure写的。


## 功能比较

> ### Hadoop
> Hadoop实现了一个分布式文件系统（Hadoop Distributed File System），简称HDFS。  
HDFS有着高容错性的特点，并且设计用来部署在低廉的（low-cost）硬件上。  
HDFS提供高传输率（high throughput）来访问应用程序的数据， 
适合那些有着超大数据集（large data set）的应用程序。  
HDFS放宽了（relax）POSIX的要求（requirements）, 
这样可以流的形式访问（streaming access）文件系统中的数据。

> 借助于Map/reduce，hadoop开发了一个抽象框架，抽象到人们无需关注大多数的分布式细节，  
而只需要表示出自己的处理逻辑即可。

> ### Storm
> 与hadoop类似，storm也开发了一个抽象框架（拓扑逻辑），借助该框架，   
能够处理大多数的实时处理的业务而无需关注底层的大部分细节。


## 其他比较

> Storm的集群表面上看和Hadoop的集群非常像。  
但是在Hadoop上面你运行的是MapReduce的Job，  
而在Storm上面你运行的是Topology。

> 它们是非常不一样的，一个关键的区别是：  
一个MapReduce Job最终会结束，而一个Topology运永远运行（除非你显式的杀掉他）。

## 结合自身需要评估后的结论

## 组员贡献

## 参考资料
