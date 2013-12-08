# 标题  Openshift vs Cloudfoundry #

# 组名： 成员名称，id #
OpenSource012：	

方超，fc13240

史晓莉，xiaolishi

周文剑，zhouwenjian

王海义，sampsonAmir


## 题目介绍 ##

本题目是比较两个开放的平台即服务(PaaS)。

云服务分为三种形式，分别是基础设施即服务(IaaS)，平台即服务(PaaS)和软件即服务(SaaS)，其实作为“中间层”的PaaS，其也可以说是一种SaaS。一般来讲，我们将其定义为：将软件研发的平台作为一种服务，以SaaS的模式提交给用户。

#####国内外知名PaaS平台######
+ 国外
  * [Microsoft Windows Azure](http://www.windowsazure.com/en-us/)
  * [Google App Engine](https://developers.google.com/appengine/?hl=zh-CN&csw=1)
  * [VMware Cloud Foundry](http://www.cloudfoundry.com/)
  * [Redhat OpenShift](https://www.openshift.com/)
  * [Force.com](http://www.salesforce.com/platform/overview/)
  * [Heroku](https://www.heroku.com/)
  * [Amazon Elastic Beanstalk](http://aws.amazon.com/elasticbeanstalk/)
  * [Engine Yard Cloud](https://www.engineyard.com/products/cloud)
  * [Engine Yard Orchestra]()
  * [CumuLogic](http://www.cumulogic.com/)
  
+ 国内
  * 新浪云  [Sina App Engine（SAE）](http://sae.sina.com.cn/)
  * 百度应用引擎  [Baidu App Enginee（BAE）](http://developer.baidu.com/service)
  * 阿里云  [Aliyun Cloud Enginee（ACE）](http://www.aliyun.com/)
  * 腾讯开放平台  [Q+](http://open.qq.com/reg)
  * Pispower云平台  [Pispower](http://pispower.onecloud.cn)

## 项目介绍 ##

- [OpenShift](https://github.com/fc13240/OpenSource-13-10/blob/master/homework/Introduce%20OpenShift.md)
- [CloudFoundry](https://github.com/fc13240/OpenSource-13-10/blob/master/homework/Introduce%20CloudFoundry.md)


官方网站：

- [OpenShift](https://www.openshift.com/)		
- [CloudFoundry英文版](http://cloudfoundry.com/)  
- [CloudFoundry中文版](http://www.cloudfoundry.cn/) 

百度百科：

- [PaaS](http://baike.baidu.com/view/1413359.htm)
- [OpenShift](http://baike.baidu.com/view/6547620.htm)
- [CloudFoundry](http://baike.baidu.com/view/8193015.htm)

Wiki百科：


- [PaaS](http://zh.wikipedia.org/wiki/PaaS)
- [Openshift](http://zh.wikipedia.org/wiki/Openshift)

## 功能比较 ##

<table width=800 cellpadding=0 cellspacing=0 class="table table-bordered table-striped table-condensed">
   <tr align=center>
      <td>比较项目</td>
      <td>OpenShift</td>
      <td>CloudFoundry</td>
   </tr>
   <tr>
      <td>支持语言</td>
      <td>Java, Java EE, Python, Perl, PHP, Ruby</td>
      <td>Java / Spring, Groovy/Grails, Ruby Rails& Sinatra, Node.js</td>
   </tr>
   <tr>
      <td>支持架构</td>
      <td>Spring、Seam、Weld、CDI、Rails、Rack、Symfony、Zend Framework、Twisted、Django、Java EE框架</td>
      <td>Spring for Java、Ruby on Rails、Node.js以及多种JVM开发框架</td>
   </tr>
   <tr>
      <td>支持数据库</td>
      <td>MySQL，MongoDB,，MemBase，Memcache</td>
      <td>MongoDB, MySQL and Redis</td>
   </tr>
   <tr>
      <td>集中的指示板和控制台</td>
      <td>是</td>
      <td>否</td>
   </tr>
   <tr>
      <td>平台组件</td>
      <td>JBoss Operations Network<br>
     	  Cloud Admin Portal<br>
          Image Toolchain<br>
          Application Engine<br>
          Cloud User Portal<br>
          JBoss Developer Studio开发工具
      </td>
      <td>Router<br>
          DEA(Droplet Execution Agency<br>
          CloudController<br>
          HealthManager<br>
          Services<br>
          NATS(Message bus)
      </td>
   </tr>
   <tr>
      <td>代码托管</td>
      <td>Github</td>
      <td>Github</td>
   </tr>
   <tr>
      <td>许可证</td>
      <td>Apache License 2.0.</td>
      <td>Apache License 2.0</td>
   </tr>
</table>

参考：

[51CTO信息图：OpenShift VS CloudFoundry](https://github.com/SampsonAmir/OpenSource-13-10/blob/master/homework/OpenShiftVSCloudFoundry.jpg)

## 其他比较 ##


###1. 社区 ###

>>#### OpenShift： ####
>>- [Forums](https://www.openshift.com/forums/openshift)
>>- [StackOverflow](http://stackoverflow.com/questions/tagged/openshift)
>>- [IRC](http://webchat.freenode.net/?channels=openshift&uio=d4)
>>- [Feature Requests](https://www.openshift.com/ideas)
>>- [File a bug](https://bugzilla.redhat.com/enter_bug.cgi?product=OpenShift%20Online)
>>- [GitHub](http://openshift.github.io/)

>>#### CloudFoundry： ####

>>- [中文博客](http://cnblog.cloudfoundry.com/)
>>- [google-group](https://groups.google.com/a/cloudfoundry.org/group/vcap-dev)
>>- [Pivotal CF Forums](http://support.cloudfoundry.com/home)
>>- [GitHub](https://github.com/cloudfoundry/cf-release)

###2. 架构比较###
>>- 详见[架构比较](https://github.com/SampsonAmir/OpenSource-13-10/blob/master/homework/Architecture%20about%20OpenShift%20vs%20CloudFoundry%20.md)

## 实际应用 ##

[新浪云平台（SAE）](http://sae.sina.com.cn) 是国内首个公有云计算平台。SAE的Ruby语言运行环境是由Cloud Foundry中国团队和SAE共同运营。该平台支持Ruby 1.8和1.9版本,提供4种编程框架（rail3, Sinatra, rack和standalone共），4种数据服务（MySql, Mongodb, RabbitMQ和Redis）。目前对用户免费公测，每个用户可以具有多达2GB内存和20个应用实例。 


[盛大云引擎](http://www.grandcloud.cn/product/ae) 基于Cloud Foundry开源项目建立的云应用平台，旨在降低应用的部署与运维成本，让应用开发者可以专心于业务的开发设计，不再担心后台的构建与运维。云引擎支持PHP，Ruby，Java，Python等语言编写的应用，后端提供丰富的数据存储服务，并根据应用访问量和业务规模进行弹性扩展。


[莫怕网(MoPaaS.com)](http://www.mopaas.com) 是为广大移动应用开发者和提供商提供便捷的云应用平台服务，为移动互联网应用的开发，部署和运行提供高效、安全和稳定的云计算应用环境。莫怕网完全基于Cloud Foundry开源项目实现，支持Ruby, Java, Node.js, PHP, Python等多种开发语言。


[用友](http://www.ufida.com.cn/) 集团基于Cloud Foundry进行特定的功能扩展，构建出健壮的私有云平台，能够为大中型企业提供具备弹性伸缩的、智能管理的、功能丰富的基础IT架构。用友目前在Cloud Foundry平台上的工作主要集中在企业私有云的服务扩展和传统应用迁移等领域。 

[盛思科技](http://www.seneasy.com/) 是一家专注教育领域的ISV，盛思教育云平台基于Cloud Foundry内核实现，在内核上扩展六大基础服务，即用户管理、单点登录、数据交换、工作流引擎、报表引擎、即时消息，实现对上层教育云应用统一服务支持。在此平台之上，盛思采用Java Spring框架搭建教育类SaaS应用。 

## 参考资料 ##
+ http://88250.b3log.org/openshift-tech-architecture-overview
+ http://baike.baidu.com/link?url=124icjYYLxYPEmba3iJ3KHOkUp84uo9Zw8p5z6gAygs6FvqX_kt9HCrrbxFLvCXASGemKQPCtCS47uWzPnyPUa
+ http://88250.b3log.org/openshift-tech-architecture-overview
+ https://access.redhat.com/site/documentation/en-US/OpenShift/2.0/html/User_Guide/index.html
+ http://openshift.github.io/documentation/oo_system_architecture_guide.html

## 结合自身需要评估后的结论 ##
无

## 组员贡献 ##
方超： 项目介绍

史晓莉： 功能比较

王海义： 其他比较

周文剑： 实际应用


