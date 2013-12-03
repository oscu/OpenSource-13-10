
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