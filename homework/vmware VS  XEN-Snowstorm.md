## VMware & XEN  ##
	
组名： Snowstorm
    
成员名称 ：    
   
       王真 队长    wzfinish （vmware 功能对比）
   
       马永龙   （提供相关社区活跃度信息,其他信息汇总）
      
       黄梦晞 （ 提供XEN 功能对比： MengxiHuang）
  

          
## 项目介绍 ##
         
针对两大业界知名的虚拟化产品vmware和XEN进行多方面的对比。    
主要包括以下几方面：（1）虚拟化程度（2）虚拟化支持系统对比（3）网络虚拟化支持（4）存储（5）访问控制（6）资源高可用（7）安全（8）云计算支持 （9）成功应用 （10）其他对比
  
 
## 功能比较 ##
功能点对比分析：（王真提供）     
1. 虚拟化程度：完全虚拟化。    
2. 虚拟化支持系统：win/linux/sun for x86/other. 
3. 网络虚拟化支持：vmware 网络虚拟化，虚拟交换机可以提供以下功能    
    3.1 负载平衡和故障切换    
    3.2 VLAN 策略    
    3.3 安全策略    
    3.4 流量调整策略    
    3.5 资源分配策略    
4. 存储:     
存储的虚拟化 ：    
vmware ESXi 提供主机级别的存储器虚拟化，即采用逻辑方式从虚拟机中抽象物理存储器层。    
ESXi 虚拟机使用虚拟磁盘来存储其操作系统、程序文件，以及与其活动相关联的其他数据。虚拟磁盘是一个较大的物理文件或一组文件，可以像处理任何其他文件那样复制、移动、归档和备份虚拟磁盘。    
5. 安全：    
vmware 4以前，使用linux内核，应用场景多，已知漏洞数80多，到5的版本后，重新编译内核，漏洞数明显减少。但XEN 作为开源，已知漏洞数比较少，总数在30以内。    
6. 虚拟化高可用     
vmware 提供的高可用：    
无论是计划停机时间还是非计划停机时间，都会带来相当大的成本。但是，用于确保更高级别可用性的传统方案都需要较大开销，并且难以实施和管理。 VMware 软件可为重要应用程序提供更高级别的可用性，并且操作更简单，成本更低。使用 vSphere，组织可以轻松提高为所有应用程序提供的基准级别，并且以更低成本和更简单的操作来实现更高级别的可用性。

## 其他比较 ##
vmware 应用场景：
公司要求虚拟机运行时将停机时间降至最低。借助 VMWARE 的
vMotion，通过专门的 vMotion 网络在主机之间移动正在运行的虚拟机的整个状态，且不会造成服务中断。

二、XEN 功能对比 （由  黄梦晞 提交）

## 结合自身需要评估后的结论 ##
VMware和Xen是目前最流行的硬件抽象层虚拟机，在X86架构服务器上应用广泛。Xen的虚拟网络性能与真实主机接近，而比VMware Workslaion虚拟网络的性能好。如果在Windows平台上，由于不能修改操作系统，只能使用VMware Workslalion；如果在Linux平台上，由于Xen的效率更高，建议使用Xen。
    
    

+　　虚拟机监控器(VMM)虚拟计算平台的硬件资源，以支持多个虚拟机(VM)的同时运行。每个虚拟机独立运行一个操作系统，运行于虚拟机内的操作系统被称为客户操作系统(GOS)，虚拟机监控器为这些操作系统提供安全和高度的隔离。

+    Xen是运行于Intel x86上的VMM，它支持多个GOS所未有的性能和隔离性同时运行，是遵循GMJ许可的开源软件。当前，运用Xen支持多个虚拟机，并且在每个虚拟机上各自运行单独的操作系统，复用计算平台的研究正逐渐成为国内外学者研究的热点。

+　　Xen能为流行的3层架构互联网应用提供复用计算平台。3层架构互联网应用包括:(1)前端是HTTP服务器，负责处理用户输入输出；(2)中间是应用服务器，实现应用的核心功能；(3)后端是数据库服务器，存储用户数据。3层架构互联网的一个突出特点是用户仅与HTTP服务器交互，不与另外两个服务器交互。换言之，HTTP服务器是访问另外两个服务的单点入口或应用网关。

+　　消弱XEN0的功能，将其功能分解到其他域，将会适当减少XEN0的瓶颈作用。对于隐通道问题的分析和处理，是一个难解的问题，需要更多研究者的努力。为了资源隔离和资源共享女全，需要实行严格的访问控制策略。例如IBM将sHyper加入XEN中进行强制访问控制；Intel将要实施的LT (LaGrande Technology)技术，能有效增强设备隔离，实现I/O保护、内存越界保护、键盘、显示的隔离保护等。通过虚拟TPM，建立可信域。另外对于虚拟机系统的管理需要特别的注意和加强。以上这些措施都可以有效增强XEN的安全性。

+　　虽然目前XEN还有很多问题，但是山于其优越的性能、开源性和良好的架构，在全球各大公司，例如：Intel、AMD、HP、IBM等的积极参与下，XEN是业界最优秀的虚拟机之一。

+　　

+　　基于Linux开发源代码的Xen虚拟化与较成熟的VMware虚拟化相比在性能及稳定性方而均有一定的差距:

+　　(1) Xen虚拟机内部应用在性能方面与VMware虚拟机内部应用有轻微差距，不是很明显。

+　　(2)Xen虚拟机在内部应用稳定性方面与VMware虚拟机有一定差距。

+　　(3) Xen虚拟机在压力较大时，可能出现小稳定的情况。

+　　(4)对于Xen和VMware，同宿主机上其它虚拟机压力大小对被测虚拟机影响小大。

+

+**三、马永龙：**

+其余资料收集整合
 
#### 安全问题 ####

+>

+VMware ESXi有着与VMware ESX一样的许多安全问题。确保虚拟化安全要做的绝不仅仅是加固虚拟化主机。即便如此，许多人还是误以为VMware ESXi来得更安全。事实并非如此，因为它没有深层防御功能。任何进程都可以在虚拟机管理程序里面运行，并不仅仅限于主要的对象类型，比如vSwitch或虚拟机容器。大多数人还认为VMware ESXi是一个硬件设备，于是只采取了VMware推荐的多项安全加强措施中的一两项，又没有关注管理或访问VMware ESXi的方式。另外，我认为大多数人在启用安装的ESXi系统上的SSH功能。如果他们这么做，其实没有真正的安全可言，因为ESXi内部没有深层防御功能。

+>

+常被忽视的几个问题：第一个就是使用扁平化虚拟网络作为虚拟网络，而不是使用更稳健、更有保障的网络。这在使用VMsafe vApps时会很有必要。另一个问题是，许多人把管理工具与ESX主机服务控制台放在了防火墙的两侧，这么做是错误的。因为这样一来，他们就得开启许多不必要的端口。相反，他们应当把ESX管理控制台和vCenter工具放在防火墙的同一侧，并且限制只能使用一个协议，比如加密的远程桌面协议（RDP）。这样一来，管理员可以访问虚拟机，进而访问管理工具。最后一个常见的安全问题是，没有使用部署环境的网络/虚拟化主机，这种环境下的网络/虚拟化主机可以防范零日攻击。相反，有些人直接部署到生产环境；如果操作出错，虽然可以删除虚拟机，但这会在磁盘上留下痕迹。

+**一、WMware漏洞：**

+>

+1. 2013-09-06VMware ESX及ESXi缓冲区溢出漏洞（CVE-2013-3657）

+2. 2013-08-29VMware ESXi及ESX NFC协议处理远程拒绝服务漏洞

+3. 2013-04-25vCenter Server Appliance 任意代码执行漏洞(CVE-2013-3079)

+4. 2013-02-21VMware vCenter, ESXi, ESX NFC协议内存破坏漏洞（CVE-2013-1659）

+5. 2013-02-06VMware vSphere产品客户端验证漏洞(CVE-2013-1405)

+6. 2012-12-21vCenter Server Appliance目录遍历漏洞(CVE-2012-6324)

+7. 2012-12-21vCenter Server Appliance任意文件下载漏洞

+8. 2012-04-12VMware多个产品本地权限提升漏洞

+9. 2012-03-09VMware vCenter Chargeback Manager信息泄露和拒绝服务漏洞

+10. 2011-11-01VMware vCenter产品JRE多个安全漏洞

+11. 2011-11-01VMware ESX Server多个安全漏洞

+12. 2011-03-30Linux平台上的VMware "vmrun"本地权限提升漏洞

+13. 2011-03-14VMware vCenter Orchestrator和Alive Enterprise远程代码执行漏洞

+14. 2010-09-25VMware Workstation <= 7.1.1 VMkbd.sys Denial of Service Exploit

+15. 2010-08-31VMware ESX Service Console多个安全漏洞

+16. 2010-05-05VMware View远程跨站脚本漏洞

+17. 2010-04-09VMware VMnc编解码器HexTile编码视频块解析堆溢出漏洞

+18. 2010-04-09VMWare Tools软件包库引用代码执行漏洞

+19. 2010-04-09VMware VMnc编解码器HexTile编码视频块多个堆溢出漏洞

+20. 2010-03-29VMware WebAccess URL转发安全漏洞

+21. 2009-11-23VMWare Virtual 8086 Linux Local Ring0 Exploit

+22. 2009-10-30Invalid #PF Exception Code in VMware can result in Guest Privilege Escalation

+23. 2009-10-27VMware PF异常本地权限提升漏洞

+24. 2009-10-08VMware Player和Workstation 'vmware-authd'远程拒绝服务漏洞

+25. 2009-10-02VMWare Fusion <= 2.0.5 vmx86 kext local PoC

+26. 2009-10-02VMWare Fusion <= 2.0.5 vmx86 kext local kernel root exploit

+27. 2009-10-01VMWare Fusion本地拒绝服务和权限提升漏洞

+28. 2009-09-07VMWare VMnc Codec Mismatched Dimensions Buffer Overflow

+29. 2009-09-02VMware Studio虚拟应用设备WEB接口文件上传目录遍历漏洞

+30. 2009-08-21VMware Server libpng Uninitialised Pointer Arrays Vulnerability

+>

+

+**二、Citrix XenServer漏洞：**

+>目前的XEN的安全性还有较多的安全问题。Xen0是一个安全瓶颈，其功能较其他域强，所以容易被敌手发起蠕虫、病毒、DoS等各种攻击，如果Xen0瘫痪或者被敌手攻破，那么将破坏整个虚拟机系统。XEN的隐通道问题没有解决，这样在XEN上就不可能运行高安全等级的操作系统。虚拟机的使用为数字版权保护提出新的挑战。虚拟机共享同一套硬件设备，一些网络安全协议可能更加容易遭到恶意破坏和恶意实施。此外，XEN提供了方便的保存和恢复机制，使得操作系统数据的回滚和重放非常容易。这些将影响操作本身的密码特性。目前XEN本身的健壮性还有待完善，其资源隔离和共享访问控制等需要进一步的完善和加强。

+>

+　　消弱XEN0的功能，将其功能分解到其他域，将会适当减少XEN0的瓶颈作用。对于隐通道问题的分析和处理，是一个难解的问题，需要更多研究者的努力。为了资源隔离和资源共享女全，需要实行严格的访问控制策略。例如IBM将sHyper加入XEN中进行强制访问控制；Intel将要实施的LT (LaGrande Technology)技术，能有效增强设备隔离，实现I/O保护、内存越界保护、键盘、显示的隔离保护等。通过虚拟TPM，建立可信域。另外对于虚拟机系统的管理需要特别的注意和加强。以上这些措施都可以有效增强XEN的安全性。

+1. 2012-09-05XenSource Xen 'physdev_get_free_pirq'拒绝服务漏洞

+2. 2012-09-05Citrix XenServer本地权限提升漏洞(CVE-2012-4606)

+3. 2011-07-29Citrix XenApp / XenDesktop Stack-Based Buffer Overflow

+4. 2011-07-29Citrix XenApp / XenDesktop XML Service Heap Corruption

+5. 2011-07-27Citrix XenApp和XenDesktop XML Service interface远程代码执行漏洞

+6. 2011-05-31Red Hat Xen管理程序实现本地Guest拒绝服务漏洞

+7. 2011-05-12Citrix XenServer多个不明细节拒绝服务漏洞

+8. 2011-05-12Citrix XenServer凭证本地信息泄露漏洞

+9. 2010-09-29Linux Kernel Xen Hypervisor实现拒绝服务漏洞

+10. 2009-12-10Xenorate 2.50(.xpl) universal Local Buffer Overflow Exploit (SEH)

+11. 2009-12-10Xenorate 2.50(.xpl) universal Local Buffer Overflow Exploit (SEH) (meta)

+12. 2009-09-28Xen pygrub本地验证绕过漏洞

+13. 2009-08-18Xenorate Media Player 2.6.0.0 (.xpl) Universal Local Buffer Exploit (SEH)

+14. 2009-07-10Citrix XenCenterWeb (XSS/SQL/RCE) Multiple Remote Vulnerabilities

+15. 2009-07-07Citrix XenCenterWeb多个输入验证漏洞

+16. 2009-05-14Xen hypervisor_callback()函数本地拒绝服务漏洞

+17. 2009-04-14XEngineSoft PMS/MGS/NM/AMS 1.0 (Auth Bypass) SQL Injection Vulns

+18. 2008-07-18Citrix XenServer XenAPI HTTP接口跨站脚本漏洞

+19. 2008-06-25Xen超虚拟化帧缓冲区后端帧缓冲区处理漏洞

+20. 2008-02-17Simple CMS <= 1.0.3 (indexen.php area) Remote SQL Injection Exploit



 

-     1. 系统虚拟化：原理与实现。

+1.[http://www.jsxubar.info/%E8%99%9A%E6%8B%9F%E5%8C%96%E4%BA%A7%E5%93%81%E6%AF%94%E8%BE%83.html](http://www.jsxubar.info/%E8%99%9A%E6%8B%9F%E5%8C%96%E4%BA%A7%E5%93%81%E6%AF%94%E8%BE%83.html "虚拟化 – VMware , Xen 和 Hyper-V 虚拟化产品比较")

+

+2.[http://www.cnblogs.com/BloodAndBone/archive/2010/11/02/1866907.html](http://www.cnblogs.com/BloodAndBone/archive/2010/11/02/1866907.html "xen虚拟化及工作原理")

+

+3.[http://zh.wikipedia.org/wiki/Xen](http://zh.wikipedia.org/wiki/Xen "维基百科-Xen")

+

+4.[http://zh.wikipedia.org/wiki/Xen](http://zh.wikipedia.org/wiki/Xen "虚拟机比较")

+

+5.[http://server.zol.com.cn/148/1484277.html](http://server.zol.com.cn/148/1484277.html "虚拟化：Xen和VMware市场上谁更成熟")

+

+6.[http://www.searchvirtual.com.cn/showcontent_74341.htm](http://www.searchvirtual.com.cn/showcontent_74341.htm "新版XenServer 6.2免费开源了 你怎么看")

+

+7.[http://labs.chinamobile.com/mblog/878337_184928](http://labs.chinamobile.com/mblog/878337_184928 "VMware与Xen、KVM虚拟化平台差异化浅析")

+

+8.[http://zh.wikipedia.org/wiki/Vmware](http://zh.wikipedia.org/wiki/Vmware "VMware")

+

+9.[http://sebug.net/appdir/VMWare](http://sebug.net/appdir/VMWare "Sebug漏洞库-VMware")

+

+10.[http://sebug.net/search?wd=xen](http://sebug.net/search?wd=xen "Sebug漏洞库-Xen")

+

+11.[http://www.cloudguide.com.cn/news/show/id/1956.html](http://www.cloudguide.com.cn/news/show/id/1956.html "Xen平台虚拟化安全问题解析")

+

+12.[http://www.searchvirtual.com.cn/showcontent_26520.htm](http://www.searchvirtual.com.cn/showcontent_26520.htm "虚拟化最主要的安全问题分析")

+

+13.支连意 云计算：Xen虚拟机与VMware ESX虚拟机性能及稳定性对比研究  软件导刊[11卷第3期]：46-48


## 参考资料 ##
1. 系统虚拟化：原理与实现。
2. vmware 技术手册。
