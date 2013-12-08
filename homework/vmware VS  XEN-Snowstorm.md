# VMware VS  XEN
  **组名**：
  >snowstorm
  
  **成员**：
   >
    1. 王真      wangz
    2. 黄梦溪    MengxiHuang
    3. 马永龙    marting007

## 项目介绍 ##
   >云计算的兴起，使得越来越多的企业意识到，虚拟化是构建云基础架构不可或缺的关键技术之一,然而面对众多的虚拟化技术我们又十分茫然，本文对在商业领域独占鳌头的VMware和其强有力竞争对手，基于Linux平台开放源代码的Xen做下对比，为我们选择合适的虚拟化技术提供帮助。
   >
   本文从虚拟化基础知识开始到VWmare、Xen产品的介绍，然后从虚拟化技术、系统平台支持、软件许可、软件成熟度、性能稳定性、使用情况、安全问题几方面进行对比，以使大家在选择二者时有一个清晰的思路。

   
## 虚拟化背景知识 ##

### 虚拟化发展阶段 ###
>
1. **虚拟化初级阶段**：在虚拟化早期，人们采用模拟软件技术模拟出计算机硬件和软件。模拟层与操作系统对话，而操作系统与计算机硬件对话。在模拟层中安装的操作系统并不知道自己是被安装在模拟环境下的，你可以按照常规的方法安装操作系统。这种虚拟化需要付出很大的性能代价。
2. **虚拟化高级阶段**：随着虚拟技术发展的不断深化，虚拟化被带到了一个更高的级别。在模拟层（负责被虚拟机器的指令翻译）和硬件之间，不需要任何主机操作系统运行硬件上的虚拟机。虚拟机监控器直接运行在硬件上。由此虚拟化变得更加高效。

### 虚拟机监视器模型 ###
>
Goldberg定义了两种虚拟机监视器模型，即Type I VMM和Type II VMM:
>
1. **Type I VMM:** 在操作系统之前预先安装，然后在此虚拟机监视器之上安装客户操作系统，它可以在硬件支持下拥有最佳性能，如IBM VM/370，VMware ESX Server，Xen，Denali等均属于这样的虚拟机。Type I VMM通常都是以一个轻量级操作系统的形式实现。
>
2. **Type II VMM:** 则是安装在已有的主机操作系统（宿主操作系统）之上，此类虚拟机监视器通过宿主主操作系统来管理和访问各类资源（如文件和各类I/O设备等)，如VMware Workstation、Parallel Workstation等。

### 虚拟化技术主要类型 ###
>
1. **硬件仿真 Hardware Emulation**: 在宿主系统上创建一个硬件 VM 来仿真出一套硬件。速度比较慢,不需要作任何修改。可以运行多个虚拟机，每个虚拟器仿真一个不同的处理器。
2. **完全虚拟化**: 是将应用程序完全跟硬件抽象出来。虚拟机与虚拟机监控器（VMM）进行通信，而VMM则与硬件平台进行通信。其主要优势在于，它安装了一个未修改的操作系统，以VMware的ESX Server为代表。然而，这一中介层要求虚拟机捕获并模拟所有特权指令，导致性能可能降低 50％。另外，当在同一台机器中同时运行两个虚拟机时，完全虚拟化不支持资源的和谐共享。例如，运行在同一个服务器硬件上的两个 Web 服务器虚拟机不能共享他们当前未使用的网页。因此，他们之间的分区仍是粗粒度的。另外，在完全虚拟化中，运行虚拟机的主机操作系统可能产生单点故障。许可复杂性及扩展性的限制也是无法消除的顾虑。
3. **超虚拟或半虚拟化**: 的操作系统实例将被修改，从而使他们能够识别虚拟化层。因此，超级管理程序可以避免难以虚拟化的处理器指令，方法是使用具备此功能的程序调用来替换这些指令。结果，性能优于完全虚拟化的虚拟机。采用超虚拟化模式的虚拟化可以在现有的芯片上获得更好的性能，而且能在下一代启用了虚拟化的 x86 芯片上提供有力的优势，因此成为了一个新趋势。同时，它还可以在不修改主机操作系统的情况下实现机器间的和谐内存共享。另外，它保留了虚拟机的优点，能与 Linux 主机操作系统完美配合。
4. 
### VMware Xen产品介绍 ###

#### VMware产品介绍 ####
>
**1.VMware Workstation:**是VMware公司销售的商业软件产品之一。该工作站软件包含一个用于英特尔x86相容电脑的虚拟机套装，其允许用户同时创建和运行多个x86虚拟机。由于企业市场中高速增加的服务器的巨大数量，VMware工作站的声望获得了增长。
>
**2.VMware Player:**用于为虚拟机提供宿主服务的免费软件产品VMware Player可运行由其它VMware产品产生的客户虚拟机，同时也可以自行创建新的虚拟机。
>
**3.VMware Fusion:**是VMware面向苹果电脑推出的一款虚拟机软件。
>
**4.VMware Server:**在2006年2月6日VMware发布了VMware Server产品的1.0版本，取代原先的VMware GSX Server。VMware服务器可以创建、编辑、运行虚拟机。除了具有可以运行由其它VMware产品创建的虚拟机的功能外，它还可运行由微软Virtual PC产品创建的虚拟机。VMware国际公司将VMware服务器产品作为可免费获得的产品，这是因为希望用户们最终能选择升级至VMware ESX服务器产品。
>
**5.VMware ESX:**ESX 服务器使用了衍生自史丹佛大学（Stanford Univ.）开发的SimOS核心，该核心在硬件初始化后替换原开机的Linux内核。ESX服务器2.x的服务控制平台（亦称为“COS”或“vmnix”）是基于Red Hat Linux 7.2的。ESX服务器3.0的服务控制平台源自一个 RedHat 7.2的经过修改的版本——它是作为一个用来加载vmkernel的引导加载程序运行的，并提供了各种管理界面（如CLI、浏览器界面MUI、远程控制台）。该虚拟化系统管理的方式提供了更少的管理开销以及更好的控制和为虚拟机分配资源时能达到的粒度（指精细的程度）；这也增加了安全性，从而使VMware ESX成为一种企业级产品。
>
**6.VMware ESXi:**Vmware ESXi是Vmware vSphere 4.1版本开始提供的服务器系统。相比Vmware ESX，ESXi剔除了基于Red Hat Linux的服务控制平台，使VMware 代理可以直接在VMkernel上运行。由于脱离了对基于Linux的控制台操作系统的依赖，整个软件平台的尺寸由ESX的约2GB缩减至不到150MB，并消除了底层Linux系统可能带来的安全性和稳定性隐患，而获得授权的第三方模块也可在VMkernel上运行。ESXi同时使用了新的管理控制台PowerCLI。
>
从Vmware vSphere 5.0版本开始，Vmware不再提供ESX服务器产品，ESXi成为Vmware产品线中唯一一款服务器平台产品。
>
**7. VMware vSphere：**
VMware vSphere，原称为VMware Infrastructure，是一整套虚拟化应用产品，它包含VMware ESX Server 4、VMware Virtual Center 4.0、最高支持8路的虚拟对称多处理器（Virtual SMP）和VMotion，以及例如VMware HA、VMware DRS和VMware统一备份服务等分布式服务。 VMware国际公司在2009年4月发布了VMware vSphere 4。该套装提供六个档次的组合方案

### Xen产品介绍 ###
>
**1. Xen Hypervisor:**
Xen Hypervisor 与 Esxi 作用类似,但又不一样.
>
Xen提供源码包,需要在物理机上先安装一个Linux操作系统,然后在其上安装Xen以及编译安装一个Xen的内核,然后使用这个Xen的内核来实现虚拟平台.。这是因为Xen采用的是半虚拟化,需要修改系统内核.而VMware是采用全虚拟化,基于动态指令转换,因此不需要修改系统内核.
>
管理工具为XenCenter,与vSphere Client功能差不多
>
**2. Xen Cloud Platform:**
简单来说，就是Xen Hypervisor 加上其它一些功能。
>
**3. XCI:** Xen的嵌入式方案
>
**4. HXEN – Hosted Xen:**HXEN就相当于VMware Workstation。

## 功能比较 ##

#### 虚拟化技术 ####
>
**一、VMware:**
WMware是全球最大的虚拟化厂商，该公司产品线漫长，主要包括桌面版的 Vmware workstation和企业版的VMWare  ESX server。它们使用的虚拟化技术主要是全虚拟，在加上硬件辅助虚拟化后，产品性能有所提高。
>
**二、Xen的半虚拟化:**
Xen通过一种叫做半虚拟化的技术获得高效能的表现（较少的效能损失，典型的情况下大约损失2%，在最糟的情况下会有8%的效能耗损；与其它使用完全的虚拟化却造成最高到20%损耗的其他解决方案形成一个明显的对比），甚至在某些与传统虚拟技术极度不友好的架构上（x86），Xen也有极佳的表现。与那些传统透过软件模拟实现硬件的虚拟机不同，在3.0版本及在Intel VT-X支援前的Xen需要让客户端操作系统（guest operating systems）与Xen API进行连接。到目前为止，这样连结已经可以运用在NetBSD，GNU/Linux，FreeBSD和贝尔实验室的Plan 9系统上。在Brainshare 2005会议上，Novell展示了NetWare与Xen的连通。与Windows XP连通的技术曾在Xen开发初期进行，但微软的协议未能允许它发布。Sun微系统公司也正积极研究Solaris与Xen的连结，使其能在Xen平台上运作。
>
**三、Xen的完全虚拟化:**
Intel对Xen贡献修改以支持其VT-X架构扩展，而AMD则修改以支持其AMD-V架构扩展。如系统处理器支持虚拟硬件扩展（Intel和AMD对本地支持虚拟化的扩展），这项技术将允许未修改的操作系统运行在Xen虚拟机中。事实上，那意味着性能的提升，并且你可以在没有进行任何协议不允许的修改的情况下对Windows进行虚拟。


#### 系统平台支持 ####
>
**一、VMware:**Windows，Red Hat，SuSE，Ubuntu，Netware，Solaris，FreeBSD等
>
**二、Xen:**Linux, Solaris, Windows XP & 2003 Server（需要3.0版和Vanderpool或Pacifica），九号计划, FreeBSD
>
Unix-like系统中的Xen:
>
1. Novell于2005年4月15日发布的SUSE Linux Professional 9.3已内含Xen 2.0.5c版本。
2. RedHat的Fedora Project于2005年6月13日发布的Fedora Core 4亦已内含Xen。
3. Xenophilia是一个基于Xen的Linux发行版。
4. Xen demo CD是一个运行Debian Linux的liveCD，使你在系统上试用Xen，不用安装到硬盘。
5. Debian Testing亦已内含Xen。
6. NetBSD 2.0包括对Xen 1.2的支持，即将发布的3.0包括对Xen 2.0的支持。
7. Oracle Linux支持Xen；还有Oracle VM的Xen管理软件。
   
#### 软件许可 ####
>
**一、VMware:**
>
1. VMware ESX Server：私有
2. VMware ESXi Server：私有
3. VMware Fusion：私有
4. VMware Server：私有（免费）
5. VMware Workstation：私有
6. VMware Player：私有（免费）
>
**二、Xen:** GPL


#### 软件成熟度 ####
>
VMware虚拟化产品提供集中管理功能，通过图形用户界面能够很好的执行任何管理操作，并有效的进行虚拟机集群管理。而对于开放源码软件来说，这种情况很少在应用中体现。
>
在谈到VMware和Xen的功能比较时，在很大程度上他们功能是相同的。实时迁移（Live migration），这个在VMware企业级虚拟化技术广泛应用的技术，Xen上也有着很强的实施，并且提供了多年的迁移支持。不同的是，VMware提供存储池技术或存储虚拟化，这些是Xen所不能提供的，因为这不是Xen的工作。因此，可以客观的说，VMware在产品成熟度上处于领先的位置。
>
Citrix公司在2007年8月以5亿美元收购了XenSource公司，在原有的平台上增加了一个完整的图形用户界面功能，同时XenServer还比VMware便宜，经过一段时间，新版XenServer 6.2免费开源。经过一段商业化的经历后，xen在软件成熟度上有了很大的提升，在几年前，我们可能会说VMware许可证的高成本是值得的，毕竟它为用户节省了这么多时间。而如今的经济形势下，削减成本变得更加普遍，恐怕Xen的开源代码的特点可能更有意义。

#### 性能稳定性 ####
>
1. Xen 虚拟机内部应用在性能方面与VMware虚拟
机内部应用有轻微差距，不是很明显。
2. Xen虚拟机在内部应用稳定性方面与VMware虚
拟机有一定差距。
3. Xen虚拟机在压力较大时，可能出现不稳定的情
况。
4. 对于Xen和VMware，同宿主机上其它虚拟机压
力大小对被测虚拟机影响不大。
>
综合上述分析，可以得出结论：基于Linux开发源代
码的Xen虚拟化与较成熟的VMware虚拟化相比在性能
及稳定性方面均有一定的差距。

#### 使用情况 ####
>
vmware是目前企业内部企业内较为常见的虚拟化平台，在国内的认知度很大，但是从官方数据来看其真实案例中最大规模主要集中在30，40台物理服务器左右，对于云计算所支撑的成百上千台服务器的规模暂时没有案例，另一方面vmware作为一个国外成熟的商业化软件其代码是完全封闭的，而作为与传统操作系统如windows,linux等同等重要的云操作系统之上未来可能运行大量国家与企业的的核心应用系统与数据，因此可能存在潜在的安全威胁。
>
xen和kvm作为成熟的开源虚拟化平台拥有最广泛的受众，同时也被Amazon、Openstack、华为、中国移动大云、美国航空航天局等公司机构的云平台选择，其中xen平台拥有10万台级别的应用案例，而kvm也有200台以上的相应案例存在。其中XEN的优势主要在其对CPU和内存的利用效率上，因此较多的被运营商采用。而KVM则由于其可靠性著称（KVM已经被集成在linux内核中，在日后的内核更新方面存在优势）因此更加适合企业内部使用。

#### 安全问题 ####
>
**一、WMware漏洞：**
>
1. 2013-09-06VMware ESX及ESXi缓冲区溢出漏洞（CVE-2013-3657）
2. 2013-08-29VMware ESXi及ESX NFC协议处理远程拒绝服务漏洞
3. 2013-04-25vCenter Server Appliance 任意代码执行漏洞(CVE-2013-3079)
4. 2013-02-21VMware vCenter, ESXi, ESX NFC协议内存破坏漏洞（CVE-2013-1659）
5. 2013-02-06VMware vSphere产品客户端验证漏洞(CVE-2013-1405)
6. 2012-12-21vCenter Server Appliance目录遍历漏洞(CVE-2012-6324)
7. 2012-12-21vCenter Server Appliance任意文件下载漏洞
8. 2012-04-12VMware多个产品本地权限提升漏洞
9. 2012-03-09VMware vCenter Chargeback Manager信息泄露和拒绝服务漏洞
10. 2011-11-01VMware vCenter产品JRE多个安全漏洞
11. 2011-11-01VMware ESX Server多个安全漏洞
12. 2011-03-30Linux平台上的VMware "vmrun"本地权限提升漏洞
13. 2011-03-14VMware vCenter Orchestrator和Alive Enterprise远程代码执行漏洞
14. 2010-09-25VMware Workstation <= 7.1.1 VMkbd.sys Denial of Service Exploit
15. 2010-08-31VMware ESX Service Console多个安全漏洞
16. 2010-05-05VMware View远程跨站脚本漏洞
17. 2010-04-09VMware VMnc编解码器HexTile编码视频块解析堆溢出漏洞
18. 2010-04-09VMWare Tools软件包库引用代码执行漏洞
19. 2010-04-09VMware VMnc编解码器HexTile编码视频块多个堆溢出漏洞
20. 2010-03-29VMware WebAccess URL转发安全漏洞
21. 2009-11-23VMWare Virtual 8086 Linux Local Ring0 Exploit
22. 2009-10-30Invalid #PF Exception Code in VMware can result in Guest Privilege Escalation
23. 2009-10-27VMware PF异常本地权限提升漏洞
24. 2009-10-08VMware Player和Workstation 'vmware-authd'远程拒绝服务漏洞
25. 2009-10-02VMWare Fusion <= 2.0.5 vmx86 kext local PoC
26. 2009-10-02VMWare Fusion <= 2.0.5 vmx86 kext local kernel root exploit
27. 2009-10-01VMWare Fusion本地拒绝服务和权限提升漏洞
28. 2009-09-07VMWare VMnc Codec Mismatched Dimensions Buffer Overflow
29. 2009-09-02VMware Studio虚拟应用设备WEB接口文件上传目录遍历漏洞
30. 2009-08-21VMware Server libpng Uninitialised Pointer Arrays Vulnerability
>
VMware ESXi有着与VMware ESX一样的许多安全问题。确保虚拟化安全要做的绝不仅仅是加固虚拟化主机。即便如此，许多人还是误以为VMware ESXi来得更安全。事实并非如此，因为它没有深层防御功能。任何进程都可以在虚拟机管理程序里面运行，并不仅仅限于主要的对象类型，比如vSwitch或虚拟机容器。大多数人还认为VMware ESXi是一个硬件设备，于是只采取了VMware推荐的多项安全加强措施中的一两项，又没有关注管理或访问VMware ESXi的方式。另外，我认为大多数人在启用安装的ESXi系统上的SSH功能。如果他们这么做，其实没有真正的安全可言，因为ESXi内部没有深层防御功能。
>
常被忽视的几个问题：第一个就是使用扁平化虚拟网络作为虚拟网络，而不是使用更稳健、更有保障的网络。这在使用VMsafe vApps时会很有必要。另一个问题是，许多人把管理工具与ESX主机服务控制台放在了防火墙的两侧，这么做是错误的。因为这样一来，他们就得开启许多不必要的端口。相反，他们应当把ESX管理控制台和vCenter工具放在防火墙的同一侧，并且限制只能使用一个协议，比如加密的远程桌面协议（RDP）。这样一来，管理员可以访问虚拟机，进而访问管理工具。最后一个常见的安全问题是，没有使用部署环境的网络/虚拟化主机，这种环境下的网络/虚拟化主机可以防范零日攻击。相反，有些人直接部署到生产环境；如果操作出错，虽然可以删除虚拟机，但这会在磁盘上留下痕迹。

**二、Citrix XenServer漏洞：**
>
1. 2012-09-05XenSource Xen 'physdev_get_free_pirq'拒绝服务漏洞
2. 2012-09-05Citrix XenServer本地权限提升漏洞(CVE-2012-4606)
3. 2011-07-29Citrix XenApp / XenDesktop Stack-Based Buffer Overflow
4. 2011-07-29Citrix XenApp / XenDesktop XML Service Heap Corruption
5. 2011-07-27Citrix XenApp和XenDesktop XML Service interface远程代码执行漏洞
6. 2011-05-31Red Hat Xen管理程序实现本地Guest拒绝服务漏洞
7. 2011-05-12Citrix XenServer多个不明细节拒绝服务漏洞
8. 2011-05-12Citrix XenServer凭证本地信息泄露漏洞
9. 2010-09-29Linux Kernel Xen Hypervisor实现拒绝服务漏洞
10. 2009-12-10Xenorate 2.50(.xpl) universal Local Buffer Overflow Exploit (SEH)
11. 2009-12-10Xenorate 2.50(.xpl) universal Local Buffer Overflow Exploit (SEH) (meta)
12. 2009-09-28Xen pygrub本地验证绕过漏洞
13. 2009-08-18Xenorate Media Player 2.6.0.0 (.xpl) Universal Local Buffer Exploit (SEH)
14. 2009-07-10Citrix XenCenterWeb (XSS/SQL/RCE) Multiple Remote Vulnerabilities
15. 2009-07-07Citrix XenCenterWeb多个输入验证漏洞
16. 2009-05-14Xen hypervisor_callback()函数本地拒绝服务漏洞
17. 2009-04-14XEngineSoft PMS/MGS/NM/AMS 1.0 (Auth Bypass) SQL Injection Vulns
18. 2008-07-18Citrix XenServer XenAPI HTTP接口跨站脚本漏洞
19. 2008-06-25Xen超虚拟化帧缓冲区后端帧缓冲区处理漏洞
20. 2008-02-17Simple CMS <= 1.0.3 (indexen.php area) Remote SQL Injection Exploit
>
　　目前的XEN的安全性还有较多的安全问题。Xen0是一个安全瓶颈，其功能较其他域强，所以容易被敌手发起蠕虫、病毒、DoS等各种攻击，如果Xen0瘫痪或者被敌手攻破，那么将破坏整个虚拟机系统。XEN的隐通道问题没有解决，这样在XEN上就不可能运行高安全等级的操作系统。虚拟机的使用为数字版权保护提出新的挑战。虚拟机共享同一套硬件设备，一些网络安全协议可能更加容易遭到恶意破坏和恶意实施。此外，XEN提供了方便的保存和恢复机制，使得操作系统数据的回滚和重放非常容易。这些将影响操作本身的密码特性。目前XEN本身的健壮性还有待完善，其资源隔离和共享访问控制等需要进一步的完善和加强。
>
　　消弱XEN0的功能，将其功能分解到其他域，将会适当减少XEN0的瓶颈作用。对于隐通道问题的分析和处理，是一个难解的问题，需要更多研究者的努力。为了资源隔离和资源共享女全，需要实行严格的访问控制策略。例如IBM将sHyper加入XEN中进行强制访问控制；Intel将要实施的LT (LaGrande Technology)技术，能有效增强设备隔离，实现I/O保护、内存越界保护、键盘、显示的隔离保护等。通过虚拟TPM，建立可信域。另外对于虚拟机系统的管理需要特别的注意和加强。以上这些措施都可以有效增强XEN的安全性。

## 结合自身需要评估后的结论 ##
 在选择上，应根据实际需求场景，VMware商用软件要付费，但管理和使用上简单，Xen开源免费但管理和使用需要专业的技能，所以学习或研究虚拟化技术当然Xen是首选，还有大的数据中心因为很多要定制开源的Xen就比VMware有竞争力，但对于小企业或安全性要求较高的企事业单位规模不大没有专业的技术团队商业化的VMware可能更适合
## 组员贡献 ##
**一、王真：**
功能点对比分析：（王真提供）
1. 虚拟化程度：完全虚拟化。
2. 虚拟化支持系统：win/linux/sun for x86/other. 3. 网络虚拟化支持：vmware 网络虚拟化，虚拟交换机可以提供以下功能
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

VMware和Xen是目前最流行的硬件抽象层虚拟机，在X86架构服务器上应用广泛。Xen的虚拟网络性能与真实主机接近，而比VMware Workslaion虚拟网络的性能好。如果在Windows平台上，由于不能修改操作系统，只能使用VMware Workslalion；如果在Linux平台上，由于Xen的效率更高，建议使用Xen。

vmware 应用场景：（王真提供） 公司要求虚拟机运行时将停机时间降至最低。借助 VMWARE 的 vMotion，通过专门的 vMotion 网络在主机之间移动正在运行的虚拟机的整个状态，且不会造成服务中断。

**二、黄梦晞：**
（由 黄梦晞 提交）
　　虚拟机监控器(VMM)虚拟计算平台的硬件资源，以支持多个虚拟机(VM)的同时运行。每个虚拟机独立运行一个操作系统，运行于虚拟机内的操作系统被称为客户操作系统(GOS)，虚拟机监控器为这些操作系统提供安全和高度的隔离。
    Xen是运行于Intel x86上的VMM，它支持多个GOS所未有的性能和隔离性同时运行，是遵循GMJ许可的开源软件。当前，运用Xen支持多个虚拟机，并且在每个虚拟机上各自运行单独的操作系统，复用计算平台的研究正逐渐成为国内外学者研究的热点。
　　Xen能为流行的3层架构互联网应用提供复用计算平台。3层架构互联网应用包括:(1)前端是HTTP服务器，负责处理用户输入输出；(2)中间是应用服务器，实现应用的核心功能；(3)后端是数据库服务器，存储用户数据。3层架构互联网的一个突出特点是用户仅与HTTP服务器交互，不与另外两个服务器交互。换言之，HTTP服务器是访问另外两个服务的单点入口或应用网关。
　　目前的XEN的安全性还有较多的安全问题。Xen0是一个安全瓶颈，其功能较其他域强，所以容易被敌手发起蠕虫、病毒、DoS等各种攻击，如果Xen0瘫痪或者被敌手攻破，那么将破坏整个虚拟机系统。XEN的隐通道问题没有解决，这样在XEN上就不可能运行高安全等级的操作系统。虚拟机的使用为数字版权保护提出新的挑战。虚拟机共享同一套硬件设备，一些网络安全协议可能更加容易遭到恶意破坏和恶意实施。此外，XEN提供了方便的保存和恢复机制，使得操作系统数据的回滚和重放非常容易。这些将影响操作本身的密码特性。目前XEN本身的健壮性还有待完善，其资源隔离和共享访问控制等需要进一步的完善和加强。

　　消弱XEN0的功能，将其功能分解到其他域，将会适当减少XEN0的瓶颈作用。对于隐通道问题的分析和处理，是一个难解的问题，需要更多研究者的努力。为了资源隔离和资源共享女全，需要实行严格的访问控制策略。例如IBM将sHyper加入XEN中进行强制访问控制；Intel将要实施的LT (LaGrande Technology)技术，能有效增强设备隔离，实现I/O保护、内存越界保护、键盘、显示的隔离保护等。通过虚拟TPM，建立可信域。另外对于虚拟机系统的管理需要特别的注意和加强。以上这些措施都可以有效增强XEN的安全性。
　　虽然目前XEN还有很多问题，但是山于其优越的性能、开源性和良好的架构，在全球各大公司，例如：Intel、AMD、HP、IBM等的积极参与下，XEN是业界最优秀的虚拟机之一。
　　
　　基于Linux开发源代码的Xen虚拟化与较成熟的VMware虚拟化相比在性能及稳定性方而均有一定的差距:
　　(1) Xen虚拟机内部应用在性能方面与VMware虚拟机内部应用有轻微差距，不是很明显。
　　(2)Xen虚拟机在内部应用稳定性方面与VMware虚拟机有一定差距。
　　(3) Xen虚拟机在压力较大时，可能出现小稳定的情况。
　　(4)对于Xen和VMware，同宿主机上其它虚拟机压力大小对被测虚拟机影响小大。

**三、马永龙：**
其余资料收集整合及撰写本文

## 参考资料 ##

1.[http://www.jsxubar.info/%E8%99%9A%E6%8B%9F%E5%8C%96%E4%BA%A7%E5%93%81%E6%AF%94%E8%BE%83.html](http://www.jsxubar.info/%E8%99%9A%E6%8B%9F%E5%8C%96%E4%BA%A7%E5%93%81%E6%AF%94%E8%BE%83.html "虚拟化 – VMware , Xen 和 Hyper-V 虚拟化产品比较")

2.[http://www.cnblogs.com/BloodAndBone/archive/2010/11/02/1866907.html](http://www.cnblogs.com/BloodAndBone/archive/2010/11/02/1866907.html "xen虚拟化及工作原理")

3.[http://zh.wikipedia.org/wiki/Xen](http://zh.wikipedia.org/wiki/Xen "维基百科-Xen")

4.[http://zh.wikipedia.org/wiki/Xen](http://zh.wikipedia.org/wiki/Xen "虚拟机比较")

5.[http://server.zol.com.cn/148/1484277.html](http://server.zol.com.cn/148/1484277.html "虚拟化：Xen和VMware市场上谁更成熟")

6.[http://www.searchvirtual.com.cn/showcontent_74341.htm](http://www.searchvirtual.com.cn/showcontent_74341.htm "新版XenServer 6.2免费开源了 你怎么看")

7.[http://labs.chinamobile.com/mblog/878337_184928](http://labs.chinamobile.com/mblog/878337_184928 "VMware与Xen、KVM虚拟化平台差异化浅析")

8.[http://zh.wikipedia.org/wiki/Vmware](http://zh.wikipedia.org/wiki/Vmware "VMware")

9.[http://sebug.net/appdir/VMWare](http://sebug.net/appdir/VMWare "Sebug漏洞库-VMware")

10.[http://sebug.net/search?wd=xen](http://sebug.net/search?wd=xen "Sebug漏洞库-Xen")

11.[http://www.cloudguide.com.cn/news/show/id/1956.html](http://www.cloudguide.com.cn/news/show/id/1956.html "Xen平台虚拟化安全问题解析")

12.[http://www.searchvirtual.com.cn/showcontent_26520.htm](http://www.searchvirtual.com.cn/showcontent_26520.htm "虚拟化最主要的安全问题分析")

13.支连意 云计算：Xen虚拟机与VMware ESX虚拟机性能及稳定性对比研究  软件导刊[11卷第3期]：46-48
