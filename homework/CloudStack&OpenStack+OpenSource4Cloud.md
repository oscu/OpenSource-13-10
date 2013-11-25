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
整体比较


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
 
* VLAN	不能VLAN间互访	支持VLAN间互访


## 结合自身需要评估后的结论 ##
个人看法“因为OpenStack是多组件，所以灵活性比CloudStack要高，而CloudStack把数据中心虚拟化，对物理资源和虚拟资源有着完整的生命周期管理，所以他们各有自己的特点，各有优势。


## 组员贡献 ##

职承立：开篇项目介绍，两个项目的架构，CloudStack资源管理等核心功能介绍

段孝妍：提交md文档；规划文章内容，确定组员分工；OpenStack计算介绍，CloudStack和OpenStack存储功能的介绍

刘成全：CloudStack和Opnstack网络部分的介绍，结束部分的社区活跃度对比和企业应用实例。

## 参考资料 ##
存储部分：_《程序员》2012年07期 作者 程辉_

_待组员提交或将自己引用部分补齐_
