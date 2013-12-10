组名:OpenSource9527

    孟凡胜 mengfanshengBUAAGY4
    武俊峰 jeffrey5  
    郝玉飞  

##1  综述 ##
计算机软件与硬件技术的飞速发展也导致了计算模型的不断演化。继分布式计算，并行计算，网络计算，效用计算，Web 2.0等计算概念与模型的不断被推出以后，计算机工业界与学术界又提出了云计算模型[2]，在某种意义上实现对这些计算概念与模型的泛化与商业化。总体上来讲，云计算通过互联网将超大规模的计算与存储资源整合起来，并以可信服务的形式按需提供给用户。
 用户通过简单的终端如笔记本，PDA，甚至手机，使用简单的客户端软件甚至Web就能访问超大规模的计算与存储资源。基于这种计算模型的诱人商业前景，目前各大主流IT公司Microsoft,Google, EMC, VMware, Amazon, Oracle等纷纷推出自己的云计算平台。


##2   三种云计算平台简介##
###2.1   Abiquo公司开源云计算平台#
   　Abiquo公司帮助用户建立，管理以及扩展复杂的计算架构。具体开源云计算产品有三类，三种产品分别是abiCloud, abiNtense和abiData。这三种产品都可以用来架构和开发公有私有混合云，以及云应用等的基础设施。
1）abiCloud是开源云管理软件，可以创建管理资源并且可以按需扩展。使公司能够以快速、简单和可扩展的方式创建和管理大型、复杂的IT基础设施(包括虚拟服务器，网络，应用，存储设备等等)。AbiCloud较之同类其他产品的一个主要的区别在于其强大的Web界面管理。你可以通过拖拽一个虚拟机来部署一个新的服务。这个版本允许通过VirtualBox部署实例，它还支持VMware，KVM和Xen。
2）abiNtense是一个类似于Grid的架构，可用来减少大量高性能计算的执行时间。
3）abiData 由Hadoop，hBase，Pig开发而来，是一个信息管理系统，可以用来搭建分析大量数据的应用。是低成本的云存储解决方案。

近日Abiquo公司宣布推出其一款开源的云计算平台——“abiCloud” ，使公司能够以快速、简单和可扩展的方式创建和管理大型、复杂的IT基础设施(包括虚拟服务器，网络，应用，存储设备等等)。
我们与Abiquo公司合作创始人兼首席执行官Diego Mari?o进行了沟通，他告诉我们，AbiCloud较之同类其他产品的一个主要的区别在于其强大的Web界面管理。他告诉我们：“你可以通过拖拽一个虚拟机来部署一个新的服务。这个版本允许通过VirtualBox 部署实例，它还支持VMware，KVM和Xen。
最初的测试包括在其基础设施上运行Virtualbox，因为它运行起来非常简单，还可以将它运行在不同的架构上，这就是他的第一个重点区别。

 
今天，他通过libvirt支持Xen及KVM，并将在第二季度为这些虚拟设备提供连接器。支持的VMware，是提供给托管服务提供商封闭模块。
基本上， Abiquo允许公司将其基础设施转换到服务。该领域的其他竞争者包括最近成立的Eucalyptus 、Enomaly和Sun公司收购的云计算公司Q-layer。
Abiquo表示，不同的产品有不同的重点和方法，该公司的产品能够为更复杂的基础设施创建私人云计算。
该公司自己的开放API将于今年第三季度公布，但并没有支持亚马逊API的计划。
AbiCloud可以从SF.net上下载。

开源云计算平台：abiCloud 1.7发布

abiCloud是Abiquo公司推出的开源云计算平台。
 该版本的新功能：
1、Abiquo 1.7 包含了对VirtualBox 4.0的支持；见 VirtualBox云节点安装 和 配置查看#系统属性。
2、高级负荷策略，包含在定制化虚拟机部署上。基于系统的规则被列入了基础设施的视图中，允许云管理员定义相关规则。
3、Nexenta 和 OpenSolaris系统的存储代理被再封装，增加如下功能：
?	本地操作系统包格式
?	包版本
?	支持包更新
?	包中元数据的完整代理信息
4、增加元节点属性
5、增加NFS存储属性
6、.7 installer 写了Abiquo安装相关的重要信息，在系统文件中。
/etc/abiquo-release
/etc/abiquo-installer
/etc/redhat-release

abiCloud 1.7 源码下载：https://abicloud.svn.sourceforge.net/svnroot/abicloud/tags/abiquo-1.7/1.7.0/
AbiCloud 强大的Web界面管理：
       


###2.2   Eucalyptus 开源云计算平台##
 Eucalyptus项目（Elastic Utility Computing Architecture for LinkingYour Programs To Useful Systems）是Amazon EC2的一个开源实现，它与商业服务接口兼容。和EC2一样，Eucalyptus依赖于Linux和Xen进行操作系统虚拟化。Eucalyptus是加利福尼亚大学（SantaBarbara）为进行云计算研究而开发的。可以从该大学的网站上下载它，或者通过Eucalyptus Public Cloud体验，不过后者有一些限制。 
Eucalyptus 项目全称是Elastic Utility Computing Architecture for Linking Your Programs To Useful Systems，由Santa Barbara大学建立的开源项目，是主要实现云计算环境的弹性需求的软件，通过其在集群或者服务器组上的部署，并且使用常见的Linux工具和基本的基于web的服务。使用FreeBSD License，意味着可以直接使用在商业软件应用中，当前支持的商业服务只是亚马逊的EC2，今后会增加多种客户端接口。该系统使用和维护十分方便，使用SOAP安全的内部通信，且把可伸缩型作为主要的设计目标，具有简单易用，扩展方便的特点。这个软件层的工具可以用来通过配置服务器集群来实现私有云，并且其接口也是与公有云相兼容，可以满足私有云与公有云混合构建扩展的云计算环境。下面的列表是该项目的路线图：
5/28/08 – Release 1.0 shipped
8/28/08 – EC2 API and initial installation model in V1.3 Completes overlay version
12/16/08 – Security groups, Elastic IPs, AMI, S3 in V1.4
4/09/09 – EBS, Metadata service in V1.5
4/23/09 - Ubuntu release
6/1/09 – Final feature release as V1.6 Completes AWS specification as of 1/1/2009 
7/15/09 – Final bug-fix release "core" opens for community contributions
根据路线图，我们会发现Eucalyptus将会被包含在Ubuntu9.10发布版中，先前关于Ubuntu将会内置云计算环境的报导也是基于此。这种集成云计算开源项目的发布版将会对亚马逊EC2等商业市场进行冲击。构建私有云的方式将会更容易被大公司所接受，公有云的发展将会更倾向于SMB客户群体。
在Eucalyptus的主页上有一个Eucalyptus Public Cloud用来体验Eucalyptus所构成的云计算。当前这个环境可以被任何用户使用，用来启动VM实例，登陆进去，测试实例里的应用，观察状态等任务。但是VM实例只能使用六小时，并且同时一个用户最多开4个VM实例。由于RightScale宣布支持基于eucalyptus的云安装，所以也可以通过RightScale上的EPC版本访问EPC。
另外一个可以运行在eucalyptus上的项目是AppScale，是一个研究型的用来执行Google AppEngine 应用的框架。目前该框架可以在eucalyptus上实现透明操作。

###2.3	10gen MongoDB 开源高性能存储平台##
  chukwa是对hadoop 集群自身的相关信息做收集和分析的组件。

##3	功能点对比分析 ##
三种主要开源云计算平台特征与性能比较如下
### Abiquo公司平台 ##
1)abiCloud可以创建管理资源并且可以按需扩展，具有强大的Web界面管理，支持VMware，KVM和Xen。
2）abiNtense，类似于Grid的架构，可用来减少大量高性能计算的执行时间。
3）abiData 由Hadoop，hBase，Pig开发而来，可以用来搭建分析大量数据的应用，是低成本的云存储解决方案。

###Eucalyptus##
Amazon EC2的一个开源实现，与商业服务接口兼容，依赖于Linux和Xen进行操作系统虚拟化。

###10gen MongoDB##
可用于创建自己的私有云，类似于App Engine的一个软件栈，提供与App Engine 类似的功能，可使用Python以及JavaScript和Ruby语言开发应用程序。还可使用沙盒概念隔离应用程序，并且使用它们自己的应用服务器的许多计算机（在Linux上构建）提供一个可靠的环境。


##4	社区活跃度比较##
 云计算拥有无限潜力有待人们开发挖掘，云计算的发展将给信息社会的发展带来历史性的飞跃，本文在介绍云计算及云计算平台构架的基础上，总结分析了当前主要的开源云计算平台的特征，通过简单的对比和初步分析，得出：Abiquo公司的abiCloud, abiNtense和abiData都可以用来架构和开发公有私有混合云，其中AbiCloud较之同类其他产品的一个主要的区别在于其强大的Web界面管理。abiNtense可减少大量高性能计算的执行时间。而abiData是一种低成本的云存储解决方案；Eucalyptus有EC2的类似功能和接口； 10gen MongoDB可用于创建自己的私有云，类似于App Engine的一个软件栈，提供与App Engine 类似的功能。

##  组员贡献 ##
孟凡胜： 项目介绍 功能比较  武俊峰：功能比较 郝玉飞：功能比较

## 参考资料 ##
[1] Boss G, Malladi P, Quan D, Legregni L, Hall H. Cloud computing. IBM White Paper, 2007.    
[2]GannonD.HeadintheeloudsJl.Nature，2007，449    
[3]人才芯片工程 http://www.lupaworld.com/article-209670-1.html    
[4]开源云计算平台比较http://wenku.baidu.com    
[5]百度百科http://baike.baidu.com/link?url=OLtbbjF8KFKboitaBzyG-9dqTb_XbChI0rAsjqDR7TpKSp9vNxpJydy1m_IbPCMmWT_wH9_rzZOe8CHigJh0Fa
