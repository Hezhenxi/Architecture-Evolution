# 微服务架构演进示例 :see_no_evil:

## Tips 更多关于对系统演进的理解
*构建可靠的大型分布式系统
 [从架构演进、架构甚础、分布式甚石、基础没施、技术方法论五个维度，带你了解如何构建一套可靠的分布式大型软件系统](https://icyfenix.cn/introduction/about-book.html)*


<a name="jxfn-1641521709530"></a><a name="3iwd-1641521710719"></a>**互联网架构演进**

![截图.png](assets/Aspose.Words.e12bb904-5d25-4bad-89a3-02c85268c1fe.001.png)


<a name="vyp5-1616512774539"></a><a name="wjsx-1616512723596"></a><a name="mwpq-1616512724605"></a><a name="cjnj-1641521710719"></a>**1.生产环境和开发环境**

![截图.png](assets/Aspose.Words.e12bb904-5d25-4bad-89a3-02c85268c1fe.002.png)

<a name="8dr4-1616911384470"></a><a name="kqyq-1616911293726"></a><a name="tocc-1641521710719"></a>**2.web1.0和web2.0**

<a name="ktwg-1616911607017"></a>2.1 web1.0时期用户量少，并发量小，单体结构能满足性能需求

<a name="hxbh-1616911647465"></a>2.2 web2.0时期，服务器集群

![截图.png](assets/Aspose.Words.e12bb904-5d25-4bad-89a3-02c85268c1fe.003.png)

<a name="j10o-1616911595909"></a><a name="0lz3-1641521710719"></a><a name="mxki-1641521710719"></a>**2.3.如何解决集群之后出现的问题**

<a name="otck-1616911976443"></a>本质上，某个服务/应用单体性能出现瓶颈之后，套娃使用集群，使用集群需要解决如下共同的问题。

![截图.png](assets/Aspose.Words.e12bb904-5d25-4bad-89a3-02c85268c1fe.004.png)

<a name="wbwa-1616912431057"></a><a name="fq9t-1616912431981"></a><a name="k3kw-1616912431986"></a>也叫中间件

![截图.png](assets/Aspose.Words.e12bb904-5d25-4bad-89a3-02c85268c1fe.005.png)

<a name="syuf-1616912407200"></a><a name="5plt-1641521710719"></a>**3.垂直架构**

<a name="y1pp-1616912779813"></a>水平架构  ---直接复制粘贴

<a name="fu4k-1616912794496"></a>垂直架构 ---先拆分成多分，再复制粘贴

<a name="sgvs-1616912824320"></a>for 单独对某个请求量大的模块进行分配多集群

![截图.png](assets/Aspose.Words.e12bb904-5d25-4bad-89a3-02c85268c1fe.006.png)

![截图.png](assets/Aspose.Words.e12bb904-5d25-4bad-89a3-02c85268c1fe.007.png)

<a name="k1ni-1616912950457"></a><a name="t8n6-1641521710719"></a><a name="f9ck-1616913122693"></a><a name="apmu-1641521710719"></a>**4.分布式架构**

<a name="vzxq-1616915926974"></a>水平架构集群增加服务数量，垂直架构细分模块，分布式架构模块之间需要通讯  RPC协议 Dubbo   HTTP feign

![截图.png](assets/Aspose.Words.e12bb904-5d25-4bad-89a3-02c85268c1fe.008.png)

![截图.png](assets/Aspose.Words.e12bb904-5d25-4bad-89a3-02c85268c1fe.009.png)

<a name="p34w-1616916121950"></a><a name="nrgh-1616915956403"></a><a name="82dq-1616916058474"></a><a name="oyy0-1641521710720"></a>**5.分布式机构下的问题**

<a name="sfjo-1641521710720"></a>**5.1 服务间的异步通讯**

<a name="yzla-1616916385684"></a>非核心业务，异步通讯减少相应系统响应时间

![截图.png](assets/Aspose.Words.e12bb904-5d25-4bad-89a3-02c85268c1fe.010.png)

![截图.png](assets/Aspose.Words.e12bb904-5d25-4bad-89a3-02c85268c1fe.011.png)

<a name="wbnn-1616916434486"></a><a name="rdmn-1641521710720"></a><a name="ekav-1616916462988"></a><a name="xarg-1641521710720"></a>**5.2 服务之间通讯地址的维护**

![截图.png](assets/Aspose.Words.e12bb904-5d25-4bad-89a3-02c85268c1fe.012.png)

<a name="dcjq-1616916830351"></a><a name="liml-1616916586126"></a>Nginx是用户调用服务的负载均衡

<a name="en4n-1616916916965"></a>robbin是服务之间的负载均衡

![截图.png](assets/Aspose.Words.e12bb904-5d25-4bad-89a3-02c85268c1fe.013.png)

<a name="wfrl-1641521710720"></a><a name="felz-1616916859193"></a><a name="yary-1616916835140"></a><a name="1ux3-1641521710720"></a>**5.3服务降级**

![截图.png](assets/Aspose.Words.e12bb904-5d25-4bad-89a3-02c85268c1fe.014.png)

![截图.png](assets/Aspose.Words.e12bb904-5d25-4bad-89a3-02c85268c1fe.015.png)


<a name="m7nc-1616917179893"></a><a name="gxfv-1616916969832"></a><a name="vijk-1616917140741"></a><a name="6nt1-1616917138684"></a><a name="qaq8-1641521710720"></a><a name="zpcw-1616917220564"></a>eruka(注册中心、网关)、ribbin（服务器间负载均衡）、hystrix都是spring cloud中的组件

<a name="zcut-1617562156333"></a>nacos                          feign

<a name="3bdk-1641521710720"></a>**5.4海量数据**

<a name="wnlj-1617562330022"></a>海量数据会导致数据库无法存储全部的内容。

<a name="0b7b-1617562532597"></a>即便数据库可以存储海量的数据，在查询数据时，数据库的响应时及其缓慢的。

<a name="1bnv-1617562569101"></a>在用户高并发的情况下，数据库也时无法承受住的。

<a name="oymp-1617562330442"></a>为了解决上述的问题，可以基于Mycat实现数据库的分库分表。


![截图.png](assets/Aspose.Words.e12bb904-5d25-4bad-89a3-02c85268c1fe.016.png)

<a name="j1ov-1617562573393"></a><a name="fgr2-1641521710720"></a><a name="hyno-1616917681714"></a><a name="tpmv-1641521710720"></a>**6.微服务架构**

![截图.png](assets/Aspose.Words.e12bb904-5d25-4bad-89a3-02c85268c1fe.017.png)

<a name="4cpg-1616917891117"></a><a name="kqot-1616917947341"></a><a name="s5nn-1616917887223"></a>分布式架构下再分布式拆分一下，单个服务只做某件事情，如商品查询

![截图.png](assets/Aspose.Words.e12bb904-5d25-4bad-89a3-02c85268c1fe.018.png)

<a name="6nfk-1616917888162"></a><a name="ze9s-1616917888166"></a><a name="un4x-1641521710720"></a>**6.2 容器化技术**

![截图.png](assets/Aspose.Words.e12bb904-5d25-4bad-89a3-02c85268c1fe.019.png)


<a name="rog3-1616918093460"></a><a name="mzah-1616918006915"></a><a name="7oqt-1616918007066"></a><a name="yoyb-1641521710720"></a>**6.3 分布式架构下的其他问题**

<a name="jcda-1617562597895"></a><a name="4qlj-1617562598026"></a>分布式架构帮助我们解决了很多的问题，但是随之也带来了很多问题:

<a name="f5q6-1617562648274"></a>1.分布式事务:--seata

<a name="nwxa-1617562606465"></a>最传统的操作事务的方式，是通过connection链接对象的方式操作，Spring也提供了声明式事务的操作。

<a name="evio-1617562613890"></a>为了解决事务的问题,后续会使用到RabbitMQ | LCN方式来解决。

<a name="qur8-1617562644609"></a>2，分布式锁:

<a name="npi7-1617562624858"></a>传统的锁方式，synchronized | Lock锁，在分布式环境下，传统的锁是没有效果的。为了解决锁的问题,后续会使用到Redis | Zookeeper来解决。

<a name="8auo-1617562640602"></a>3．分布式任务: --xxxJob,quartz

<a name="llgl-1617562632978"></a>在传统的定时任务下，由于分布式环境的问题，可能会造成任务重复执行，一个比较大的任务，需要可以拆分。

<a name="svlc-1617562661496"></a><a name="0btv-1616918301175"></a>分布式事务失效，同一功能，希望事务1，事务2都成功或者都失败

<a name="lwxy-1616918303074"></a>s

![截图.png](assets/Aspose.Words.e12bb904-5d25-4bad-89a3-02c85268c1fe.020.png)
