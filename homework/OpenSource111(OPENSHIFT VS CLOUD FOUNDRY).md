#OPENSHIFT VS CLOUD FOUNDRY#
组名：OpenSource111

成员名称：
刘可欣 kexinliu；
康盛 kangsheng；
陈国峰。
## 项目介绍 ##
对比RedHat公司的OPENSHIFT和VMware公司的CLOUD FOUNDRY之间的区别和共同之处。
## 功能比较 ##
**OPENSHIFT**

全球开源解决方案领导者红帽公司近日推出了OpenShift，一个面向开源开发人员开放的平台即服务(PaaS)。
红帽OpenShift通过为开发人员提供在语言、框架和云上的更多的选择，使开发人员可以构建、测试、运行和管理他们的应用，从而重新定义了 PaaS市场。以红帽全面的JBoss专业知识为基础，并支持Java EE 6，从而将PaaS的能力扩展到更丰富和更苛刻的应用。

**CLOUD FOUNDRY**

Cloud Foundry是VMware于2011年4月12日推出的业界第一个开源PaaS云平台，它支持多种框架、语言、运行时环境、云平台及应用服务，使开发人员能够在几秒钟内进行应用程序的部署和扩展，无需担心任何基础架构的问题。

<table>
   <tr>
      <td>平台</td>
      <td>OpenShift</td>
      <td>Cloud Foundry</td>
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
      <td>数据库</td>
      <td>Multiple: MySQL, MongoDB, MemBase,Memcache</td>
      <td>MongoDB, MySQL and Redis</td>
   </tr>
   <tr>
      <td>插件</td>
      <td>无</td>
      <td>无</td>
   </tr>
   <tr>
      <td>集中控制</td>
      <td>是</td>
      <td>否</td>
   </tr>
   <tr>
      <td>平台组件</td>
      <td>JBoss Operations Network Cloud Admin Portal Image Toolchain Application Engine Cloud User Portal JBoss Developer Studio开发工具。</td>
      <td>Router DEA(Droplet Execution Agency) CloudController HealthManager Services NATS(Message bus)</td>
   </tr>
   <tr>
      <td>特点</td>
      <td>1、它提供了各种语言的平台给你选择，包括Ruby, Python, PHP 以及当前热门的 Node.js等等，与此同时还提供一些开发应用框架的一键安装，比如 ROR, WordPress 等等。 2、它是首个支持企业级Java的PaaS平台，支持JEE6与JBoss和其Eclipse集成开发环境以及Maven和Jenkins自动化。可以支持Java EE6的平台即服务产品，在云上为Java提供全面的生命周期支持。 3、OpenShift 基于开源和开放标准构建，应用程序在运行时环境中能够保持可移植性,支持开发者插入自己喜爱的框架。 4、OpenShift依靠Git、Jenkins、Maven等标准开发工具，以及Eclipse等集成开发环境(IDE)，可以简化应用程序开发和维护。</td>
      <td>1、开发者可以保留自己的代码编写习惯，不需要做改变，在任何地方可以运行。满足多云需求，作为平台即服务开源项目，保护开发者不被锁定在任何特定云中。 2、该系统在设计时就已经设计成可自愈的，并且在各层级都可水平扩展，既能在大型数据中心里运行，也能运行在一台桌面电脑中，二者使用相同的代码库。 3、通过将Cloud Foundry源代码融合到GitHub的公共代码库中，与Gerrit集成进行代码审查，与Jenkins集成进行持续整合，新流程将社区代码贡献简单化，提高了代码质量，同时能够更清晰的看到代码变化。 4、对系统进行扩展不会导致正在活动的用户和应用停止服务，系统会为所有应用程序实例考虑负载均衡和高可用方面的事情。</td>
   </tr>
</table>
## 其他比较 ##
<table>
   <tr>
      <td>平台</td>
      <td>OpenShift</td>
      <td>Cloud Foundry</td>
   </tr>
   <tr>
      <td>简述</td>
      <td>OpenShift是由红帽推出的一款面向开源开发人员的开放的平台即服务(PaaS)，OpenShift通过为开发人员提供在语言、框架和云上的更多的选择，使开发人员可以构建、测试、运行和管理他们的应用。</td>
      <td>Cloud Foundry是VMware的一款OpenPaaS，它支持多种框架、语言、云平台及应用服务，是一个分布式系统，为开发者提供了应用和服务的舞台，承担了IaaS相关的通用的工作。</td>
   </tr>
   <tr>
      <td>提供商</td>
      <td>Red Hat</td>
      <td>VMware</td>
   </tr>
   <tr>
      <td>平台类型</td>
      <td>Paas</td>
      <td>Paas</td>
   </tr>
   <tr>
      <td>发布时间</td>
      <td>2011年5月</td>
      <td>2011年4月</td>
   </tr>
   <tr>
      <td>社区</td>
      <td>采用Apache License 2.0许可,使得更多用户、开发者、供应商可以使用它，目的是使其社区成为完全开放、广受人们喜爱的精英管理的社区，使用OpenShift的人数及社区人数在不断增长。</td>
      <td>流水线方式的开源参与，支持几十个重要开发框架和应用服务，以及多种云基础架构部署、漏洞修复、文档及其它贡献。</td>
   </tr>
   <tr>
      <td>模式</td>
      <td>免费的FreeShift。原先的开发者预览版本将进化为 FreeShift，依然免费，最多允许 3 个Gear，提供完整 Java EE6 Full Profile &CDI 支持，但不支持存储空间扩展。收费的MegaShift。付费的MegaShift方案，每月$42起价，允许最多16个Gear，且由RedHat提供技术支持。</td>
      <td>通过cloudfoundry.com，免费提供CloudFoundry软件的普通实例，旨在通过针对一些比较高级的中间件(面向云托管的应用程序)收取许可费来获利，但它不提供任何的服务级别协议。</td>
   </tr>
</table>
## 结合自身需要评估后的结论 ##
1.语言方面：基本相同，都支持java，Pythone,php,perl,ruby等。CF多支持Elang;

2.关系数据库：都支持mysql和PostgreSql;

3.NoSQL:都支持MongoDB，CF多支持Redis，Neo4j，分布式缓存memcacheD;

4.OpenShift、CloudFoundry 在支持IAAS的同时，现在都开始使用LXC的方式.

## 参考资料 ##
1.互联网资源；

2.The Bueaty of Cloud Foundry;

3.Red Hat与VMware官方网站。