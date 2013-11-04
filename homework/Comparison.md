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
|社区||[ChinaUnix](http://bbs.chinaunix.net/forum-240-1.html)|

参考：

http://bbs.chinaunix.net/thread-1644309-1-1.html
http://os.51cto.com/art/201209/355996.htm
http://os.51cto.com/art/201209/355977.htm
http://os.51cto.com/art/201209/356431.htm
http://quanzhong.iteye.com/blog/947306