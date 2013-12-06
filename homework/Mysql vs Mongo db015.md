Mysql vs Mongo db015.md
======================

成员：

* 张军
* 张英明(yingming19851028)
* 齐驱(qiqu338183)
* 程飞(dj99fei)

###新一代云门户项目介绍

中国联通云门户是采用最新互联网和云计算技术构建的新一代企业内部门户系统，面向总部和全国范围内所有省分公司和子公司提供服务。在提供原有门户功能的基础上，云门户参考流行的互联网应用特点，引进了丰富的企业社区应用，旨在实现从“以企业和生产为中心”向“以员工和体验为中心”的转变。

云门户致力于提升员的操作效率和使用体验。通过应用中心，员工可以快速定位希望访问的应用入口。可以满足不同员工在工作岗位、操作习惯等方面的差异化要求。
云门户引入了诸如微博、相册、投票等流行的互联网应用，构建中国联通企业社区。在协助工作的同时，为活动组织、领导关怀、员工沟通提供了多种渠道，以实现“七分工作”+“三分生活”的良性互动环境，提升员工的企业归属感。

云门户实现了联通集团、我的公司、我的部门三个层级的新闻公告和信息展示，方便员工快速获取自己所关心的信息。各级别的组织都既可以选择在组织内发布信息，满足内部通知和公告的需要；也可以选择将信息发布到更高层级，实现在更大范围内的宣传和沟通。

云门户支持快速搭建专业线虚拟站点，帮助业务部门对其所负责的专业，实施贯穿总部、省分、地市等各级组织的纵向管理。主管业务部门可以对授权哪些组织和人员访问本虚拟站点进行控制，也可以对虚拟站点提供的应用进行自我管理，包括信息发布、论坛、文档共享、专业通讯录等。



###数据库层功能比较

为了实现以上强大的服务功能，新一代门户采用了mysql和mongodb数据库来提供有力的底层数据支持。两种数据库各有不同的特点，在使用场景上要求事务（银行、金融）或SQL的系统、正规化数据模型的使用关系型数据库mysql，要求缓存性能高、Web操作的使用monggodb数据库。但殊途同归，都是开源软件，都可以完成数据库开发和管理工作，通过以下表可以更详细的看出不同。
<table>
	<tr>
		<td>作用</td>
		<td>Mysql</td>
		<td>MongoDB</td>
	</tr>
	<tr>
		<td>服务器守护进程</td>
		<td>mysqld</td>
		<td>mongod</td>
	</tr>
	<tr>
		<td>客户端工具</td>
		<td>mysql</td>
		<td>mongo</td>
	</tr>
	<tr>
		<td>逻辑备份工具</td>
		<td>mysqldump</td>
		<td>mongodump</td>
	</tr>
	<tr>
		<td>逻辑还原工具</td>
		<td>mysql</td>
		<td>mongorestore</td>
	</tr>
	<tr>
		<td>数据导出工具</td>
		<td>mysqldump</td>
		<td>mongoexport</td>
	</tr>
	<tr>
		<td>数据导入工具 </td>
		<td>source</td>
		<td>mongoimport</td>
	</tr>
	<tr>
		<td>新建用户并授权</td>
		<td>grant all on *.*  to username@'localhost'  identified by 'passwd';</td>
		<td>db.addUser("user","psw") db.auth("user","psw")</td>
	</tr>
	<tr>
		<td>显示库列表</td>
		<td>show databases;</td>
		<td>show dbs</td>
	</tr>
	<tr>
		<td>进去库</td>
		<td>use dbname;</td>
		<td>use dbname</td>
	</tr>
	<tr>
		<td>显示表列表</td>
		<td>show tables;</td>
		<td>show collections</td>
	</tr>
	<tr>
		<td>查询主从状态</td>
		<td>show slave status;</td>
		<td>rs.status</td>
	</tr>
	<tr>
		<td>创建库</td>
		<td>create database name;</td>
		<td>无需单独创建，直接use进去</td>
	</tr>
	<tr>
		<td>创建表</td>
		<td>create table tname(id int);</td>
		<td>无需单独创建，直接插入数据</td>
	</tr>
	<tr>
		<td>删除表</td>
		<td>drop table tname;</td>
		<td>db.tname.drop()</td>
	</tr>
	<tr>
		<td>删除库</td>
		<td>drop database dbname;</td>
		<td>首先进去该库，db.dropDatabase()</td>
	</tr>
	<tr>
		<td>插入记录</td>
		<td>insert into tname(id) value(2);</td>
		<td>db.tname.insert({id:2})</td>
	</tr>
	<tr>
		<td>删除记录</td>
		<td>delete from tname where id=2;</td>
		<td>db.tname.remove({id:2})</td>
	</tr>
	<tr>
		<td>修改/更新记录</td>
		<td>update tname set id=3  where id=2;</td>
		<td>db.tname.update({id:2}, {$set:{id:3}},false,true)</td>
	</tr>
	<tr>
		<td>查询所有记录</td>
		<td>select * from tname;</td>
		<td>db.tname.find()</td>
	</tr>
	<tr>
		<td>查询所有列</td>
		<td>select id from tname;</td>
		<td>db.tname.find({},{id:1})</td>
	</tr>
	<tr>
		<td>条件查询</td>
		<td>select * from tname where id=2;</td>
		<td>db.tname.find({id:2})</td>
	</tr>
	<tr>
		<td>条件查询</td>
		<td>select * from tname where id < 2;</td>
		<td>db.tname.find({id:{$lt:2}})</td>
	</tr>
	<tr>
		<td>条件查询</td>
		<td>select * from tname where id >=2;</td>
		<td>db.tname.find({id:{$gte:2}})</td>
	</tr>
	<tr>
		<td>条件查询</td>
		<td>select * from tname where id=2  and name='steve';</td>
		<td>db.tname.find({id:2, name:'steve'})</td>
	</tr>
	<tr>
		<td>条件查询</td>
		<td>select * from tname where id=2 or name='steve';</td>
		<td>db.tname.find($or:[{id:2}, {name:'steve'}])</td>
	</tr>
	<tr>
		<td>条件查询</td>
		<td>select * from tname limit 1;</td>
		<td>db.tname.findOne()</td>
	</tr>
	<tr>
		<td>模糊查询</td>
		<td>select * from tname where name like "%ste%";</td>
		<td>db.tname.find({name:/ste/})</td>
	</tr>
	<tr>
		<td>模糊查询</td>
		<td>select * from tname where name like "ste%";</td>
		<td>db.tname.find({name:/^ste/})</td>
	</tr>
	<tr>
		<td>获取表记录数</td>
		<td>select count(id) from tname;</td>
		<td>db.tname.count()</td>
	</tr>
	<tr>
		<td>获取有条件 的记录数</td>
		<td>select count(id) from tname where id=2;</td>
		<td>db.tname.find({id:2}).count()</td>
	</tr>
	<tr>
		<td>查询时去掉 重复值</td>
		<td>select distinct(last_name) from tname;</td>
		<td>db.tname.distinct('last_name')</td>
	</tr>
	<tr>
		<td>正排序查询</td>
		<td>select *from tname order by id;</td>
		<td>db.tname.find().sort({id:1})</td>
	</tr>
</table>

可以看出mongodb使用JSON的变种BSON作为内部存储的格式和语法。针对MongoDB的操作都使用JSON风格语法，客户端提交或接收的数据都使用JSON形式来展现。相对于现在使用的SQL99标准来说，是一种新的风格。而且内置GridFS，GridFS是一个出色的分布式文件系统，可以支持海量的数据存储。并且提供基于Range的Auto Sharding机制：一个collection可按照记录的范围，分成若干个段，切分到不同的Shard上。Shards可以和复制结合，配合Replica sets能够实现Sharding+fail-over，不同的Shard之间可以负载均衡。在使用场合下，千万级别的文档对象，近10G的数据，对有索引的ID的查询不会比mysql慢，而对非索引字段的查询，则是全面胜出。 mysql实际无法胜任大数据量下任意字段的查询。写入性能同样很令人满意，同样写入百万级别的数 据，mongodb比其他nosql数据库要快得多，基本10分钟以下可以解决。

当然鱼和熊掌不能兼得mongodb也有自身的限制。 所以事务要求严格的系统（如果银行系统）肯定不能用它。还有mongodb占用空间过大。

关于其原因，在官方的FAQ中，提到有如下几个方面：

1. 空间的预分配：为避免形成过多的硬盘碎片，mongodb每次空间不足时都会申请生成一大块的硬盘空间，而且申请的量从64M、128M、256M那 样的指数递增，直到2G为单个文件的最大体积。随着数据量的增加，你可以在其数据目录里看到这些整块生成容量不断递增的文件。

2. 字段名所占用的空间：为了保持每个记录内的结构信息用于查询，mongodb需要把每个字段的key-value都以BSON的形式存储，如果 value域相对于key域并不大，比如存放数值型的数据，则数据的overhead是最大的。一种减少空间占用的方法是把字段名尽量取短一些，这样占用 空间就小了，但这就要求在易读性与空间占用上作为权衡了。我曾建议作者把字段名作个index，每个字段名用一个字节表示，这样就不用担心字段名取多长 了。但作者的担忧也不无道理，这种索引方式需要每次查询得到结果后把索引值跟原值作一个替换，再发送到客户端，这个替换也是挺耗费时间的。现在的实现算是 拿空间来换取时间吧。

3. 删除记录不释放空间：这很容易理解，为避免记录删除后的数据的大规模挪动，原记录空间不删除，只标记“已删除”即可，以后还可以重复利用。

4. 可以定期运行db.repairDatabase()来整理记录，但这个过程会比较缓慢
同时MongoDB没有如MySQL那样成熟的维护工具，这对于开发和IT运营都是个值得注意的地方。




###云门户成功应用案例

新一代云门户Mysql备份采用全备与增备结合，生产环境中mysql的全备有数据点2处分别以双主双备高可用架构。  该架构由4台主机组成，分为两个master,两个slave, 在同一时刻，Master_1与  Master_2只有一台主机向外提供”write服务”，并且Master_1 与Master_2    双向复制，4台机器可以同时向外提供”read服务”。

![image](https://github.com/dj99fei/OpenSource-13-10/blob/master/homework/images/Mysql_mongo1.png?raw=true)
