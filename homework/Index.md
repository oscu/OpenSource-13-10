# 组名： 成员名称，id #

DFS-001: 

李怡石, watanuoli

马鑫,   maxinpony

# 题目介绍 #
本题目是比较两个分布式文件系统 DFS（Distributed File System）。  
DFS在云计算框架中属于IaaS存储层面，介绍如下   

- [wiki](http://en.wikipedia.org/wiki/Distributed_File_System_(Microsoft\))
  
官方网站：  
[MooseFS](http://www.moosefs.org)    
[FastDFS](https://code.google.com/p/fastdfs/wiki/Overview)  


----------
# 评估内容： #

## 项目介绍 ##
- MooseFS
MooseFS是一个运行于多台物理机上的网络分布式文件系统，特性如下：

Unix-alike，
	支持层级目录结构
	支持POSIX文件属性（rwx，访问时间）
	支持块设备文件，管道文件和套接口文件等特殊文件类型
	支持文件的软连接和硬链接
	通过IP地址和密码限制客户端对文件系统的访问权限

高可用性，文件可以有多个拷贝。
动态扩展文件系统容量。
支持文件回收站功能
文件快照

## 组成  


- Managing server(master server) - 文件系统的管理节点，保存着每个文件的元数据（大小，属性，位置等）



- Metadata backup server(s)(metalogger server) - 作为Managing server的备份


- Data server(Chunk server) - 负责存储文件的多台机器

客户端访问文件系统是需要通过mfsmount，它从Managing Server获取文件信息。这方面与NFS的访问类似（mount）。

MooseFS是实现在用户空间的文件系统，因此可以在各种实现了FUSE的平台上安装。如(Linux, FreeBSD, MacOS X）


文件元数据（Metadata）放在managing server的内存中，定时以二进制文件和增量日志的形式同步保存到磁盘上，并同步到备份metaloggers上
 

文件数据被分为64Mib大小的分片（块）存储，同时可以配置在data servers上保留几个备份。
每个（Chunk）是位于磁盘上的一个文件。这些64Mib的文件分布在多个data server上并配置成多份拷贝，这样实现高可用性。

## 工作原理图： ##
![](http://www.moosefs.org/tl_files/mfs_folder/read862.png)

![](http://www.moosefs.org/tl_files/mfs_folder/write862.png)

通过从客户机挂载到MooseFS系统上，所有在的文件操作就像在本地文件系统之上。客户端操作系统内核把对文件的操作(read/write)通过FUSE模块传到mfsmount进程，后者再经由网络与Managing server 和 data server交换信息，整个过程对于用户是看不到的。（用户看到的是操作本地文件） 


mfsmount进程每次和managing server通信的时候无非以下几种文件操作：  
1.创建文件  
2.删除文件  
3.读目录  
4.修改文件属性xwr  
5.修改文件尺寸  
mfsmount与data server直接相通存储文件chunk。当完成写文件后，managing server会从mfsmount取回文件信息来更新文件长度和最后修改时间。 

另外，data server之间会相互传播文件数据来实现冗余。
 
## 容错性： ##
管理员可以配置单个文件和目录的备份数量，这样就避免了单点故障带来的数据损失。
通过设置“goal”属性可以实现文件备份的数量，goal=1时文件只存在一台data server。重要的文件一般需要设置2+份拷贝。

当一台data server挂掉，一个具有两份拷贝的文件会失去这台server上的一个拷贝，剩下的拷贝会选择一台活的data server把数据传播过去，这样仍然会维持两个拷贝数量。


文件系统扩容很方便，新data server可以随时加入，并且即时变为可用状态。


管理工具可以查询文件状态并设置拷贝数量。


如果一个文件跨多个chunk存储，每个chunk上的分片数据都有一个版本号，当一个chunk所在data server宕机期间文件发生改变，在这个server恢复后，会对当前其他文件部分做同步，发现版本滞后的情况下，会自动清理废弃的chunk，腾出空间分配新chunk。


客户机的文件操作失败不会影响文件的一致性。

 
## 平台： ##
MooseFS可以安装在支持FUSE的操作系统之上。以下列出适用的系统：
Linux(内核版本2.6.14以及后续版本)
FreeBSD
OpenSolaris
MacOS X


master server, metalogger server 和 chunk servers也可以运行在Solaris或Windows Cygwin模拟器上，但是没有FUSE支持，就不能挂载文件系统

参考：
http://www.moosefs.org

- FastDFS

FastDFS是一款开源的高性能分布式文件系统。主要功能包括文件存储、同步、访问（上传下载），支持海量文件存储，负载均衡等。多用于照片，视频文件共享的网站。

FastDFS中包含两个角色：tracker和storage。
tracker掌管文件访问的请求调度和负载均衡。
storage负责存储，同步，提供文件访问接口。storage还要管理文件元数据（Key-Value形式）。
![](http://cn.yimg.com/ncp28/content/08195_487b02ea16406_655_644_135_132.jpg)

tracker和storage集群可以随时加入新机器，不会影响在线服务，tracker采用点对点通信模式。
storage server采用文件卷组（volume group）的形式做集群，整个storage系统由一个或多个
Volume组成，每个Volume包含多台storage server,每个server上持有相同的文件数据互为备份，对Volume中每台服务器的访问是负载均衡的。当加入一台storage server后，Volume上的文件会复制到这台机器上，完成后新机器上线对外服务。

FastDFS上文件的标识由两部分组成Volume名和文件名。

文件上传过程：  
![](http://cn.yimg.com/ncp28/content/08195_487b030816241_445_285_135_86.jpg)

文件下载过程：  
![](http://cn.yimg.com/ncp28/content/08195_487b0320124c5_445_285_135_86.jpg)

参考：
https://code.google.com/p/fastdfs/
http://www.programmer.com.cn/4380/
 
## 功能点对比分析  
 
|比较项目|MooseFS  | FastDFS|
|----|------------- | -------------|
|单点故障 |  Managing server,metalogger互为备份，无单点故障 | 一个group至少有两台服务器，不存在单点故障的问题 |
|适合单个文件大小 | 64MB以上大文件 | 小文件 | 
|负载均衡 | 支持 | 支持 |
|文件元数据 | Managing server管理 | storage分散管理 |
|文件是否有多个副本 | 是 | 是 |
|扩展性 | 在线，即时 | 在线，即时 |
|文件操作形式 | POSIX，Unix-alike，local file access | Volume+File Name |
|[FUSE](http://zh.wikipedia.org/wiki/FUSE)  | 支持 | 不支持 |
|源产地 | Poland | China对mogileFS改进 |
|应用场合 | 照片，电子文档，视频 | 照片，电子文档，视频 |  
|模块 | Managing server,metalogger server,Chunk server | Tracker,Storage| 
|代码托管 | sourcegorge | google code|
|开发语言 | Perl |C |
|许可证|  GPL v3 | GPL v3 |

参考：

http://bbs.chinaunix.net/thread-1644309-1-1.html  
http://os.51cto.com/art/201209/355996.htm  
http://os.51cto.com/art/201209/355977.htm  
http://os.51cto.com/art/201209/356431.htm  
http://quanzhong.iteye.com/blog/947306    


## 社区活跃程度对比   

## MooseFS: 有各种形式的社区以及支持

Referenced from http://www.moosefs.org/contact.html

> If you are looking for professional support for MooseFS please visit this page:
> http://coretechnology.pl/support.php
>  
> The best way to get free help with Moose File System is by sending email to its mailing list at:
> moosefs-users@lists.sourceforge.net
> 
> You can also subscribe to this mailing list at:
> https://lists.sourceforge.net/lists/listinfo/moosefs-users
>  
> And if you want to check the archive, please visit:
> https://sourceforge.net/mailarchive/forum.php?forum_name=moosefs-users
>  
> If you'd like to join us or other users on IRC:
> Webchat: Go to http://webchat.freenode.net/
> 
> For a more detailled help, please see http://freenode.net/faq.shtml and your IRC client documentation.
>  
> If you want to submit feature request write it here:
> http://sourceforge.net/tracker/?group_id=228631&atid=1075722
>  
> If you want to submit bug release please write it here:
> http://sourceforge.net/tracker/?group_id=228631&atid=1075719

## FastDFS：主要讨论区在ChinaUnix，形式比较单一 ##

http://bbs.chinaunix.net/forum-240-1.html  
https://code.google.com/p/fastdfs/w/list

## 应用    

## MooseFS 
官方地图标注了MooseFS的地理分布
[Who is using MooseFS](http://www.moosefs.org/who-is-using-moosefs.html)   
![](Who%20is%20using%20MooseFS.png)  
国内豆瓣在用

## FastDFS ##
国内20+公司，名称不详，一部分做网盘。 

## 组员贡献 ##
马鑫： 题目介绍、项目介绍

李怡石： 功能点对比分析、社区活跃程度对比、应用