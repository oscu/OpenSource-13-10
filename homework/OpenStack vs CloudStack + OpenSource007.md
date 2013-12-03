# OpenStack vs CloudStack #

  **组名：**OpenSource007 
  
  **成员：**季万强(jiwanqiang)、赵勇(zhaoyong111)、徐伟(xuwei888)、冯一帆(evanf)

## 项目介绍 ##
###1. OpenStack###
![OpenStack Logo](http://upload.wikimedia.org/wikipedia/en/4/4c/OpenStack.png "OpenStack Logo")

OpenStack源自美国国家航空航天局和Rackspace合作研发的云计算项目，旨在为公共云以及私有云的建设提供IaaS服务。
作为自由以及开源软件它受Apache协议所限制，该项目由OpenStack基金会所管理，该基金会成立自2012年9月，其任务
是推广OpenStack项目以及社区的维护。

截止到本文发布时，已经超过200家企业加入，其中包含了 Arista Networks, AT&T, AMD, Brocade Communications
 Systems, Canonical, Cisco, Dell, EMC, Ericsson, Groupe Bull, HP, IBM, Inktank, Intel, NEC,
  NetApp, Nexenta, Rackspace Hosting, Red Hat, SUSE Linux, VMware, 以及Yahoo!等。
  
OpenStack 是由 Rackspace 和 NASA 共同开发的云计算平台，帮助服务商和企业内部实现类似于 Amazon EC2 和 S3 的
云基础架构服务(Infrastructure as a Service, IaaS)。OpenStack 包含两个主要模块：Nova 和 Swift，前者是 NASA 
开发的虚拟服务器部署和业务计算模块；后者是 Rackspace开发的分布式云存储模块，两者可以一起用，也可以分开单独用
。OpenStack 是开源项目，除了有 Rackspace 和 NASA 的大力支持外，后面还有包括 Dell、Citrix、 Cisco、 Canonical 
这些重量级公司的贡献和支持，发展速度非常快，有取代另一个业界领先开源云平台 Eucalyptus 的态势。
  
#### *运用范围* ####
OpenStack是IaaS(基础设施即服务)组件，让任何人都可以自行建立和提供云端运算服务。
此外，OpenStack也用作建立防火墙内的“私有云”（Private Cloud），提供机构或企业内各部门共享资源。

#### *组件* ####
+ *Compute (Nova)*
+ *Object Storage (Swift)*
+ *Block Storage (Cinder)*
+ *Networking (Neutron)*
+ *Dashboard (Horizon)*
+ *Identity Service (Keystone)*
+ *Image Service (Glance)*
+ *Metering (Ceilometer)*
+ *Orchestration (Heat)*

###2. CloudStack###
![CloudStack Logo](http://upload.wikimedia.org/wikipedia/en/4/40/CloudStack_Logo.png "CloudStack Logo")

CloudStack是一个开源的具有高可用性及扩展性的云计算平台。支持管理大部分主流的hypervisors，如KVM，XenServer，
VMware，Oracle VM，Xen等。同时CloudStack是一个开源云计算解决方案。可以加速高伸缩性的公共和私有云（IaaS
）的部署、管理、配置。使用CloudStack作为基础，数据中心操作者可以快速方便的通过现存基础架构创建云服务。

#### *简介* ####
CloudStack形成的基础设施云和数据中心运营商可以快速，轻松地建立在其现有的基础设施提供云服务的需求，弹性云计算服务。

CloudStack用户可以充分利用云计算提供更高的效率，无限的规模和更快地部署新服务和系统的最终用户。

CloudStack 是一个开源的云操作系统，它可以帮助用户利用自己的硬件提供类似于Amazon EC2那样的公共云服务。

CloudStack可以通过组织和协调用户的虚拟化资源，构建一个和谐的环境。

CloudStack具有许多强大的功能，可以让用户构建一个安全的多租户云计算环境。

CloudStack 兼容Amazon API 接口。

CloudStack可以让用户快速和方便地在现有的架构上建立自己的云服务。

CloudStack可以帮助用户更好地协调服务器、存储、网络资源，从而构建一个IaaS平台。

CloudStack的前身是Cloud com，后被思杰收购。英特尔、阿尔卡特-朗迅、瞻博网络、博科等都已宣布支持CloudStack。
2011年7月，Citrix收购Cloud com，并将CloudStack 100%开源。2012年4月5日，Citrix又宣布将其拥有的
CloudStack开源软件交给Apache软件基金会管理。CloudStack已经有了许多商用客户，包括GoDaddy、英国电信、
日本电报电话公司、塔塔集团、韩国电信等。

#### *特色* ####
+ Built-in high-availability for hosts and VMs
+ AJAX web GUI for management
+ AWS API compatibility
+ Hypervisor agnostic
+ Snapshot management
+ Usage metering
+ Network management (VLAN's, security groups)
+ Virtual routers, firewalls, load balancers
+ Multi-role support

#### *兼容性* ####
+ CloudStack可以管理多种Hypervisor的虚拟化程序，并支持这些虚拟化程序所兼容的计算服务器。

+ CloudStack建立虚拟机所使用的主存储可以使用计算服务器自己的本地磁盘，也可以挂载iSCSI，光纤，NFS存储。存放光盘镜像模版的二级存储可以使用NFS外，还可以使用Openstack的swift组件。

+ Cloudstack除了支持各种网络的连接方式，不需要硬件设备，系统身就会提供多种的网络服务，就可以实现如：网络隔离，防火墙，负载均衡，VPN等功能。并且可以提供给用户自己进行配置，省去了管理员大量的配置工作，节省硬件成本。

#### *CloudStack中国社区* ####
2012年4月，世界领先的应用服务软件方案提供商Citrix（思杰公司），宣布将CloudStack开源软件加入Apache软件基金会
，CloudStack成为行业中首个加入该基金会的云基础设施解决方案。作为国内首家提供CloudStack技术支持及商业版销售的北京天云趋势科技有限公司，
也收到了大量公司和个人对CloudStack软件架构进行技术交流的要求。因此，天云趋势与Citrix达成战略合作协议，共推CloudStack社区在中国的发展，
并成立了CloudStack中国社区。

天云趋势作为第一家在中国市场基于CloudStack云平台咨询和服务的软件企业，在过去的两年内，为超过100个国内客户
提供相关咨询和技术支持服务，并有多名开发人员活跃于CloudStack国际开源社区，并全力支持国内CloudStack社区的
建设和发展，2012年至今已协助CloudStack中国社区在北京、南京、上海、西安、广州等多个城市成功举办CloudStack
技术沙龙巡回活动，并邀请到许多Apache CloudStack核心开发人员主讲，受到了国内广大CloudStack技术爱好者的欢迎.

国内有越来越多的企业或个人开始加入到CloudStack的行列中。CloudStack中国社区旨在为广大的CloudStack爱好者
提供有关Apache CloudStack部署、运维、开发的有关内容，并对云计算相关行业技术汇总。CloudStack中国社区为国
内广大CloudStack 爱好者提供了一个沟通交流的平台，并举办中国各大中城市的CloudStack技术沙龙巡回活动。

## 功能比较 ##

CloudStack经常被当做OpenStack和Eucalyptus的同类提到，实际上三者各有所侧重。CloudStack更意味着
建设和管理私有云基础设施，而不是提供严格的Amazon Web Services兼容的私有云系统(Eucalyptus)，或
提供一个大厂商所利用的云建设组件的工具箱(OpenStack)。
　　
另一个关键的区别是每个项目的支持者的
类型。CloudStack的两个主要支持者是其托管者，思杰和ASF。OpenStack的支持者包括硬件和软件厂商：
红帽，VMware，惠普，戴尔，Rackspace，思科，等等 - 其中许多厂商都有自己的基于的OpenStack产品(
如惠普融合云)。

大多数Apache CloudStack的用户是云经销商或另一种供应商：Datapipe，SoftLayer(现在是IBM子公司)，
和GoDaddy，以及日本和英国电信NTT和BT。IBM是OpenStack的支持者，但显然决定让SoftLayer保持其现有
的CloudStack投资，为IBM的客户提供两种技术。相比之下，思杰在2012年离开了OpenStack，现在完全致力
于CloudStack。

Openstack包括5个核心项目，分别是：
+ l、Nova - 计算服务
+ 2、Glance - 镜像服务
+ 3、Neutron - 网络务
+ 4、Swift - 对象存储服务
+ 5、Cinder - 块存储服务

还包括其它几个子项目，分别是：
+ 1、OpenStack Identity (Keystone)
+ 2、Metering (Ceilometer)
+ 3、Orchestration (Heat)
+ 4、OpenStack Dashboard (Horizon)
+ 5、OpenStack Common Libraries (Oslo)

<table>
	<tr align="center">
		<td><strong>项目名称</strong></td>
		<td><strong>OpenStack</strong></td>
		<td><strong>CloudStack</strong></td>
	</tr>
	<tr>
		<td><strong>开发语言</strong></td>
		<td>Python</td>
		<td>Java</td>
	</tr>
	<tr>
		<td><strong>服务层次</strong></td>
		<td>IaaS</td>
		<td>IaaS</td>
	</tr>
	<tr>
		<td><strong>动态资源调配</strong></td>
		<td>无现成功能，需通过Nova-scheduler 组件自己实现</td>
		<td>主机Maintainance模式下自动迁移VM </td>
	</tr>
	<tr>
		<td><strong>VM模板</strong></td>
		<td>支持</td>
		<td>支持</td>
	</tr>
	<tr>
		<td><strong>VM Console</strong></td>
		<td>支持</td>
		<td>支持</td>
	</tr>
	<tr>
		<td><strong>用户界面</strong></td>
		<td>DashBoard，较简单</td>
		<td>Web Console,功能较完善</td>
	</tr>
	<tr>
		<td><strong>负载均衡</strong></td>
		<td>软件负载均衡(Nova-network或  OpenStack Load Balance API)、硬件负载均衡</td>
		<td>软件负载均衡(Virtual Router)、硬件负载均衡</td>
	</tr>
	<tr>
		<td><strong>虚拟化技术</strong></td>
		<td>XenServer,Oracle  VM,KVM,QEMU,ESX/ESXi,LXC(Liunx Container)等</td>
		<td>XenServer,Oracle VM，vCenter,KVM,Bare Metal</td>
	</tr>
	<tr>
		<td><strong>最小化部署</strong></td>
		<td>支持All in one （Nova,Keystone,Glance组件必选）</td>
		<td>一管理节点，一主机节点</td>
	</tr>
	<tr>
		<td><strong>数据库支持</strong></td>
		<td>PostgreSQL,MySQL,SQLite</td>
		<td>MySQL</td>
	</tr>
	<tr>
		<td><strong>组件</strong></td>
		<td>Nova,Glance,Keystone,Horizon,Swift</td>
		<td>Console Proxy VM,Second Storage VM,Virtual Router VM,Host Agent,Management Server</td>
	</tr>
	<tr>
		<td><strong>网络</strong></td>
		<td>VLAN,FLAT,FLATDhcp</td>
		<td>Isolation（VLAN），Share</td>
	</tr>
</table>
## 其他比较 ##
CloudStack项目有30家合作伙伴，包括NTT，瞻博网络，塔塔通信等，其中很多和OpenStack都是有关联的。
CloudStack 具有与AWS 兼容的本地API设置， OpenStack 也有这样的特点。
CloudStack是一项可以安装的软件产品，为了推广，Citrix将其提升为一个完全开源的Apache项目。

和CloudStack相比，OpenStack有不够完善的地方。当然对许多像Piston ，Cloudscaling ，这些公司来说
CloudStack 开源代码是他们产品的基础。OpenStack 更加复杂，对终端用户支持度不够。然而OpenStack 支持高端网络功能，可以为特定的案例提供支持，例如高性能和庞大的分布式计算。OpenStack 也通过
Apache公开资源。

### CloudStack ###

CloudStack是一个管理数据中心计算资源的控制台。Zynga、诺基亚研究中心和Cloud Central等许多知名

的信息驱动的公司已经使用CloudStack部署了云。除了拥有自己的API(应用程序编程接口)之外，这个平台

还支持能够把一个亚马逊API转变为CloudStackAPI的CloudBridge Amazon EC2。

主要特点：
    不依赖于任何管理程序(KVM、XEN、ESXi、OVM和BareMetal)
    任务(分配和管理权限)、
    虚拟网络(支持虚拟局域网)
    资源池(让管理员限制虚拟资源，例如，限制一个账户创建的虚拟机的数量以及分配给一个账户的公共

IP地址的数量，等等)
    快照和卷
    虚拟路由器、防火墙和负载均衡器
    使用主机维护进行动态迁移

价格：CloudStack将根据GNU Public License v3(GNU公共许可证第三版)免费发布。
社区：有一个在线社区免费提供及时的技术支持。你可以在论坛中找到许多CloudStack问题的解决方案。

还有一个IRC(互联网中继聊天)频道，欢迎每一个人提出问题。
说明文件：如果你有基本的技术背景，你使用默认设置安装CloudStack平台是很容易的。如果需要更复杂

的安装，你会遇到一些难题，因为说明文件不包含全部的复杂问题。这个手册提供一步一步的指令，但是

没有提供这个平台总体如何运行的任何信息。

### openstack ###
OpenStack用于部署云的一个开源软件平台.
主要特点：
    能够管理虚拟化的商品服务器资源
    能够管理局域网
    虚拟机镜像管理
    安全组
    基于任务的访问控制
    项目与配额
    通过网络浏览器的VNC(虚拟网络计算机)代理

价格：OpenStack是开源软件并且能够免费下载。
社区：OpenStack似乎拥有最大的和最活跃的社区。
说明文件：OpenStack的说明文件有些不完整。由于产品的迅速开发，这个说明文件不能及时地覆盖所有当

前的问题和新特点。你必须经常访问论坛或者使用IRC得到需要的信息。
<table>
	<tr align="center">
		<td><strong>项目名称</strong></td>
		<td><strong>OpenStack</strong></td>
		<td><strong>CloudStack</strong></td>
	</tr>
	<tr>
		<td><strong>开发语言</strong></td>
		<td>Python</td>
		<td>Java</td>
	</tr>
	<tr>
		<td><strong>层次</strong></td>
		<td>IaaS</td>
		<td>IaaS</td>
	</tr>
	<tr>
		<td><strong>发起组织</strong></td>
		<td>美国国家航空航天局和Rackspace</td>
		<td>Cloud.com, Citrix</td>
	</tr>
	<tr>
		<td><strong>发起时间</strong></td>
		<td>2010年7月</td>
		<td>2010年5月</td>
	</tr>
	<tr>
		<td><strong>开发者</strong></td>
		<td>openstack.org</td>
		<td>Apache Software Foundation</td>
	</tr>
	<tr>
		<td><strong>遵循协议</strong></td>
		<td>Apache License 2.0</td>
		<td>Apache License 2.0</td>
	</tr>
	<tr>
		<td><strong>兼容问题</strong></td>
		<td>存在各版本之间的兼容问题</td>
		<td>版本发布稳定，不存在兼容问题</td>
	</tr>
</table>
## 结合自身需要评估后的结论 ##
如果采用Python语言进行开发时，优先考虑OpenStack。如果采用Java语言进行开发时，则采用CloudStack。个人更倾
向于CloudStack，主要原因为拥有强大的社区支持以及ASF的支持与维护，除此之外由于拥有强大的维护团队，CloudStack
版本更加稳定以及兼容性更好，为此首选CloudStack。

## 组员贡献 ##

## 参考资料 ##
1. [OpenStack - Wikipedia](http://en.wikipedia.org/wiki/OpenStack "OpenStack - Wikipedia, the free encyclopedia")
2. [CloudStack - Wikipedia](http://en.wikipedia.org/wiki/CloudStack "Apache CloudStack - Wikipedia, the free encyclopedia")
3. [Apache CloudStack](http://cloudstack.apache.org "Apache CloudStack: Open Source Cloud Computing")
4. [so on](#)
