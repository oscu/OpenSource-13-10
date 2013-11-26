# Eucalyptus VS.OpenStack #

  组名：OpenSource011
  ---
	##i.王文明 gleamy ##
	##ii.陈琼 orangebutter##
	##iii.夏小刚 BUAA-Louis ##
    ##iv.杜华侨 dubin1003   ##


## 项目介绍 ##

Eucalyptus 英文全称Elastic Utility Computing Architecture for Linking Your Programs To Useful Systems,是一种开源的软件基础结构，用来通过计算集群或工作站群实现弹性的、实用的云计算。它最初是美国加利福尼亚大学 Santa Barbara 计算机科学学院的一个研究项目，现在已经商业化，发展成为了 Eucalyptus Systems Inc。不过，Eucalyptus 仍然按开源项目那样维护和开发。Eucalyptus Systems 还在基于开源的 Eucalyptus 构建额外的产品；它还提供支持服务。
Eucalyptus云计算软件，在一个平台上（分为open source版和enterprise版），提供了对这些资源的抽象。Eucalyptus的源码是公开的。并且有提供给CentOS 5，Debian squeeze，OpenSUSE 11，Fedora 12的软件包。
Eucalyptus选择Xen和KVM作为虚拟化的管理程序。目前版本是3.2。Eucalyptus的enterprise版已经对vSphere ESX/ESXi提供了支持。

OpenStack是一个美国国家航空航天局和Rackspace合作研发的，以Apache许可证授权，并且是一个自由软件和开放源代码项目。
OpenStack是一个云平台管理的项目，它不是一个软件。这个项目由几个主要的组件组合起来完成一些具体的工作。
OpenStack是一个旨在为公共及私有云的建设与管理提供软件的开源项目。它的社区拥有超过130家企业及1350位开发者，这些机构与个人都将OpenStack作为基础设施即服务（简称IaaS）资源的通用前端。OpenStack项目的首要任务是简化云的部署过程并为其带来良好的可扩展性。本文希望通过提供必要的指导信息，帮助大家利用OpenStack前端来设置及管理自己的公共云或私有云。
OpenStack 是由 Rackspace 和 NASA 共同开发的云计算平台，帮助服务商和企业内部实现类似于 Amazon EC2 和 S3 的云基础架构服务(Infrastructure as a Service, IaaS)。OpenStack 包含两个主要模块：Nova 和 Swift，前者是 NASA 开发的虚拟服务器部署和业务计算模块；后者是 Rackspace开发的分布式云存储模块，两者可以一起用，也可以分开单独用。OpenStack 是开源项目，除了有 Rackspace 和 NASA 的大力支持外，后面还有包括 Dell、Citrix、 Cisco、 Canonical 这些重量级公司的贡献和支持，发展速度非常快。

## 功能比较 ##
使这个平台使用更方便的最大的优势之一是Eucalyptus API全面兼容亚马逊API。因此，基于亚马逊API的所有的脚本和软件产品都可以轻松地为你的私有云部署。Eucalyptus支持三个管理程序：XEN、KVM和ESXi。最后一个管理程序仅向企业云版用户提供。

主要特点：

- 任务（分配和管理权限）

- 不依赖于任何管理程序。

- 集群与分区。

- 灵活的网络管理、安全组和流量隔离。

Openstack项目包括三个产品：Nova （类似于亚马逊的EC2）、Swift （类似于亚马逊S3）和Glance（一种为虚拟硬盘镜像提供发现、注册和交付服务的API服务器）。Swift为可访问的许多PB（1PB = 100万GB）数据提供可扩展的对象存储。目前，Nova全面支持两个管理程序：KVM和XEN。这个平台正在迅速地开发并且很快将提供更广泛的功能。

主要特点：

- 能够管理虚拟化的商品服务器资源

- 能够管理局域网

- 虚拟机镜像管理

- 安全组

- 基于任务的访问控制

- 项目与配额

- 通过网络浏览器的VNC（虚拟网络计算机）代理

各功能节点比较

<table>
<tr>
<td>&nbsp;</td>
<td>前端</td>
<td>计算节点</td>
<td>备注</td>
</tr>
<tr>
<td>Eucalyptus</td>
<td>使用ubuntu10.04或者Centos5.5操作系统,通过apt-get install或者yum install的方式直接安装二进制包,构建一个包含CLC,Walrus,SC,CC的前端.根据官方网站提供的文档进行操作,是比较容易实现的。</td>
<td>使用ubuntu10.04或者Centos5.5操作系统，通过apt-get install或者yum install 的方式直接安装二进制包，构建一个提供NC服务的计算节点。根据官方网站提供的文档进行操作，是比较容易实现的。</td>
<td>Eucalyptus包含了一个dhcpd，如果配置不好的话，会造成一定的麻烦。另外，计算节点（NC）与集群控制器（CC）必须在一个C类之网里。如果NC和CC在一个超网里，在注册服务的时候会出现一些问题。</td>
</tr>
<tr>
<td>OpenStack</td>
<td>在ubuntu10.04上利用官方网站提供的nova-install脚本进行安装，基本上没有遇到问题</td>
<td>在ubuntu10.04上利用官方网站提供的nova-install脚本进行安装，基本上没有遇到问题</td>
<td>对于一个简单的系统，安装配置比较简单。</td>
</tr>
</table>
几种虚拟化技术支持
<table>
<tr>
<td>&nbsp;</td>
<td>Xen</td>
<td>KVM</td>
<td>XenServer/XCP</td>
<td>VMWare</td>
<td>LXC</td>
<td>openVZ</td>
</tr>
<tr>
<td>Eucalyptus</td>
<td>Y</td>
<td>Y</td>
<td>&nbsp;</td>
<td>Y</td>
<td>&nbsp;</td>
<td>&nbsp;</td>
</tr>
<tr>
<td>OpenStack</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
<td>&nbsp;</td>
</tr>
</table>
## 其他比较 ##

社区版采用GPLv3授权协议 社区版不需要安装许可

一、授权协议和许可证管理
-
<table class="table table-bordered table-striped table-condensed">
<tr>
<th colspan="2"></th>
<th>授权协议</th>
<th>许可管理</th>
<th>商业模式</th>
</tr>
<tr>
<td rowspan="2">Eucalyptus</td>
<td>社区版</td>
<td>GPLv3授权协议</td>
<td>不需要安装许可</td>
<td>社区版免费使用</td>
</tr>
<tr>
<td>企业版</td>
<td>使用自定义的商业授权协议</td>
<td>需要在云控制器(CLC)节点上安装许可证</td>
<td>按处理器核心总数收费，用户购买的许可证针对特定版本永久有效。</td>
</tr>
<tr>
<td colspan="2">OpenStack</td>
<td>Apache 2.0 授权协议</td>
<td>不需要许可证</td>
<td>免费使用</td>
</tr>
</table>


二、项目历史、运营团队、社区规模
- 
<table>
<tr>
<th></th>
<th>项目历史与运营团队</th>
<th>社区规模和活跃程度</th>
<th>沟通交流</th>
</tr>
<tr>
<td>Eucalyptus</td>
<td>最初是UCSB的HPC研究项目，2009年初成立公司来支持项目的商业化运营。现任CEO是曾担任MySQL CEO的Marten Mickos,现任工程部门SVP的Tim Cramerc曾担任Sun公司NetBeans和OpenSolaris项目的执行总监。整个管理团队对开放源代码项目的管理和运营方面具有丰富的经验。</td>
<td>在同类开放源代码项目当中，Encalyptus的社区规模最大，活跃程度也最高。主要原因是该项目起源于大学研究项目，次要原因是管理团队对开放源代码理念的高度认同。Ubuntu 10.04服务器版选择Encalyptus作为UEC的基础构架，大大的促进了Encalyptus.</td>
<td>社区发表在论坛上的问题通常在48小时内得到回应，通过技术支持电子邮件提出的问题通常在24小时内得到回应。Encalyptus在北京和深圳设有办事处，在中国有工程师提供支持团队。</td>
</tr>
<tr>
<td>OpenStack</td>
<td>OpenStack是服务器托管公司RackSpace与NASA共同发起的开放源代码项目。在开放源代码项目的管理和运营方面，RackSpace和NASA显然缺乏足够的经验。针对OpenStack项目的批评集中在(1)RackSpace对项目有过于强烈的控制欲；(2)OpenStack项目的运作对于社区成员来说基本上是不透明的；(3)OpenStack项目对同类开放源代码项目的攻击性过强。</td>
<td>社区规模较小，主要参与者支持/参与该项目的公司人员。有几个公开的邮件列表，流量很小，由于该项目比较新，在网络上可以参考的安装与配置方面的文章不多。Ubuntu11.04服务器版同时支持Encalyptus和OpenStack作为UEC的基础构架，将有助于OpenStack的推广。</td>
<td>通过邮件列表进行技术方面的沟通，通常在48小时内得到回应。商务方面的邮件沟通，回应较为缓慢。</td>
</tr>
</table>

三、架构方面的比较
- 
- Eucalyptus架构 
> Eucalyptus是一个与Amazon EC2兼容的IaaS系统。Eucalyptus包括云控制器(CLC)、Walrus、集群控制器(CC)、存储控制器(SC)和节点控制器(NC)。CLC是整个Eucalyptu系统的核心，负责高层次的资源调度，例如向CC请求计算资源。Walrus是 一个与Amazon S3类似的存储服务，主要用于存储虚拟机映像和用户数据。CC是一个集群的前端，负责协调一个集群内的计算资源，并且管理集群内的网络流量。SC是一个与Amazon EBS类似的存储块设备服务，可以用来存储业务数据。NC是最终的计算节点，通过调用操作系统层的虚拟化技术来启动和关闭虚拟机。在同一个集群(CC)内的所有计算节点(NC)必须在同一个子网内。 在一个集群(CC)内通常需要部署一台存储服务器(SC)，为该集群内的计算节点提供数据存储服务。

> Eucalyptus通过Agent的方式来管理计算资源。在每一个计算节点上，都需要运行一个eucalyptus-nc的服务。该服务在集群控制器(CC)上注册后，云控制器(CLC)即可通过集群控制器(CLC)将需要运行的虚拟机映像文件(EMI)拷贝到该计算节点上运行。

> Eucalyptus将虚拟机映像文件存储在Walrus上。当用户启动一个虚拟机实例的时候，Eucalyptus首先将相应的虚拟机映像(EMI)从Walrus拷贝到将要运行该实例的计算节点(NC)上。当用户关闭(或者是由于意外而重启)一个虚拟机实例的时候，对虚拟机所做的修改并不会被写回到Walrus上原来的虚拟机映像(EMI)上，所有对该虚拟机的修改都会丢失。如果用户需要保存修改过的虚拟机，就需要利用工具(euca2ools)将该虚拟机实例保存为新的虚拟机映像(EMI)。如果用户需要保存数据，则需要利用存储服务器(SC)所提供的弹性块设备来完成。

- OpenStack架构
> OpenStack是一个与Amazon EC2兼容的IaaS系统。OpenStack包括OpenStack Compute和OpenStack Object Storage两个部分。

> OpenStack Compute又包含Web前端、计算服务、存储服务、身份认证服务、存储块设备(卷)服务、网络服务、任务调度等多个模块。OpenStack Compute的不同模块之间不共享任何信息，通过消息传递进行通讯。因此，不同的模块可以运行在不同的服务器上，也可以运行在同一台服务器上。

> OpenStack Object Store可以利用通用服务器搭建可扩展的海量数据仓库，并且通过冗余来保证数据的安全性。同一份数据的在多台服务器上都有副本，将出现故障的服务器从集群中撤除不会影响数据的完整性，加入新的服务器后系统会自动地在新的服务器上为相应的文件创建新的副本。从功能上讲，OpenStack Object Store同时具备Eucalyptus中的Walrus服务和弹性块设备(SC)服务。不过OpenStack Object Store不是一个文件系统，不能够保证数据的实时性。从这个方面来考虑，OpenStack Object Store更适合用于存储需要长期保存的静态数据，例如操作系统映像文件和多媒体数据。

> OpenStack通过Agent的方式来管理计算资源。在每一个计算节点上，都需要运行nova-network服务和nova-compute服务。这些服务启动之后，就可以通过消息队列来与云控制器进行交互。

## 结合自身需要评估后的结论 ##

## 组员贡献 ##

## 参考资料 ##
CloudStack、OpenStack等四大云平台评测 http://www.chinacloud.cn/show.aspx?id=12339&cid=16
婉兮清扬的blog http://www.qyjohn.net/