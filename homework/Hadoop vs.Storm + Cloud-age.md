# Hadoop vs. Storm

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


## 社区活跃程度比较
hadoop有3179个项目，strorm有1665个项目；
以两者中最活跃的项目作对比：

hadoop-common 长期和短期的维护频度都要远远超过nathanmarz/storm。

从提交者的情况来分析，hadoop维护的人员更多，storm维护的人员相对较少。
Fork hadoop-common项目的人有605，加Star的有651；
Fork nathanmarz/storm项目的人有1376，加Star的有7362；

再跟踪部分fork的成员，可以发现虽然fork storm的人数虽多，但是绝大多数都在fork之后没有做过任何修改。而fork hadoop的人会有相当多的人在自己的工程中做周期性的维护。

hadoop-common的成员加入gitbub的时间较长，涉及的项目较多，但是奇怪的是这个项目中的很多成员我无法找到相关信息。
storm的成员加入github时间较晚，似乎都是为了这个项目而来的，最活跃的成员只专注storm项目。

hadoop-common项目中我们只能看到一个别合入的提交的改变情况，但是看不到成员之间的讨论，可能是需要加入讨论邮件才可以看到。
storm项目中对于一个提交，发起成员都要征求其他成员的意见，当大家达成共识的时候，这个提交就被合入了。

两个项目中都有华裔开发者的贡献。

## 结合自身谈一下对Github的体会
我对开源一直都抱有崇敬的态度。之前我使用过开源软件，在开发过程中发现过开源代码的错误或者是异常问题，但是没有反哺的作为，因为的确也不知道如何操作。
Github把我们领入了另一个世界，了解到这个世界上的的确确有很多人在另一个纬度做着自己的贡献，在此我也希望自己未来可以为这个纬度贡献自己的能力。
但是在使用github过程中我也发现了不少问题，让我明白要成为一个有贡献的人也不容易。
> 1 找到目标工程
比如我们组这次的初始题目是比较hadoop和strom。在github中一找这两个关键词，就能发现很多项目，一下子就有点乱花渐欲迷人眼的感觉。这个时候就要好好看一下每个项目到底是个什么意思。如果是一个初学者我觉得这已经是第一步比较困难的选择了，只有在对hadoop比较了解的情况下才能弄明白。
> 2 下载工程
也许是因为在大陆地区访问github这个网站有某些限制，用github客户端下载源码或者在github上编辑或者查看都感觉很不顺畅。因此我体会到了之前为什么某个订票插件引起github死掉的感觉。而且还需要开发者对git的使用要有所了解。
> 3 查看和编译工程
本以为下载的hadoop工程很容易就可以使用了，但是在装好java环境，安装完ide之后发现hadoop工程还有许多错误。为了解决这些错误，我还得先学习一下java的各种问题解决的办法，也就是说无法直捣黄龙。因为之前一直都是c系列的开发，没有用过java，只是看过java代码，觉得写代码没什么问题；但是环境的配置的确是没有c那么流畅。不过做完之后也觉得没什么了，但是这对初学者来说的确是一个大问题。

## 组员贡献
> vfrankwang列举出hadoop和storm功能上面的不同

> loulou886结合自己实践，谈了使用心得和社会活跃度对比。

## 参考资料