# Eucalyptus VS.OpenStack #

  ������OpenSource011
  ---
	##i.������ gleamy ##
	##ii.���� orangebutter##
	##iii.��С�� BUAA-Louis ##
    ##iv.�Ż��� dubin1003   ##


## ��Ŀ���� ##

- Eucalyptus����

> Eucalyptus Ӣ��ȫ��Elastic Utility Computing Architecture for Linking Your Programs To Useful Systems,��һ�ֿ�Դ�����������ṹ������ͨ�����㼯Ⱥ����վȺʵ�ֵ��Եġ�ʵ�õ��Ƽ��㡣
> ��������������������Ǵ�ѧ Santa Barbara �������ѧѧԺ��һ���о���Ŀ�������Ѿ���ҵ������չ��Ϊ�� Eucalyptus Systems Inc��������Eucalyptus ��Ȼ����Դ��Ŀ����ά���Ϳ�����Eucalyptus Systems ���ڻ��ڿ�Դ�� Eucalyptus ��������Ĳ�Ʒ�������ṩ֧�ַ���

> Eucalyptus�Ƽ�����������һ��ƽ̨�ϣ���Ϊopen source���enterprise�棩���ṩ�˶���Щ��Դ�ĳ���Eucalyptus��Դ���ǹ����ġ��������ṩ��CentOS 5��Debian squeeze��OpenSUSE 11��Fedora 12����������
> Eucalyptusѡ��Xen��KVM��Ϊ���⻯�Ĺ�������Ŀǰ�汾��3.2��Eucalyptus��enterprise���Ѿ���vSphere ESX/ESXi�ṩ��֧�֡�

- OpenStack����

> OpenStack��һ���������Һ��պ���ֺ�Rackspace�����з��ģ���Apache����֤��Ȩ��������һ�����������Ϳ���Դ������Ŀ��

> OpenStack��һ����ƽ̨��������Ŀ��������һ�������������Ŀ�ɼ�����Ҫ���������������һЩ����Ĺ�����
> OpenStack��һ��ּ��Ϊ������˽���ƵĽ���������ṩ�����Ŀ�Դ��Ŀ����������ӵ�г���130����ҵ��1350λ�����ߣ���Щ��������˶���OpenStack��Ϊ������ʩ�����񣨼��IaaS����Դ��ͨ��ǰ�ˡ�OpenStack��Ŀ����Ҫ�����Ǽ��ƵĲ�����̲�Ϊ��������õĿ���չ�ԡ�����ϣ��ͨ���ṩ��Ҫ��ָ����Ϣ�������������OpenStackǰ�������ü������Լ��Ĺ����ƻ�˽���ơ�

> OpenStack ���� Rackspace �� NASA ��ͬ�������Ƽ���ƽ̨�����������̺���ҵ�ڲ�ʵ�������� Amazon EC2 �� S3 ���ƻ����ܹ�����(Infrastructure as a Service, IaaS)��OpenStack ����������Ҫģ�飺Nova �� Swift��ǰ���� NASA ��������������������ҵ�����ģ�飻������ Rackspace�����ķֲ�ʽ�ƴ洢ģ�飬���߿���һ���ã�Ҳ���Էֿ������á�OpenStack �ǿ�Դ��Ŀ�������� Rackspace �� NASA �Ĵ���֧���⣬���滹�а��� Dell��Citrix�� Cisco�� Canonical ��Щ��������˾�Ĺ��׺�֧�֣���չ�ٶȷǳ��졣


## ���ܱȽ� ##
ʹ���ƽ̨ʹ�ø��������������֮һ��Eucalyptus APIȫ���������ѷAPI����ˣ���������ѷAPI�����еĽű���������Ʒ���������ɵ�Ϊ���˽���Ʋ���Eucalyptus֧��������������XEN��KVM��ESXi�����һ���������������ҵ�ư��û��ṩ��

��Ҫ�ص㣺

- ���񣨷���͹���Ȩ�ޣ�

- ���������κι�������

- ��Ⱥ�������

- ���������������ȫ����������롣

Openstack��Ŀ����������Ʒ��Nova ������������ѷ��EC2����Swift ������������ѷS3����Glance��һ��Ϊ����Ӳ�̾����ṩ���֡�ע��ͽ��������API����������SwiftΪ�ɷ��ʵ�����PB��1PB = 100��GB�������ṩ����չ�Ķ���洢��Ŀǰ��Novaȫ��֧��������������KVM��XEN�����ƽ̨����Ѹ�ٵؿ������Һܿ콫�ṩ���㷺�Ĺ��ܡ�

��Ҫ�ص㣺

- �ܹ��������⻯����Ʒ��������Դ

- �ܹ�����������

- ������������

- ��ȫ��

- ��������ķ��ʿ���

- ��Ŀ�����

- ͨ�������������VNC��������������������

�����ܽڵ�Ƚ�

<table>
<tr>
<td>&nbsp;</td>
<td>ǰ��</td>
<td>����ڵ�</td>
<td>��ע</td>
</tr>
<tr>
<td>Eucalyptus</td>
<td>ʹ��ubuntu10.04����Centos5.5����ϵͳ,ͨ��apt-get install����yum install�ķ�ʽֱ�Ӱ�װ�����ư�,����һ������CLC,Walrus,SC,CC��ǰ��.���ݹٷ���վ�ṩ���ĵ����в���,�ǱȽ�����ʵ�ֵġ�</td>
<td>ʹ��ubuntu10.04����Centos5.5����ϵͳ��ͨ��apt-get install����yum install �ķ�ʽֱ�Ӱ�װ�����ư�������һ���ṩNC����ļ���ڵ㡣���ݹٷ���վ�ṩ���ĵ����в������ǱȽ�����ʵ�ֵġ�</td>
<td>Eucalyptus������һ��dhcpd��������ò��õĻ��������һ�����鷳�����⣬����ڵ㣨NC���뼯Ⱥ��������CC��������һ��C��֮������NC��CC��һ���������ע������ʱ������һЩ���⡣</td>
</tr>
<tr>
<td>OpenStack</td>
<td>��ubuntu10.04�����ùٷ���վ�ṩ��nova-install�ű����а�װ��������û����������</td>
<td>��ubuntu10.04�����ùٷ���վ�ṩ��nova-install�ű����а�װ��������û����������</td>
<td>����һ���򵥵�ϵͳ����װ���ñȽϼ򵥡�</td>
</tr>
</table>
�������⻯����֧��
<table>
<tr>
<td>&nbsp;</td>
<td>Xen</td>
<td>KVM</td>
<td>XenServer/XCP</td>
<td>VMWare</td>
<td>LXC</td>
<td>openVZ</td>
</tr>
<tr>
<td>Eucalyptus</td>
<td>Y</td>
<td>Y</td>
<td>&nbsp;</td>
<td>Y</td>
<td>&nbsp;</td>
<td>&nbsp;</td>
</tr>
<tr>
<td>OpenStack</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
<td>Y</td>
<td>&nbsp;</td>
</tr>
</table>

## �����Ƚ� ##


###��ȨЭ�������֤����###


<table class="table table-bordered table-striped table-condensed">
<tr>
<th colspan="2"></th>
<th>��ȨЭ��</th>
<th>���ɹ���</th>
<th>��ҵģʽ</th>
</tr>
<tr>
<td rowspan="2">Eucalyptus</td>
<td>������</td>
<td>GPLv3��ȨЭ��</td>
<td>����Ҫ��װ����</td>
<td>���������ʹ��</td>
</tr>
<tr>
<td>��ҵ��</td>
<td>ʹ���Զ������ҵ��ȨЭ��</td>
<td>��Ҫ���ƿ�����(CLC)�ڵ��ϰ�װ����֤</td>
<td>�����������������շѣ��û����������֤����ض��汾������Ч��</td>
</tr>
<tr>
<td colspan="2">OpenStack</td>
<td>Apache 2.0 ��ȨЭ��</td>
<td>����Ҫ����֤</td>
<td>���ʹ��</td>
</tr>
</table>


###��Ŀ��ʷ����Ӫ�Ŷӡ�������ģ###


<table>
<tr>
<th></th>
<th>��Ŀ��ʷ����Ӫ�Ŷ�</th>
<th>������ģ�ͻ�Ծ�̶�</th>
<th>��ͨ����</th>
</tr>
<tr>
<td>Eucalyptus</td>
<td>�����UCSB��HPC�о���Ŀ��2009���������˾��֧����Ŀ����ҵ����Ӫ������CEO��������MySQL CEO��Marten Mickos,���ι��̲���SVP��Tim Cramerc������Sun��˾NetBeans��OpenSolaris��Ŀ��ִ���ܼࡣ���������ŶӶԿ���Դ������Ŀ�Ĺ�������Ӫ������зḻ�ľ��顣</td>
<td>��ͬ�࿪��Դ������Ŀ���У�Encalyptus��������ģ��󣬻�Ծ�̶�Ҳ��ߡ���Ҫԭ���Ǹ���Ŀ��Դ�ڴ�ѧ�о���Ŀ����Ҫԭ���ǹ����ŶӶԿ���Դ��������ĸ߶���ͬ��Ubuntu 10.04��������ѡ��Encalyptus��ΪUEC�Ļ������ܣ����Ĵٽ���Encalyptus.</td>
<td>������������̳�ϵ�����ͨ����48Сʱ�ڵõ���Ӧ��ͨ������֧�ֵ����ʼ����������ͨ����24Сʱ�ڵõ���Ӧ��Encalyptus�ڱ������������а��´������й��й���ʦ�ṩ֧���Ŷӡ�</td>
</tr>
<tr>
<td>OpenStack</td>
<td>OpenStack�Ƿ������йܹ�˾RackSpace��NASA��ͬ����Ŀ���Դ������Ŀ���ڿ���Դ������Ŀ�Ĺ�������Ӫ���棬RackSpace��NASA��Ȼȱ���㹻�ľ��顣���OpenStack��Ŀ������������(1)RackSpace����Ŀ�й���ǿ�ҵĿ�������(2)OpenStack��Ŀ����������������Ա��˵�������ǲ�͸���ģ�(3)OpenStack��Ŀ��ͬ�࿪��Դ������Ŀ�Ĺ����Թ�ǿ��</td>
<td>������ģ��С����Ҫ������֧��/�������Ŀ�Ĺ�˾��Ա���м����������ʼ��б���������С�����ڸ���Ŀ�Ƚ��£��������Ͽ��Բο��İ�װ�����÷�������²��ࡣUbuntu11.04��������ͬʱ֧��Encalyptus��OpenStack��ΪUEC�Ļ������ܣ���������OpenStack���ƹ㡣</td>
<td>ͨ���ʼ��б����м�������Ĺ�ͨ��ͨ����48Сʱ�ڵõ���Ӧ����������ʼ���ͨ����Ӧ��Ϊ������</td>
</tr>
</table>


###�ܹ��Ƚ�###


- Eucalyptus�ܹ�

> Eucalyptus��һ����Amazon EC2���ݵ�IaaSϵͳ��Eucalyptus�����ƿ�����(CLC)��Walrus����Ⱥ������(CC)���洢������(SC)�ͽڵ������(NC)��CLC������Eucalyptuϵͳ�ĺ��ģ�����߲�ε���Դ���ȣ�������CC���������Դ��Walrus�� һ����Amazon S3���ƵĴ洢������Ҫ���ڴ洢�����ӳ����û����ݡ�CC��һ����Ⱥ��ǰ�ˣ�����Э��һ����Ⱥ�ڵļ�����Դ�����ҹ�����Ⱥ�ڵ�����������SC��һ����Amazon EBS���ƵĴ洢���豸���񣬿��������洢ҵ�����ݡ�NC�����յļ���ڵ㣬ͨ�����ò���ϵͳ������⻯�����������͹ر����������ͬһ����Ⱥ(CC)�ڵ����м���ڵ�(NC)������ͬһ�������ڡ� ��һ����Ⱥ(CC)��ͨ����Ҫ����һ̨�洢������(SC)��Ϊ�ü�Ⱥ�ڵļ���ڵ��ṩ���ݴ洢����

> Eucalyptusͨ��Agent�ķ�ʽ������������Դ����ÿһ������ڵ��ϣ�����Ҫ����һ��eucalyptus-nc�ķ��񡣸÷����ڼ�Ⱥ������(CC)��ע����ƿ�����(CLC)����ͨ����Ⱥ������(CLC)����Ҫ���е������ӳ���ļ�(EMI)�������ü���ڵ������С�

> Eucalyptus�������ӳ���ļ��洢��Walrus�ϡ����û�����һ�������ʵ����ʱ��Eucalyptus���Ƚ���Ӧ�������ӳ��(EMI)��Walrus��������Ҫ���и�ʵ���ļ���ڵ�(NC)�ϡ����û��ر�(�������������������)һ�������ʵ����ʱ�򣬶�������������޸Ĳ����ᱻд�ص�Walrus��ԭ���������ӳ��(EMI)�ϣ����жԸ���������޸Ķ��ᶪʧ������û���Ҫ�����޸Ĺ��������������Ҫ���ù���(euca2ools)���������ʵ������Ϊ�µ������ӳ��(EMI)������û���Ҫ�������ݣ�����Ҫ���ô洢������(SC)���ṩ�ĵ��Կ��豸����ɡ�

- OpenStack�ܹ�

> OpenStack��һ����Amazon EC2���ݵ�IaaSϵͳ��OpenStack����OpenStack Compute��OpenStack Object Storage�������֡�

> OpenStack Compute�ְ���Webǰ�ˡ�������񡢴洢����������֤���񡢴洢���豸(��)�����������������ȵȶ��ģ�顣OpenStack Compute�Ĳ�ͬģ��֮�䲻�����κ���Ϣ��ͨ����Ϣ���ݽ���ͨѶ����ˣ���ͬ��ģ����������ڲ�ͬ�ķ������ϣ�Ҳ����������ͬһ̨�������ϡ�

> OpenStack Object Store��������ͨ�÷����������չ�ĺ������ݲֿ⣬����ͨ����������֤���ݵİ�ȫ�ԡ�ͬһ�����ݵ��ڶ�̨�������϶��и����������ֹ��ϵķ������Ӽ�Ⱥ�г�������Ӱ�����ݵ������ԣ������µķ�������ϵͳ���Զ������µķ�������Ϊ��Ӧ���ļ������µĸ������ӹ����Ͻ���OpenStack Object Storeͬʱ�߱�Eucalyptus�е�Walrus����͵��Կ��豸(SC)���񡣲���OpenStack Object Store����һ���ļ�ϵͳ�����ܹ���֤���ݵ�ʵʱ�ԡ���������������ǣ�OpenStack Object Store���ʺ����ڴ洢��Ҫ���ڱ���ľ�̬���ݣ��������ϵͳӳ���ļ��Ͷ�ý�����ݡ�

> OpenStackͨ��Agent�ķ�ʽ������������Դ����ÿһ������ڵ��ϣ�����Ҫ����nova-network�����nova-compute������Щ��������֮�󣬾Ϳ���ͨ����Ϣ���������ƿ��������н�����


###�ɹ�Ӧ�öԱ�###
 
>�������߹��ܱȽ��еĸ������ԣ���������ҵ�ڶ��в�ͬ�ĳɹ�Ӧ����ҵ��


- Eucalyptus��Ӧ��

>Eucalyptus Ӧ�ò���ǳ��㷺��˽�л�����ʩ������������ƽ̨�����и߿�����Iaas�����ع�������������ʽ���칹�����������������ɿ���SAN���ɣ���������ͳ�ƺ����������ص㣬����ҵ˽���Ʒ���Ҳ�кܺõ�Ӧ��

> �ɹ�Ӧ����ҵ������ѷ�����ᣬPuma�����ƿƼ�
 
- OpenStack��Ӧ��
 
>OpenStack ��һ����ƽ̨�������������Թ��������ơ�˽���ƺͻ���Ƽܹ�����OpenStack���������ص㣺

>-	1.�ӽ��û�����ȫʵ�ֶ��ƻ��� 

>-	2.���⳧�������� 

>-	3.ʹ�û������̬������

>���,Խ��Խ�����ҵ��ʼת��ʹ��OpenStack��

> �ɹ�Ӧ����ҵ�������Ұ�ȫ�֣���˼��PayPal,����˹�أ����ˣ���Ϊ�洢����ʤ��ɣ����ƣ����գ�


## ���������Ҫ������Ľ��� ##

Eucalyptus�ļܹ������������ɣ���AWS���ƣ���װ�Ѷ�Ϊ�е�ˮƽ����GUI�����������ޣ���Ҫ����������Ӧ�����еİ��������⣬Eucalyptus����һ����Կ������ȫģʽ���ڸ�ģʽ�У�����ܹ������Ҫ�˴�ע�ᡣEucalyptus������ȸ��á����⣬ͨ��CLC��Eucalyptus����֧�ּ�Ⱥ�ļ�Ⱥ�����ԣ�Eucalyptus����չ�Ը�ǿ������������ҵ����չ����Ҫ��

Openstack��Ŀ��չ�Ͽ죬Ҳ�õ��˽϶��ĳ���֧�֡���openstack��ģ��ṹ�����Ƭ������װ�ѶȽϸߣ�ά���ż��ϸߣ������ڵ�ǰ��ά��Աʹ�á�

��ˣ��ۺ�������Eucalyptus��һ�������ļ��������������OpenStack�����ױ��û������ܡ���ˣ�Eucalyptus���ʺ���Ϊ��ǰһ��ʱ���ڵĻ����ƽ̨��
## ��Ա���� ##

������ ���ס������Ƚϡ�����

���� ���ס���Ŀ���ܣ����ܱȽϣ����ۡ�����

��С�� ����"�ܹ��Ƚ�" ����

�Ż��� ���ס��ɹ�Ӧ�ñȽϡ�����## 

�ο����� ##

CloudStack��OpenStack���Ĵ���ƽ̨���� http://www.chinacloud.cn/show.aspx?id=12339&cid=16 

���������blog http://www.qyjohn.net/