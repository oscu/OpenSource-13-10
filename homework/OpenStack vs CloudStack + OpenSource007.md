# OpenStack vs CloudStack #

  **组名：**OpenSource007 
  
  **成员：**季万强(jiwanqiang)、赵勇(zhaoyong111)、徐伟(xuwei888)、冯一帆()

## 项目介绍 ##
###1. OpenStack###
![OpenStack Logo](http://upload.wikimedia.org/wikipedia/en/4/4c/OpenStack.png "OpenStack Logo")

OpenStack源自美国国家航空航天局和Rackspace合作研发的云计算项目，旨在为公共云以及私有云的建设提供IaaS服务。
作为自由以及开源软件它受Apache协议所限制，该项目由OpenStack基金会所管理，该基金会成立自2012年9月，其任务
是推广OpenStack项目以及社区的维护。

截止到本文发布时，已经超过200家企业加入，其中包含了 Arista Networks, AT&T, AMD, Brocade Communications
 Systems, Canonical, Cisco, Dell, EMC, Ericsson, Groupe Bull, HP, IBM, Inktank, Intel, NEC,
  NetApp, Nexenta, Rackspace Hosting, Red Hat, SUSE Linux, VMware, 以及Yahoo!等。
  
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
		<td>Cloud.com</td>
	</tr>
	<tr>
		<td><strong>发起时间</strong></td>
		<td>2010年7月</td>
		<td>2010年5月</td>
	</tr>
	<tr>
		<td><strong>兼容问题</strong></td>
		<td>存在各版本之间的兼容问题</td>
		<td>版本发布稳定，不存在兼容问题</td>
	</tr>
</table>
## 结合自身需要评估后的结论 ##

## 组员贡献 ##

## 参考资料 ##
1. [OpenStack - Wikipedia](http://en.wikipedia.org/wiki/OpenStack "OpenStack - Wikipedia, the free encyclopedia")
2. [CloudStack - Wikipedia](http://en.wikipedia.org/wiki/CloudStack "Apache CloudStack - Wikipedia, the free encyclopedia")
3. [Apache CloudStack](http://cloudstack.apache.org "Apache CloudStack: Open Source Cloud Computing")
4. [so on](#)