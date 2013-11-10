# VMware VS XEN #

  组名：王飞 ，chinawangfei

## 项目介绍 ##
  - 虚拟化软件的比较
    + 全虚拟化
        + Hypervisors通过一个防真硬件层为其上的每个Guest操作系统（虚拟机）防真出一个具有常用硬件设备的标准服务器，当一个运行的Guest系统试图用特权指令控制硬件时，hypervisor会将真实的硬件隐藏起来，并防真一个硬件设备给Guest系统，从而使得Guest系统无需修改代码就可以安全的访问硬件。该技术使得Guest系统无法任何修改就可在不支持Intel VT/AMD-V的CPU上运行，但该技术的复杂性也降低了系统的性能。

    + 半虚拟化技术
         + Guest系统在访问真实硬件时是重用当前系统的驱动，而不是通过防真的硬件实现的。Guest系统和hypervisor交互是通过一个高效，底层的API来实现的，这使得hypervisor和Guest系统可以共同最优化地使用底层的硬件和I/O，从而可获得极高的运行性能。

## 功能比较 ##
  - XenServer 
    + 虚拟化技术:半虚拟化
    + 硬件要求:
          - CPU必须是64位CPU
          - CPU必需支持Intel VT/AMD-V,否则不支持Windows Guest系统            
    + 支持的Guest系统:Windows系列，Linux系列
  - VMWare ESX
    + 虚拟化技术:全虚拟化
    + 硬件要求:不支持IDE，SATA硬盘
    + 支持的Guest系统:几乎支持所有的可运行在 x86架构上的系统

## 其他比较 ##
  - XenServer 
    + P2V迁移:
          - 自带Linux的P2V迁移工具
          - Windows的迁移采用第三方工具
    + V2V迁移:有第三方免费工具将VMWare虚拟机转换为XenServer虚拟机
  - VMWare ESX
    + P2V迁移:
          - 自带Windows的P2V迁移工具

## 结合自身需要评估后的结论 ##
  - 暂无实际经验。
 
## 参考资料 ##
  - http://wenku.it168.com/d_000111788.shtml