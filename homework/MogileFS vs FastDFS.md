#  MogileFS vs FastDFS #

  **组名：**DFS-008   

  **成员：**丁进福 dingjinfu、岳大炯moonblue333、王文波 conanbob、雷冬 ldkof99
   

## 项目介绍 ##
MogileFS、 FastDFS是两个分布式文件系统 DFS（Distributed File System）。DFS在云计算框架中属于存储层面，介绍如下：

### *MogileFS* ###

MogileFS 是一个开源的分布式文件系统，用于组建分布式文件集群，由LiveJournal 旗下 Danga Interactive 公司开发，Danga 团队开发了包括 Memcached、MogileFS、Perlbal 等不错的开源项目：(注：Perlbal 是一个强大的 Perl 写的反向代理服务器)。目前国内使用 MogileFS 的有图片托管网站 yupoo 等。

### *FastDFS：* ###

FastDFS是一款类Google FS的开源分布式文件系统，它用纯C语言实现，支持Linux、FreeBSD、AIX等UNIX系统。它只能通过专有API对文件进行存取访问，不支持 POSIX接口方式，不能mount使用。准确地讲，Google FS以及FastDFS、mogileFS、HDFS、TFS等类Google FS都不是系统级的分布式文件系统，而是应用级的分布式文件存储服务。
FastDFS是为互联网应用量身定做，充分考虑了冗余备份、负载均衡、线性扩容等机制，并注重高可用、高性能等指标。和现有的类 Google FS分布式文件系统相比，FastDFS的架构和设计理念有其独到之处，主要体现在轻量级、分组方式和对等结构三个方面。


## 功能比较 ##

### *Mogile FS* ###
MogileFS是一个分布式文件存储的解决方案，它能够做到不需要特殊的核心组件、无单点失败、自动的文件复制、比RAID好多了、传输中立，无特殊协议(客户端可以通过NFS或HTTP来和MogileFS通 信)、简单的命名空间、不用共享任何东西、不需要RAID、不会碰到文件系统本身的不可知情况 等等优点。
 Mogilefs分为几部分
1. 数据库（MySQL）：你可以用 mogdbsetup程序来初始化数据库。数据库保存了Mogilefs的所有元数据，你可以单独拿数据库服务器来做，也可以跟其他程序跑在一起，数据库 部分非常重要，类似邮件系统的认证中心那么重要，如果这儿挂了，那么整个Mogilefs将处于不可用状态。因此最好是HA结构。
2. 存储节点：mogstored 程序的启动将使本机成为一个存储节点。启动时默认去读/etc/mogilefs/mogstored.conf ，具体配置可以参考配置部分。mogstored启动后，便可以通过mogadm增加这台机器到cluster中。一台机器可以只运行一个 mogstored作为存储节点即可，也可以同时运行其他程序。
3. trackers（跟踪器）：mogilefsd即 trackers程序，类似mogilefs的wiki上介绍的，trackers做了很多工作，Replication ，Deletion，Query，Reaper，Monitor等等。mogadm,mogtool的所有操作都要跟trackers打交 道，Client的一些操作也需要定义好trackers，因此最好同时运行多个trackers来做负载均衡。trackers也可以只运行在一台机器 上，也可以跟其他程序运行在一起，只要你配置好他的配置文件即可，默认在/etc/mogilefs/mogilefsd.conf。
4. 工具：主要就是mogadm，mogtool这两个工具了，用来在命令行下控制整个mogilefs系统以及查看状态等等。
5. Client：Client实际上是一个Perl的pm，可以写程序调用该pm来使用mogilefs系统，对整个系统进行读写操作。
Mogilefs在应用层没有特殊的组件要求。不支持对一个文件的随机读写，因此注定了只适合做一部分应用。比如图片服务，静态HTML服务。即文件写入后基本上不需要修改的应用，当然你也可以生成一个新的文件覆盖上去。
存储节点、跟踪器、跟踪用的数据库均可运行在多个机器上，因此没有单点失败。
MogileFS可以在不同的机器之间进行文件复制，因此文件始终是可用的。
MogileFS客户端可以通过NFS或HTTP来和MogileFS的存储节点来通信，传输中立，无特殊协议。
MogileFS具有简单的命名空间，文件通过一个给定的key来确定，是一个全局的命名空间。只要你愿意，可以自己生成多个命名空间。
MogileFS不需要依靠昂贵的SAN来共享磁盘，每个机器只用维护好自己的磁盘，不用共享任何东西。 
在MogileFS中的磁盘可以是做了RAID的也可以是没有，如果是为了安全性着想的话RAID没有必要买了，因为MogileFS已经提供了。
在MogileFS中的存储节点的磁盘可以被格式化成多种格式（ext3,reiserFS等等）。MogilesFS会做自己内部目录的哈希，所以它不会碰到文件系统本身的一些限制，比如一个目录中的最大文件数。你可以放心的使用，不会碰到文件系统本身的不可知情况。

### *FastDFS：* ###

FastDFS是一个开源的分布式文件系统，她对文件进行管理，功能包括：文件存储、文件同步、文件访问（文件上传、文件下载）等，解决了大容量存储和负载均衡的问题。特别适合以文件为载体的在线服务，如相册网站、视频网站等等。
FastDFS服务端有两个角色：跟踪器（tracker）和存储节点（storage）。跟踪器主要做调度工作，在访问上起负载均衡的作用。
存储节点存储文件，完成文件管理的所有功能：存储、同步和提供存取接口，FastDFS同时对文件的meta data进行管理。所谓文件的meta data就是文件的相关属性，以键值对（key value pair）方式表示，如：width=1024，其中的key为width，value为1024。文件meta data是文件属性列表，可以包含多个键值对。

跟踪器和存储节点都可以由一台或多台服务器构成。跟踪器和存储节点中的服务器均可以随时增加或下线而不会影响线上服务。其中跟踪器中的所有服务器都是对等的，可以根据服务器的压力情况随时增加或减少。
为了支持大容量，存储节点（服务器）采用了分卷（或分组）的组织方式。存储系统由一个或多个卷组成，卷与卷之间的文件是相互独立的，所有卷 的文件容量累加就是整个存储系统中的文件容量。一个卷可以由一台或多台存储服务器组成，一个卷下的存储服务器中的文件都是相同的，卷中的多台存储服务器起 到了冗余备份和负载均衡的作用。
在卷中增加服务器时，同步已有的文件由系统自动完成，同步完成后，系统自动将新增服务器切换到线上提供服务。
当存储空间不足或即将耗尽时，可以动态添加卷。只需要增加一台或多台服务器，并将它们配置为一个新的卷，这样就扩大了存储系统的容量。
FastDFS中的文件标识分为两个部分：卷名和文件名，二者缺一不可。
 
上传文件交互过程：
1. client询问tracker上传到的storage，不需要附加参数；
2. tracker返回一台可用的storage；
3. client直接和storage通讯完成文件上传。 
 
下载文件交互过程：
1. client询问tracker下载文件的storage，参数为文件标识（卷名和文件名）；
2. tracker返回一台可用的storage；
3. client直接和storage通讯完成文件下载。
需要说明的是，client为使用FastDFS服务的调用方，client也应该是一台服务器，它对tracker和storage的调用均为服务器间的调用。

## 其他比较 ##
<table>
	<tr align="center">
		<td><strong>序号</strong></td>
		<td><strong>指标</strong></td>
		<td><strong>FastDFS</strong></td>
		<td><strong>MogileFS</strong></td>
	</tr>
	<tr>
		<td>1</td>
		<td>系统简洁性</td>
		<td>简洁：只有两角色(tracker、storage)</td>
		<td>一般：三角色（tracker、storage和存储文件信息的mysql.db）</td>
	</tr>
	<tr>
		<td>2</td>
		<td>系统性能</td>
		<td>很高（没有使用数据库，文件同步直接点对点，不经过tracker中转）</td>
		<td>高（使用mysql存储文件索引等信息，文件同步通过tracker调度和中转）</td>
	</tr>
	<tr>
		<td>3</td>
		<td>系统稳定性</td>
		<td>高（C语言开发，支持高并发和高负载）</td>
		<td>一般（Per1语言开发，高并发和高负载支持一般）</td>
	</tr>
	<tr>
		<td>4</td>
		<td>RAID方式</td>
		<td>分组（组内冗余），灵活性较大</td>
		<td>动态冗余，灵活性一般</td>
	</tr>
	<tr>
		<td>5</td>
		<td>通讯协议</td>
		<td>专有协议，下载文件支持HTTP</td>
		<td>HTTP</td>
	</tr>
	<tr>
		<td>6</td>
		<td>技术文档</td>
		<td>较详细</td>
		<td>较少</td>
	</tr>
	<tr>
		<td>7</td>
		<td>文件附加属性（meta data）</td>
		<td>支持</td>
		<td>不支持</td>
	</tr>
	<tr>
		<td>8</td>
		<td>相同文件只保留一份</td>
		<td>支持</td>
		<td>不支持</td>
	</tr>
	<tr>
		<td>9</td>
		<td>下载文件时支持文件偏移量</td>
		<td>支持</td>
		<td>不支持</td>
	</tr>
</table> 

## 结合自身需要评估后的结论 ##

综合以上情况，FastDFS在系统简洁性、性能、及稳定性等方面均优于MogileFS，应用范围也更广一些。
（FastDFS有10＋公司在使用；一个集群中的存储GROUP数超过25个，机器超过50台，存储容量超过300TB,文件数达到1600万，group持续增长。）


## 组员贡献 ##
丁进福创建主干，岳大炯对其进行修改补充，并对其它比较进行表格对比。王文波以及雷冬进行相关资料的收集。

## 参考资料 ##
1.	MogileFS 一个开源的分布式文件系统http://bbs.chinaunix.net/thread-1235868-1-1.html
2.	分布式文件系统 MogileFS 安装手册http://bbs.chinaunix.net/thread-1976725-1-1.html
3.	FastDFS一个高效的分布式文件系统http://bbs.chinaunix.net/thread-2001101-1-1.html
