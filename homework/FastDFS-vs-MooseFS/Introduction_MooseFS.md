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
