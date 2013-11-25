# CloudStack&OpenStack介绍#



  **OpenSource4Cloud：**
  
                    1. 段孝妍，duanxiaoyan
        
                    2. 刘成全，id
                    
                    3. 职承立，zhichengli
                    
## 项目介绍 ##
 
**CloudStack** 

–2008年由Cloud.com开发，有商业和开源两个版本。开源版本采用GPL v2 license 

–2011年7月Cloud.com被Citrix(思杰)收购，CloudStack全部开源 

–2012年4月Citrix将CloudStack贡献给Apache基金会，改为Apache 2.0 license 

**OpenStack** 

–Rackspace和NASA合作研发，2010年10月开源，采用Apache 2.0 license 

–2011年Rackspace宣布成立OpenStack基金会，将OpenStack贡献给该基金会

-核心组件有以下几个，Nova，Swift，Glance，Keystone，Horizon，Quantum&Melange，还包括一些社区项目


## 其他比较 ##
####整体比较####


* 比较项  	| CloudStack	| OpenStack

* 服务层次	|IaaS	       |  IaaS

* 授权协议	| Apache 2.0	| Apache 2.0

* 许可证	| 不需要	| 不需要

* 动态资源调配	| 主机Maintainance模式下自动迁移VM	| 无现成功能，需通过Nova-scheduler组件自己实现

* VM模板	| 支持	| 支持

* VM Console	| 支持	| 支持

* 开发语言	| Java	| Python

* 用户界面	|Web Console,功能较完善	| DashBoard，较简单

* 负载均衡	| 软件负载均衡(Virtual Router)、硬件负载均衡	| 软件负载均衡(Nova-network或 OpenStack Load Balance API)、硬件负载均衡

* 虚拟化技术	| XenServer,Oracle VM，vCenter,KVM,Bare Metal	| XenServer,Oracle VM,KVM,QEMU,ESX/ESXi,LXC(Liunx Container)等

* 最小化部署	| 一管理节点，一主机节点	|支持All in one（Nova,Keystone,Glance组件必选）

* 支持数据库	| MySQL	| PostgreSQL,MySQL,SQLite

* 组件	| Console Proxy VM,Second Storage VM,Virtual Router VM,Host Agent,Management Server	| Nova,Glance,Keystone,Horizon,Swift

* 网络形式	| Isolation（VLAN），Share |	VLAN,FLAT,FLATDhcp

* 版本问题	| 版本发布稳定，不存在兼容性问题	| 存在各版本兼容性问题
 
* VLAN	不能VLAN间互访	| 支持VLAN间互访

####存储比较####

**CloudStack：**

   CloudStack把存储分成了主存储与二级存储. 根据Hypervisor种类的不同, 主存支持不同的磁盘镜像格式。iSCSI和FC-San存储在Xenserver中被加载为clustered LVM格式，此种格式下，不支持存储的超配。如果存储支持XenServer的thin-provisioning，对于每个磁盘是链式存储，对磁盘的copy等操作，都会基于该磁盘生成一个新的链，新加内容写入新的链中，所以支持存储超配。
   
   _两种存储的功能：_
   
   主存储主要用来存放虚拟机的磁盘镜像,二级存储用来存放template，snapshot和需要下载的volume。二级存储不直接挂载到hyperviser上，需要由management server或ssvm来进行操作

**OpenStack：**

   OpenStack有三个与存储相关的组件：

* Swift——对象存储 （Object Storage），在概念上类似于Amazon S3服务，swift具有很强的扩展性、冗余和持久性，用于永久类型的静态数据的长期存储。在OpenStack中它与Glance结合，为其存储镜像文件。并且因为它具有无限的可扩展性，也适合用于存储日志文件和数据备份仓库。

* Glance——虚机镜像（Image）存储和管理，Glance是一个虚机镜像的存储。向前端nova提供镜像服务，包括存储，查询和检索。这个模块本身不存储大量的数据，需要挂载后台存储（比如swift）来存放实际的镜像数据。

* Cinder——块存储（Block Storage），类似于Amazon的EBS块存储服务，目前仅给虚机挂载使用。Openstack从Folsom开始使用Cinder替换原来的Nova-Volume服务，为Openstack云平台提供块存储服务。
Cinder通过添加不同厂商的指定drivers来为了支持不同类型和型号的存储。目前能支持的商业存储设备有EMC 和IBM的几款，也能通过LVM支持本地存储和NFS协议支持NAS存储。

####网络设计对比####
（刘成全部分）


## 结合自身需要评估后的结论 ##
（刘成全部分）
个人看法“因为OpenStack是多组件，所以灵活性比CloudStack要高，而CloudStack把数据中心虚拟化，对物理资源和虚拟资源有着完整的生命周期管理，所以他们各有自己的特点，各有优势。


## 组员贡献 ##

职承立：开篇项目介绍，整体比较，CloudStack的资源管理

段孝妍：提交文档；CloudStack和OpenStack存储功能的介绍，OpenStack的nova组件介绍

刘成全：CloudStack和Opnstack网络部分的介绍，结束部分的社区活跃度对比和应用实例。

## 参考资料 ##
存储部分：_《程序员》2012年07期 作者 程辉_

_待组员提交或将自己引用部分补齐_
