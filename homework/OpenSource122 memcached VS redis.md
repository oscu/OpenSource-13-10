# memcached VS redis #

  组名：成员名称，id
  OpenSource122：
  	刘健 ticnic
	崔灿 finecci
	石占伟
	任峰杰

## 项目介绍 ##
### memcached ###
#### 简介 ####
memcached是一套分布式的高速缓存系统，由LiveJournal的Brad Fitzpatrick开发，目前被许多网站使用。这是一套开放源代码软件，以BSD license授权发布。
memcached缺乏认证以及安全管制，这代表应该将memcached服务器放置在防火墙后。
memcached的API使用三十二比特的循环冗余校验（CRC-32）计算键值后，将数据分散在不同的机器上。当表格满了以后，接下来新增的数据会以LRU机制替换掉。由于memcached通常只是当作高速缓存系统使用，所以使用memcached的应用程序在写回较慢的系统时（像是后端的数据库）需要额外的代码更新memcached内的数据。

#### 客户端支持 ####
Memcached的客户端软件实现非常多，包括C/C++, PHP, Java, Python, Ruby, Perl, Erlang, Lua等。

#### 安装方法 ####
在Window系统下，Memcached的安装非常方便，只需从以上给出的地址下载可执行软件然后运行memcached.exe –d install即可完成安装。在Linux等系统下，我们首先需要安装libevent，然后从获取源码，make && make install即可。默认情况下，Memcached的服务器启动程序会安装到/usr/local/bin目录下。在启动Memcached时，我们可以为其配置不同的启动参数。

#### 使用单位 ####
* Digg
* Facebook（同时也回馈了许多代码）
* Meetup.com（提供memcached对Java的连接库）
* Slashdot
* Wikipedia

### redis ###
#### 简介 ####
Redis是一个开源、支持网络、基于内存、键值对存储数据库，使用ANSI C编写。其开发由VMware主持。Redis使用C语言开发，在大多数像Linux、BSD和Solaris等POSIX系统上无需任何外部依赖就可以使用。
Redis是一个key-value存储系统。和Memcached类似，它支持存储的value类型相对更多，包括string(字符串)、list(链表)、set(集合)、zset(sorted set --有序集合)和hash（哈希类型）。这些数据类型都支持push/pop、add/remove及取交集并集和差集及更丰富的操作，而且这些操作都是原子性的。在此基础上，redis支持各种不同方式的排序。与memcached一样，为了保证效率，数据都是缓存在内存中。区别的是redis会周期性的把更新的数据写入磁盘或者把修改操作写入追加的记录文件，并且在此基础上实现了master-slave(主从)同步。

#### 客户端支持 ####
Redis支持的客户端语言非常丰富，常用的计算机语言如C、C#、C++、Object-C、PHP、Python、Java、Perl、Lua、Erlang等均有可用的客户端来访问Redis服务器。

#### 安装方法 ####
Redis的安装非常方便，只需从http://redis.io/download获取源码，然后make && make install即可。默认情况下，Redis的服务器启动程序和客户端程序会安装到/usr/local/bin目录下。在启动Redis服务器时，我们需要为其指定一个配置文件，缺省情况下配置文件在Redis的源码目录下，文件名为redis.conf。

#### 使用单位 ####
* 新浪
* 淘宝
* GitHub
* Pinterest
* Stack Overflow
* Flickr
* Instagram
* Twitter

## 功能比较 ##

## 其他比较 ##

## 结合自身需要评估后的结论 ##

## 组员贡献 ##
刘健 ticnic 参与章节：整体结构、项目介绍
崔灿 finecci 参与章节：
石占伟 参与章节：
任峰杰 参与章节：                                                            

## 参考资料 ##
* [百度百科](http://baike.baidu.com/)
* [维基百科](http://zh.wikipedia.org/)
* [谈谈Memcached与Redis(一)](http://blog.sina.com.cn/s/blog_48c95a1901016903.html)
* [谈谈Memcached与Redis(二)](http://blog.sina.com.cn/s/blog_48c95a190101693p.html)