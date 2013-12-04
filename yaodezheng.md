# MySQL vs PostgreSQL#

  组名：OpenSource000  姚德政，yaodezheng

## 项目介绍 ##
  - MySQL 和 PostgreSQL的比较
    + MySQL
        + MySQL原本是一个开放源码的关联式资料库管理系统，原开发者为瑞典的MySQL AB公司，该公司于2008年被升阳微系统（Sun Microsystems）收购。2009年，甲骨文公司（Oracle）收购升阳微系统公司，MySQL成为Oracle旗下产品。
       + MySQL在过去由于性能高、成本低、可靠性好，已经成为最流行的开源数据库，因此被广泛地应用在Internet上的中小型网站中。随着MySQL的不断成熟，它也逐渐用于更多大规模网站和应用，比如维基百科、Google和Facebook等网站。非常流行的开源软件组合LAMP中的“M”指的就是MySQL。
    + PostgreSQL
         + PostgreSQL是自由的对象-关系型数据库服务器（数据库管理系统），在灵活的BSD-风格许可证下发行。它在其他开放源代码数据库系统（比如MySQL和Firebird），和专有系统比如Oracle、Sybase、IBM的DB2和Microsoft SQL Server之外，为用户又提供了一种选择。

## 功能比较 ##

<table border="1">
    <tr>
        <th width="50"><strong>特性</strong></th>
        <th width="350"><strong>MySQL</strong></th>
        <th width="350"><strong>PostgreSQL</strong></th>
    </tr>    
    <tr>
        <td width="50">实例</td>
        <td width="350">通过执行 MySQL 命令（mysqld）启动实例。一个实例可以管理一个或多个数据库。一台服务器可以运行多个 mysqld 实例。一个实例管理器可以监视 mysqld 的各个实例。 </td>
        <td width="350">通过执行 Postmaster 进程（pg_ctl）启动实例。一个实例可以管理一个或多个数据库，这些数据库组成一个集群。集群是磁盘上的一个区域，这个区域在安装时初始化并由一个目录组成，所有数据都存储在这个目录中。使用 initdb 创建第一个数据库。一台机器上可以启动多个实例。</td>
    </tr>
    <tr>
        <td width="50">数据库</td>
        <td width="350">数据库是命名的对象集合，是与实例中的其他数据库分离的实体。一个 MySQL 实例中的所有数据库共享同一个系统编目 。</td>
        <td width="350">数据库是命名的对象集合，每个数据库是与其他数据库分离的实体。每个数据库有自己的系统编目，但是所有数据库共享 pg_databases。</td>
    </tr>
    <tr>
        <td width="50">数据缓冲区</td>
        <td width="350">通过 innodb_buffer_pool_size 配置参数设置数据缓冲区。这个参数是内存缓冲区的字节数，InnoDB 使用这个缓冲区来缓存表的数据和索引。在专用的数据库服务器上，这个参数最高可以设置为机器物理内存量的 80%。 </td>
        <td width="350">Shared_buffers 缓存。在默认情况下分配 64 个缓冲区。默认的块大小是 8K。可以通过设置 postgresql.conf 文件中的 shared_buffers 参数来更新缓冲区缓存。</td>
    </tr>
    <tr>
        <td width="50">数据库连接</td>
        <td width="350">客户机使用 CONNECT 或 USE 语句连接数据库，这时要指定数据库名，还可以指定用户 id 和密码。使用角色管理数据库中的用户和用户组。 </td>
        <td width="350">客户机使用 connect 语句连接数据库，这时要指定数据库名，还可以指定用户 id 和密码。使用角色管理数据库中的用户和用户组。</td>
    </tr>
    <tr>
        <td width="50">身份验证</td>
        <td width="350">MySQL 在数据库级管理身份验证。 基本只支持密码认证。 </td>
        <td width="350">PostgreSQL 支持丰富的认证方法：信任认证、口令认证、Kerberos 认证、基于 Ident 的认证、LDAP 认证、PAM 认证</td>
    </tr>
    <tr>
        <td width="50">加密</td>
        <td width="350">可以在表级指定密码来对数据进行加密。还可以使用 AES_ENCRYPT 和 AES_DECRYPT 函数对列数据进行加密和解密。可以通过 SSL 连接实现网络加密。  </td>
        <td width="350">可以使用 pgcrypto 库中的函数对列进行加密/解密。可以通过 SSL 连接实现网络加密。</td>
    </tr>
    <tr>
        <td width="50">审计 </td>
        <td width="350">可以对 querylog 执行 grep。  </td>
        <td width="350">可以在表上使用 PL/pgSQL 触发器来进行审计。 </td>
    </tr>
    <tr>
        <td width="50">查询解释 </td>
        <td width="350">使用 EXPLAIN 命令查看查询的解释计划。  </td>
        <td width="350">使用 EXPLAIN 命令查看查询的解释计划。  </td>
    </tr>
    <tr>
        <td width="50">备份、恢复和日志</td>
        <td width="350">InnoDB 使用写前（write-ahead）日志记录。支持在线和离线完全备份以及崩溃和事务恢复。需要第三方软件才能支持热备份。  </td>
        <td width="350">在数据目录的一个子目录中维护写前日志。支持在线和离线完全备份以及崩溃、时间点和事务恢复。 可以支持热备份。</td>
    </tr>
    <tr>
        <td width="50">表类型  </td>
        <td width="350">取决于存储引擎。例如，NDB 存储引擎支持分区表，内存引擎支持内存表。   </td>
        <td width="350">支持临时表、常规表以及范围和列表类型的分区表。不支持哈希分区表。 由于PostgreSQL的表分区是通过表继承和规则系统完成了，所以可以实现更复杂的分区方式。</td>
    </tr>
    <tr>
        <td width="50">索引类型  </td>
        <td width="350">取决于存储引擎。MyISAM：BTREE，InnoDB：BTREE。</td>
        <td width="350">支持 B-树、哈希、R-树和 Gist 索引。</td>
    </tr>
    <tr>
        <td width="50">约束   </td>
        <td width="350">支持主键、外键、惟一和非空约束。对检查约束进行解析，但是不强制实施。</td>
        <td width="350">支持主键、外键、惟一、非空和检查约束。</td>
    </tr>
    <tr>
        <td width="50">存储过程和用户定义函数  </td>
        <td width="350">支支持 CREATE PROCEDURE 和 CREATE FUNCTION 语句。存储过程可以用 SQL 和 C++ 编写。用户定义函数可以用 SQL、C 和 C++ 编写。 </td>
        <td width="350">没有单独的存储过程，都是通过函数实现的。用户定义函数可以用 PL/pgSQL（专用的过程语言）、PL/Tcl、PL/Perl、PL/Python 、SQL 和 C 编写。</td>
    </tr>
    <tr>
        <td width="50">触发器  </td>
        <td width="350">支持行前触发器、行后触发器和语句触发器，触发器语句用过程语言复合语句编写。 </td>
        <td width="350">支持行前触发器、行后触发器和语句触发器，触发器过程用 C 编写。</td>
    </tr>
    <tr>
        <td width="50">系统配置文件 </td>
        <td width="350">my.conf </td>
        <td width="350">Postgresql.conf </td>
    </tr>
    <tr>
        <td width="50">数据库配置  </td>
        <td width="350">my.conf </td>
        <td width="350">Postgresql.conf </td>
    </tr>
    <tr>
        <td width="50">客户机连接文件  </td>
        <td width="350">my.conf </td>
        <td width="350">pg_hba.conf </td>
    </tr>
    <tr>
        <td width="50">数据访问和管理服务器  </td>
        <td width="350"><strong>OPTIMIZE TABLE</strong> —— 回收未使用的空间并消除数据文件的碎片
<br><strong>myisamchk -analyze</strong> —— 更新查询优化器所使用的统计数据（MyISAM 存储引擎）
<br><strong>mysql</strong> —— 命令行工具
<br><strong>MySQL Administrator</strong> —— 客户机 GUI 工具 </td>
        <td width="350"><strong>Vacuum</strong> —— 回收未使用的空间
<br><strong>Analyze</strong> —— 更新查询优化器所使用的统计数据
<br><strong>psql</strong> —— 命令行工具
<br><strong>pgAdmin</strong> —— 客户机 GUI 工具 </td>
    </tr>
    <tr>
        <td width="50">并发控制   </td>
        <td width="350">支持表级和行级锁。InnoDB 存储引擎支持 READ_COMMITTED、READ_UNCOMMITTED、REPEATABLE_READ 和 SERIALIZABLE。使用 SET TRANSACTION ISOLATION LEVEL 语句在事务级设置隔离级别。 </td>
        <td width="350">支持表级和行级锁。支持的 ANSI 隔离级别是 Read Committed（默认 —— 能看到查询启动时数据库的快照）和 Serialization（与 Repeatable Read 相似 —— 只能看到在事务启动之前提交的结果）。使用 SET TRANSACTION 语句在事务级设置隔离级别。使用 SET SESSION 在会话级进行设置。 </td>
    </tr>
</table>

    
## 结合自身需要评估后的结论 ##
  - 暂无实际经验。
 
## 参考资料 ##
  - http://bbs.chinaunix.net/thread-1688208-1-1.html
