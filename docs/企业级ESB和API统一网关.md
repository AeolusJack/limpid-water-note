部分开源和付费ESB的介绍和对比，与阿里云统一网关的适用场景对比
## 1.什么东西
### ESB
前置名词解释：   
soa 网络面向服务架构(Service-Oriented Architecture);服务导向架构;面向服务的架构。  
网络释义：面向服务架构(Service-Oriented Architecture)   
SOA 是通过功能组件化、服务化，来实现系统集成、解决信息孤岛，这是其主要目标。而更进一步则是实现更快响应业务的变化、更快推出新的应用系统。与此同时，SOA 还实现了整合资源，资源复用。      
SOA 服务的设计标准是粗粒度、高重用、灵活、标准。性能则并非首要考虑因素。      
SOA 的两大功能是集成、服务编排(BPEL、BPM)。WF 在 SOA 架构中，实现服务编排的功能。   

ESB 是一个概念,ESB 复杂而模糊，不同产品特性千差万别，ESB 是 SOA 的重要实现手段。ESB 实现 SOA 时，它作为中心、媒介，集成的系统将只与它进行交互。而 ESB 实现与各种系统间的协议转换、数据转换、透明的动态路由功能（基于内容）。   
IBM 总结了 ESB 的功能，较完整的功能如下：  

| **通信** | **服务交互** |
| --- | --- |

- 路由
- 寻址
- 通信技术、协议和标准（例如 IBM® WebSphere® MQ、HTTP 和 HTTPS）
- 发布/订阅
- 响应/请求
- Fire-and-Forget，事件
- 同步和异步消息传递
 
- 服务接口定义（例如，Web 服务描述语言（Web Services Description Language，WSDL））
- 支持替代服务实现
- 通信和集成所需的服务消息传递模型（例如 SOAP 或企业应用程序集成 (EAI) 中间件模型）
- 服务目录和发现
 
| **集成** | **服务质量** |  
| --- | --- |
- 数据库
- 服务聚合
- 遗留系统和应用程序适配器
- EAI 中间件的连接性
- 服务映射
- 协议转换
- 应用程序服务器环境（例如 J2EE 和 .NET）
- 服务调用的语言接口（例如 Java 和 C/C++/C#）
- 事务（原子事务、补偿、Web 服务事务（WS-Transaction））
- 各种确定的传递范例（例如 Web 服务可靠消息传递（WS-ReliableMessaging）或对 EAI 中间件的支持）
 
| **安全性** | **服务级别** |
| --- | --- |
- 身份验证
- 授权
- 不可抵赖性
- 机密性
- 安全标准（例如 Kerberos 和 Web 服务安全性（WS-Security））
- 性能
- 吞吐量
- 可用性
- 其他可以构成契约或协定的持久评估方法  

| **消息处理** | **管理和自治** |  
| --- | --- | 
- 编码的逻辑
- 基于内容的逻辑
- 消息和数据转换
- 有效性
- 中介
- 对象标识映射
- 数据压缩
 
- 服务预置和注册
- 记录、测量和监控
- 发现
- 系统管理和管理工具的集成
- 自监控和自管理
 
| **建模** | **基础架构智能** |
| --- | --- | 
- 对象建模
- 通用业务对象建模
- 数据格式库
- B2B 集成的公共与私有模型
- 开发和部署工具
 
- 业务规则
- 策略驱动的行为，特别是对于服务级别、服务功能的安全和质量（例如 Web 服务策略（WS-Policy））
- 模式识别
 

而最低要求的 ESB 需要具有的功能：

| **通信** | **集成** |
| --- | --- |

- 提供位置透明性的路由和寻址服务
- 控制服务寻址和命名的管理功能
- 至少一种形式的消息传递范型（例如，请求/响应、发布/订阅等等）
- 支持至少一种可以广泛使用的传输协议
 
- 支持服务提供的多种集成方式，比如 Java 2 连接器、Web 服务、异步通信、适配器等等
 
| **服务交互**   |  |
| --- | --- |
- 一个开放且与实现无关的服务消息传递与接口模型，它应该将应用程序代码从路由服务和传输协议中分离出来，并允许替代服务的实现。
 


### 统一网关
（以阿里云对于统一网关的实现为例进行解释）   
阿里云API网关doc：
[https://help.aliyun.com/document_detail/29464.html](https://help.aliyun.com/document_detail/29464.html)  
[SOFAStack API 统一网关](https://help.aliyun.com/product/153275.html)   
阿里云统一网关（Aliyun API Gateway）是阿里云推出的一种高可用、高可扩展、高性能的API管理服务。它提供了API的发布、管理、监控、调用等功能，可以帮助开发者快速搭建和管理API服务。   
阿里云统一网关的主要特点包括：

1. 高性能：支持大规模并发请求，可以满足高并发场景下的API服务需求。
2. 高可用：采用多活部署架构，保证服务可用性和稳定性。
3. 高可扩展：支持动态扩容和自动负载均衡，可以根据业务需求自由扩展API服务。
4. 多协议支持：支持HTTP、HTTPS、WebSocket等多种协议，可以满足不同场景下的API服务需求。
5. 安全防护：内置多种安全防护机制，包括IP黑白名单、签名鉴权、防DDoS等，保障API服务的安全性。
6. 监控报警：提供实时监控和报警功能，可以及时发现和解决API服务的问题。
7. 管理调用：提供API的发布、管理、调用等功能，方便开发者进行API服务的管理和调用。

阿里云统一网关是一种高性能、高可用、高可扩展的API管理服务，可以帮助开发者快速搭建和管理API服务，提高API服务的稳定性和可靠性。   
阿里云统一网关还提供了多种计费方式，包括按调用次数、按带宽流量、按流量阶梯等多种计费方式，方便开发者根据业务需求进行灵活选择和管理。同时，阿里云统一网关还支持多种扩展功能和生态集成，可以与阿里云其他服务和第三方应用进行集成，实现更丰富的功能和应用场景。  
## 2.应用场景
### ESB
适用于内部系统， 多异构系统数据同步等，统一管理   
存在问题： 性能问题    
ESB作为一种集成技术，可以帮助企业实现混合云和云端数据之间的接口打通，提高系统之间的互操作性和可维护性，增强企业的业务竞争力。    
使用ESB存在复杂性、单点故障、性能问题和安全问题等。

1.  服务化架构：ESB是服务化架构的基础，它可以将企业内部的各种应用、系统、数据源等组织成服务，实现系统间的互联互通，从而提高企业的业务效率和系统的可维护性。 
2.  数据集成：ESB可以将多个异构的数据源集成到一起，提供一个统一的数据访问接口，使得企业内部的各种应用和系统可以共享数据，避免了数据的冗余和不一致。 
3.  业务流程管理：ESB可以实现企业内部的各种业务流程的自动化管理，包括流程定义、流程执行、流程监控等，从而提高企业的业务效率和管理水平。 
4.  消息中间件：ESB可以作为消息中间件的一
种实现方式，提供消息传输、消息路由、消息转换等功能，支持多种协议和消息格式，适用于企业内部的异构系统间的消息通信。 
5. 系统集成：ESB可以作为系统集成的基础平台，实现各种系统间的集成，包括企业内部的系统集成、企业与合作伙伴的系统集成等，从而实现业务的扩展和创新。
6. 服务治理：ESB可以提供服务治理的功能，包括服务的注册、发现、监控、安全、负载均衡等，从而保障服务的可靠性和可用性，提高服务的管理水平。
7. 云端集成：ESB可以作为云端集成的一种方式，实现企业内部和云端系统之间的集成，包括云端应用、云端服务、云端数据等，
### 统一网关
丰富的 API 生态，互相借力，协同发展

- 通过 API 网关将企业的核心能力，开放给合作伙伴，达成深度合作，协同发展；
- 将 API 接入阿里云市场，以 API 的形式开放能力、服务、数据供广大开发者采购使用，产生价值；
- 在 API 市场，采购第三方成熟的能力和服务，避免平铺式开发，专注专业，借力发展

安全地实现多端统一，一套服务，多端输出

- 企业只需维护一个服务体系，即可面向多端输出；只需调整API定义，即可实现对APP、设备、web端等多种终端的支持；
- 避免多个场景多套API，大幅降低管理运维成本。

轻松实现系统集成，规范化、标准化

- 通过 API 网关对系统间接口进行规范统一，用标准化的接口实现系统集成；
- 快速完成资源整合和管理，消除快速发展造成的冗余和浪费，聚力发展业务。

在我个人看来，排除费用，技术复杂性两个维度后，两者最大的区别（还有其他突出异同点，但是两者是有功能重叠部分的）是 ：一个适合用于有数据安全要求，并且存在自建机房，对并发能力要求不高的，内部系统之间数据打通时使用（ESB）；一个适合于有对外暴露接口的需求，对并发能力要求高的，提供给其他个人或者第三方企业（云厂商提供的统一网关）。
## 3.达到什么效果
  &nbsp;&nbsp; &nbsp;&nbsp;概念性的效果描述参见应用场景，这里做几个简单的实际描述。   
  &nbsp;&nbsp; &nbsp;&nbsp;比如我们本身有一个内部考核机制，对应的有相应系统数据统计，包括人员管理，人员数据获取。   
  &nbsp;&nbsp; &nbsp;&nbsp;在存在多个系统都需要获取该人员数据来做统计和其他处理时，如果直接调用的话，这个接口其实是无监控，无维护，无管理的状态。   
  &nbsp;&nbsp; &nbsp;&nbsp;在发生改变或者或者追溯到对应人员时，稍显麻烦，会造成较多的沟通成本等，如果是通过ESB的话，我们针对每个接口有对应的管理人员，对于接口的调用可以控制，可以在ESB中看到对应接口功能等，在后面出现其他系统也需要类似的该接口时，可以直接申请接口使用权限后开箱即用。对于一些网络安全要求的，可以链接高低级别，因为是通过ESB调用，这时候服务调用是处于监控中的，所以已避免了直接调用时的一些不安全因素。   
  &nbsp;&nbsp; &nbsp;&nbsp;（会产生一定的使用复杂性）对于已有的接口，可以直观的看到，这时候可以通过统合，生成一些综合接口，以快速落地部分业务诉求。   
   &nbsp;&nbsp; &nbsp;&nbsp;再拿SaaS和混合云来说，混合云需要调用SaaS的接口，如果直接通过连接SaaS的话，像是一些接口统计等的功能，或者其他的一些控制等，我们可能就要单独去实现了，但是如果是通过API统一网关或者ESB去调用的话，这些接口其实是被管理的，这里又存在一个问题，如果是使用API统一网关的话，它是计费的，但是实际我们对于一些接口可能并不是收费的，但是我们又想管理和控制，这时候相对来说其他使用ESB更好一点，但是也存在一些问题，具体怎么去选择就要看怎么去权衡了。   

 &nbsp;&nbsp; &nbsp;&nbsp;对于API统一网关，我们可以通过API统一网关统一对外提供服务,在这里也可控制调用权限等，直接通过配置化来灵活控制API等，对外提供服务的话可以控制流量，费用等，减少二次开发一些功能，像是DDOS攻击等也可通过API统一网关做一层防护。    
 &nbsp;&nbsp; &nbsp;&nbsp;像是API网关的话，我们可以参见一些云服务厂商的API统一网关，可以充分的看到相应效果：   
（当然，我们自己也可以实现统一网关的功能，但是可能并没有必要去做这一件事。）   
亚马逊云   
阿里云：[https://help.aliyun.com/document_detail/29464.html](https://help.aliyun.com/document_detail/29464.html) 
## 4.落地例子
  &nbsp;&nbsp; &nbsp;&nbsp;像是ESB的话在一些制造业、金融业等 传统业务结合互联网的发展过程中，由于存在历史遗留系统，和发展迅猛期，出现了比较多的系统，系统直接数据独立，存在孤岛问题（虽然有数仓，但是数仓的能力 不在这里），如果直接接口调用的话，各种外部接口来回调，不利于管理，不利于统计，也不利于发展。     

&nbsp;&nbsp; &nbsp;&nbsp; API统一网关的话，使用也比较多，比较广泛，像是大多数的互联网产品也都会使用，一些SaaS产品对外提供API服务时也会使用，但是有比较高的数据安全要求的话，往往在选择上，不会倾向于用类似于一些云服务厂商提供的服务，因为存在数据泄漏问题（会将其问题放大）。    
## 5.具体的一些产品，优缺点比较，能力比较
### ESB：
####  付费产品： RestCloud ESB（国内）
  &nbsp;&nbsp; &nbsp;&nbsp;其他（国内）：东方通ESB、普元ESB 还有一大堆基于开源mulesoft esb进行包装的ESB   
  &nbsp;&nbsp; &nbsp;&nbsp; RestCloud **ESB平台**是一个以API为中心的轻量级ESB总线平台。企业级私有化部署，是一个集成的容器，一个集中式的服务总线。  

一、RestCloud ESB平台的组成   
&nbsp;&nbsp; &nbsp;&nbsp; RestCloud ESB平台由API网关和ESB服务编排平台组成，API网关负责API的路由和透传，ESB总线平台则负责以API为中心链接各个业务系统进行数据的推送、拉取、事务控制、异常数据告警等能力。

二、RestCloud ESB平台的功能

- 单一节点失败时跳过，流程结束后补偿失败节点
- 单一节点失败，终止流程执行
- 单一节点失败立即补偿，补偿成功后继续执行后续节点
- 单一节点失败可以调用回滚API，实现数据回滚
- 补偿次数可自定义，补偿间隔时间可自定义

三、RestCloud ESB平台的优势   
基于微服务架构的ESB平台，全Web化，通过拖拉拽进行可视化的统一编排和调度API服务，集中式管理，支持分布式部署运行，可以极大的提升业务API服务的复用率，全面提升前端业务创新能力   
官网：[http://www.restcloud.cn/restcloud/mycms/index.html](http://www.restcloud.cn/restcloud/mycms/index.html)   
RestCloud API管理平台   
![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/a6b43cac705146fbac626cbe7c7a388e~tplv-k3u1fbpfcp-zoom-1.image)
ESB复杂的服务集成与数据推送：  
![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/2387909bf5f64443b3dfaac4aecb57fe~tplv-k3u1fbpfcp-zoom-1.image)
分布式事务支持能力：  
![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/805703989bf54979a975f08bc2b0966f~tplv-k3u1fbpfcp-zoom-1.image) 
####   开源产品： MuleESB（MuleSoft） 、WSO2 ESB（WSO2）、UltraESB、Apache ServiceMix（Apache）、OpenESB（Sun/Oracle）、JBoss ESB（JBoss）   
   

| **名称** | **功能和特点** | **使用的语言** | **复杂性** |
| --- | --- | --- | --- |
| MuleESB | - MuleESB是一个轻量级、高度可扩展的企业服务总线<br>- 支持多种协议和传输<br>- 提供了丰富的连接器和转换器<br>- 支持RESTful和SOAP协议<br>- 采用基于XML的配置和Java编程模型 | Java | 中等 |
| WSO2 ESB | - WSO2 ESB是一个开源的、完全可配置的企业服务总线<br>- 支持多种协议和传输<br>- 提供了丰富的连接器和转换器<br>- 支持RESTful和SOAP协议<br>- 可以在云中或本地部署<br>- 支持多租户 | Java | 高 |
| UltraESB | - UltraESB是一个高性能、轻量级的企业服务总线<br>- 支持多种协议和传输<br>- 提供了丰富的连接器和转换器<br>- 支持RESTful和SOAP协议<br>- 可以在云中或本地部署<br>- 支持多租户 | Java | 中等 |
| Apache ServiceMix | - Apache ServiceMix是一个开源的、基于OSGi的企业服务总线<br>- 支持多种协议和传输<br>- 提供了丰富的连接器和转换器<br>- 支持RESTful和SOAP协议<br>- 可以与其他Apache项目集成 | Java | 高 |
| OpenESB | - OpenESB是一个开源的、基于Java EE的企业服务总线<br>- 支持多种协议和传输<br>- 提供了丰富的连接器和转换器<br>- 支持RESTful和SOAP协议<br>- 可以与其他Java EE应用程序集成 | Java | 高 |
| JBoss ESB | - JBoss ESB是一个开源的、基于Java EE的企业服务总线<br>- 支持多种协议和传输<br>- 提供了丰富的连接器和转换器<br>- 支持RESTful和SOAP协议<br>- 可以与其他Java EE应用程序集成<br>- 集成了规则引擎和工作流引擎 | Java | 高 |

该复杂性是相对的，取决于许多因素，如配置和部署。   
此处的复杂性是基于通用印象和许多用户反馈得出的结论，而不是基于任何具体度量标准。
##### MuleESB
MuleESB官网 
部分资料：   
[https://www.cnblogs.com/enjoyingsoft/p/10132360.html](https://www.cnblogs.com/enjoyingsoft/p/10132360.html)   
[https://blog.csdn.net/Programmer_SKT/article/details/106134565](https://blog.csdn.net/Programmer_SKT/article/details/106134565)        
Mule ESB在github上的托管地址：    
[https://github.com/mulesoft/mule](https://github.com/mulesoft/mule)   
&nbsp;&nbsp; &nbsp;&nbsp; 其实正常来说，我们期望通过swagger或者其他接口json数据导入，或者手动页面交互创建ESB接口，但是Mule社区版，包括其他一些开源的ESB一般都不会满足我们的一些特定要求的，可以通过开发相应插件或者使用一些现成的插件，来集成和组合出适合自己要求的ESB，Github上也有一些开发的Mule插件。   
可以看以下一篇文章：    
[https://zhuanlan.zhihu.com/p/194242793](https://zhuanlan.zhihu.com/p/194242793)   
此处是以ESB架构为核心，SaaS转型过程中，将ESB架构转为微服务架构。   
需要注意的是，ESB本身存在性能问题和中心化问题，这个问题并非不能解决，但是稍显麻烦，所以笔者认为在使用已有ESB技术，不做过多改造的话，适用于企业内部系统之间的接口管理，在前文中也有提及。   
但是也有使用微服务发展过程中，又再去引入ESB的。   
现在也有出现可视化微服务API编排，其实众多ESB已经囊括这一能力。   
基于云ESB的API解决方案：      
##### UltraESB   
  相关资料：[https://developer.adroitlogic.com/ultraesb-legacy/docs/2.6.1/](https://developer.adroitlogic.com/ultraesb-legacy/docs/2.6.1/)   
  未找到在github上的托管地址   

## 6.具有部分ESB（企业服务总线）能力的API统一网关   
####  除了阿里云API网关，其他具有部分ESB能力的API统一网关有（以下是一些常见的）：  

1. MuleSoft Anypoint Platform：它是一个完整的API集成平台，提供了ESB、API管理、数据集成等功能，并支持多种协议和数据格式。
2. Apigee Edge：它是一个全面的API管理平台，支持API的开发、管理和监控，提供了许多安全、性能和分析功能。
3. IBM API Connect：它是一个完整的API管理平台，包括API的设计、开发、测试、部署和管理等环节，支持多种协议和数据格式。
4. AWS API Gateway：它是亚马逊AWS的一项服务，提供了API的创建、部署、管理和监控等功能，并支持多种协议和数据格式。
5. Azure API Management：它是微软Azure的一项服务，提供了API的管理、安全、性能和监控等功能，并支持多种协议和数据格式。

这些API统一网关都具有不同程度的ESB能力，能够协助企业进行API的集成和管理。选择哪种API统一网关取决于企业的具体需求和技术栈。
注意：MuleSoft Anypoint Platform的核心技术是Mule运行时引擎，即Mule esb
####    部分开源API统一网关：

1. Kong：Kong是一个轻量级的、高性能的开源API网关，支持多种协议和数据格式，并提供了一系列安全、性能和分析功能。
2. Tyk：Tyk是一个开源的API管理平台，提供了API的设计、开发、测试、部署和管理等功能，支持多种协议和数据格式。
3. Apiman：Apiman是一个开源的API管理平台，支持API的设计、开发、测试、部署和管理等功能，并提供了一系列安全、性能和分析功能。
4. WSO2 API Manager：WSO2 API Manager是一个开源的API管理平台，提供了API的设计、开发、测试、部署和管理等功能，支持多种协议和数据格式，并提供了一系列安全、性能和分析功能。
5. Ambassador：Ambassador是一个开源的、云原生的API网关，支持多种协议和数据格式，并提供了一系列安全、性能和分析功能。

  
   kong  的GitHub托管地址（**GitHub 34.5k star**）  [https://github.com/Kong/kong](https://github.com/Kong/kong)   
   
    开发语言lua脚本语言占比比较高：  
    
![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/fdb255b423274732825b638999e1c012~tplv-k3u1fbpfcp-zoom-1.image)
   Tyk 的GitHub托管地址（**GitHub 8.3k star**）：[https://github.com/TykTechnologies/tyk](https://github.com/TykTechnologies/tyk)
   
   开发语言go语言占比比较高：    
     
   ![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/ad863e8d1a6b445e9e4bc80f5318ae44~tplv-k3u1fbpfcp-zoom-1.image) 
  apiman的GitHub托管地址（**GitHub 743 star**）： [https://github.com/apiman/apiman](https://github.com/apiman/apiman)   
  
  
   开发语言java占比比较高：   
    
 ![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/06c0d52d261b4ad88882f5fd7ed8b5a7~tplv-k3u1fbpfcp-zoom-1.image)
   WSO2 API Manager 的GitHub托管地址（**GitHub 690 star）**： [https://github.com/wso2/product-apim](https://github.com/wso2/product-apim)
     开发语言java占比比价高：
     ![image.png](https://p3-juejin.byteimg.com/tos-cn-i-k3u1fbpfcp/937f6a616e8d45e18682bae4fe9bee46~tplv-k3u1fbpfcp-zoom-1.image) 
## 7.API统一网关和ESB的部分共同点
随着系统的演进，API统一网关越来越偏向ESB的一些功能。

| **功能** | **API统一网关** | **ESB** |
| --- | --- | --- |
| 集成能力 | 可以集成多个应用程序和服务，提供通用API接口 | 可以集成多个应用程序和服务 |
| 消息路由和转换 | 提供消息路由和转换功能 | 提供消息路由和转换功能 |
| 数据转换和数据格式支持 | 支持多种数据格式和协议，提供数据转换和格式转换功能 | 支持多种数据格式和协议，提供数据转换和格式转换功能 |
| 安全性和认证 | 提供身份验证和授权功能，保护数据和服务不受攻击和恶意行为的影响 | 提供身份验证和授权功能，保护数据和服务不受攻击和恶意行为的影响 |
| 监控和管理 | 提供实时性能指标和错误日志，提供管理控制台和API | 提供实时性能指标和错误日志，提供管理控制台和API |

   &nbsp;&nbsp; &nbsp;&nbsp;API统一网关和ESB在很多方面都具有相似的功能，但是它们的设计目的和重点略有不同。API统一网关更加专注于提供API接口和管理功能，而ESB则更加注重在多个应用程序和服务之间提供数据交换和转换的功能。
其实ESB本身就是一个比较模糊的概念，并不是说有个定性的标志，现在很多的功能和侧重点一些商业ESB软件都已经覆盖到了，从功能上来看比大多数API统一网关都要更全面，而API统一网关也逐渐发展的偏ESB的许多功能。
是否逐渐会互相替换和融合呢？

***本文正在参加[「金石计划」](https://juejin.cn/post/7207698564641996856/ "https://juejin.cn/post/7207698564641996856/")***