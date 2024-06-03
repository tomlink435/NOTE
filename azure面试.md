# it基础

1字=2字节bite=16位bit

1kb=1024bites



tcp/ip协议就是网络通讯协议，对通信标准做了规定；包含四层：应用层、传输层、网络层、数据链路层

应用层的主要协议：ftp/smtp；接收传输层的数据，或者按不同的要求将数据传到传输层

传输层：udp。tcp

网络层：icmp，ip,igmp。网络中数据包的传输

数据链路层：arp/rarp 。提供链路管理错误检测



## tcp三次握手

是指建立一个tcp连接时，需要客户端和服务端发送3个报文（同步、同步确认、确认）

客户端将syn置为1，将数据包发送给服务端

服务端收到数据包知道标记位syn为1，知道客户端请求建立连接；服务端将标记位syn和ack置为1，发送给客户端

客户端收到确认后，客户端和服务端建立连接

## http/https

80. ​    443

ssl/tls tcp和网络层之间 加密报文 

HTTPS 协议需要向 CA（证书权威机构）申请数字证书，来保证服务器的身份是可信的。



## **面向对象的三个基本特征是：封装、继承、多态。**

我们知道，封装可以隐藏实现细节，使得代码模块化；继承可以扩展已存在的代码模块（类）；它们的目的都是：代码重用。而多态则是为了实现另一个目的——接口重用！多态的作用，就是为了类在继承和派生的时候，保证使用“家谱”中任一类的实例的某一属性时的正确调用。



## 重写和重载

从字面上看，重写就是 重新写一遍的意思。其实就是在子类中把父类本身有的方法重新写一遍。子类继承了父类原有的方法，但有时子类并不想原封不动的继承父类中的某个方法，所以在方法名，参数列表，返回类型(除过子类中方法的返回值是父类中方法返回值的子类时)都相同的情况下， 对方法体进行修改或重写，这就是重写。但要注意子类函数的访问修饰权限不能少于父类的。

在一个类中，同名的方法如果有不同的参数列表（**参数类型不同、参数个数不同甚至是参数顺序不同**）则视为重载。同时，重载对返回类型没有要求，可以相同也可以不同，但**不能通过返回类型是否相同来判断重载**。



## static：静态的

主要用来修饰类的内部结构，例如：属性、方法、代码块、内部类

修饰属性（静态变量或类变量）：我们创建了类的多个对象，多个对象共享同一个静态变量。当通过某一个对象修改静态变量时，会导致其他对象调用此静态变量时，是修改过了的。

注意:

静态变量随着类的加载而加载，会赋默认值。可以通过"类.静态变量"的方式进行调用
静态变量的加载要早于对象的创建。
由于类只会加载一次，则静态变量在内存中也只会存在一份：存在方法区的静态域中。
修饰方法（静态方法、类方法）：随着类的加载而加载，可以通过"类.静态方法"的方式进行调用。静态方法中，只能调用静态的方法或属性。非静态方法中，既可以调用非静态的方法或属性，也可以调用静态的方法或属性

修饰代码块：当 JVM加载类时，就会执行该代码块,只会被执行一次。

static 方法不能被重写

## final：最终的

可以用来修饰：类、方法、变量
final 标记的变量只能赋一次值(对基本类型来说其值不可变，引用类型其引用不可变，即不能指向其他对象)
final 方法不能被子类重写
final 类不能被继承，没有子类，final 类中的方法默认是 final 的



## 翻转链表实现

迭代：遍历整个链表，更改节点指向，直到每个节点指向反转。



##  REST API

是一种广泛使用的设计风格，用于在网络上的客户端和服务器之间进行通信。REST利用HTTP协议的标准方法来实现数据交换和操作。以下是最常见的REST API方法，每种方法对应于一种典型的CRUD（创建、读取、更新、删除）操作：

### 1. GET

- **用途**：用于检索资源。
- **CRUD 操作**：读取（Read）。
- **特点**：GET请求应该只用于获取数据，不应改变服务器上的状态。

### 2. POST

- **用途**：用于创建新资源。
- **CRUD 操作**：创建（Create）。
- **特点**：POST请求通常用于提交实体到指定资源，通常导致状态变化或副作用。

### 3. PUT

- **用途**：用于更新现有资源或创建新资源。
- **CRUD 操作**：更新（Update）/创建（Create）。
- **特点**：PUT请求用于更新资源的全部内容。如果指定的资源不存在，PUT方法可以创建一个新的资源。

### 4. DELETE

- **用途**：用于删除资源。
- **CRUD 操作**：删除（Delete）。
- **特点**：DELETE请求用于删除指定的资源。

### 5. PATCH

- **用途**：用于对资源进行部分修改。
- **CRUD 操作**：更新（Update）。
- **特点**：与PUT方法不同，PATCH方法用于对资源的部分更新，而不是替换整个资源。

每种方法的使用都遵循HTTP协议的定义，以确保Web服务的标准化和互操作性。在设计RESTful API时，选择适当的HTTP方法来匹配操作的性质是非常重要的，这有助于提高API的可读性和维护性。





## REST API状态码

REST API使用HTTP状态码来表示请求的成功或失败。常见的状态码包括：

- **200 OK** - 请求成功。
- **201 Created** - 资源成功创建。
- **400 Bad Request** - 请求格式错误。
- **401 Unauthorized** - 请求未经授权。客户端
- **403 Forbidden** - 服务器拒绝请求。
- **404 Not Found** - 未找到资源。
- **500 Internal Server Error** - 服务器内部错误。服务端

## TCP握手

TCP（传输控制协议）握手是一种三次握手过程，用于在两个网络设备之间建立一个可靠的连接。它包括三个步骤：

1. **SYN**：客户端发送一个SYN（同步）包到服务器以开始连接。
2. **SYN-ACK**：服务器回应一个SYN-ACK（同步确认）包确认收到。
3. **ACK**：客户端发送ACK（确认）包作为响应，完成连接建立。

## UDP vs TCP

- **TCP（传输控制协议）**：是一种面向连接的、可靠的协议，确保数据完整性和顺序。适用于需要高可靠性的应用，如网页浏览和电子邮件。
- **UDP（用户数据报协议）**：是一种无连接的协议，不保证数据的完整性、顺序或可靠性。适用于对速度要求高但可以容忍一定丢包的应用，如视频流和在线游戏。

## TLS/SSL

TLS（传输层安全）和SSL（安全套接字层）是用于在互联网上提供加密通信和安全身份验证的协议。它们保护数据传输不被窃听或篡改。SSL是早期的加密协议，而TLS是其更新、更安全的版本。

## DNS查找

DNS（域名系统）查询是将域名转换为相应IP地址的过程。DNS查询主要有两种方法：递归查询和迭代查询。下面简要说明这两种查询方法的工作原理：

### 递归查询

在递归查询中，客户端（例如，你的电脑或智能手机上的浏览器）向DNS服务器发送一个查询请求，询问某个特定域名的IP地址。如果这个DNS服务器不直接拥有这个信息，它会代表客户端向其他DNS服务器查询，直到找到答案。一旦找到答案，这个DNS服务器会将查询结果返回给客户端。递归查询的特点是客户端只需要发送一次查询请求，然后等待答案，整个查询负担主要由DNS服务器承担。

### 迭代查询

在迭代查询中，客户端向其本地DNS服务器发送查询请求。如果这个DNS服务器没有缓存所请求的域名的IP地址，它会向客户端提供另一个DNS服务器的地址，让客户端去询问。客户端随后向这个新的DNS服务器发送查询请求。这个过程会一直重复，直到找到域名对应的IP地址。每次服务器只是指引下一个查询的方向，最终找到答案的任务在客户端，这就是迭代查询。

### DNS查询过程简述

1. **客户端发起查询**：当你试图访问一个网站时，你的设备首先会检查本地DNS缓存是否已有该网站域名的IP地址。
2. **查询本地DNS服务器**：如果本地缓存没有，你的设备会向配置的本地DNS服务器（通常是你的互联网服务提供商ISP提供的DNS服务器）发送DNS查询请求。
3. **根DNS服务器查询**：本地DNS服务器会先查询根DNS服务器，根服务器会返回负责该顶级域（如.com、.net）的权威DNS服务器的地址。
4. **权威DNS服务器查询**：本地DNS服务器随后查询权威DNS服务器。如果是递归查询，本地DNS服务器会负责进行所有后续查询；如果是迭代查询，客户端会根据每一步返回的信息自己查询。
5. **返回IP地址**：最终，当查询到域名对应的IP地址后，这个信息会被返回给客户端，客户端随后可以使用这个IP地址与目标服务器建立连接。

## 会话/Cookie

- ### Cookie

  - **存储位置**：Cookie存储在客户端，即用户的浏览器上。
  - **目的**：用于跟踪浏览器会话，存储用户偏好设置或登录状态等小段数据。
  - **生命周期**：Cookie可以设置为在特定时间后过期，或当浏览器关闭时过期。开发者可以设定Cookie的生命周期。
  - **安全性**：由于存储在客户端，敏感数据（如身份验证令牌）需要加密以防止安全漏洞。第三方Cookie（由其他网站创建）可能会引发隐私问题。
  - **大小限制**：Cookie的大小和数量（每个域）都有限制，一般单个Cookie限制为4KB。

  ### Session

  - **存储位置**：Session数据存储在服务器端。
  - **目的**：用于存储跨多个页面请求的用户信息，或者用户的会话数据。这可以包括用户的登录状态、购物车内容等。
  - **生命周期**：Session在一段时间不活动后过期（服务器设置），或者显式地由应用逻辑销毁。
  - **安全性**：由于数据存储在服务器端，相对更安全。用户的敏感信息不会直接暴露在客户端。
  - **大小限制**：理论上，Session可以存储较大量的数据，但过多的Session数据会增加服务器的内存压力。

  ### 二者的交互

  通常，网站利用这两种技术来管理用户的会话。例如，当用户登录网站时，服务器创建一个Session来存储用户的登录状态和相关信息。同时，服务器发送一个包含Session标识符（Session ID）的Cookie到用户的浏览器。在后续的请求中，浏览器会返回这个Cookie，服务器通过Session ID来识别用户和检索Session存储的信息，从而实现无状态HTTP协议下的状态保持功能。

## 进程和线程

- **进程**：是运行在自己独立内存空间内的一个程序或应用实例。 堆和方法区域； 栈、程序计数器
- **线程**：是进程中的一个执行流，可以共享进程资源。线程比进程更轻量级，同一进程内的线程间切换开销小。

## 死锁

死锁是多任务环境中两个或多个进程在执行过程中因争夺资源而造成的一种僵局。在死锁状态下，每个进程都在等待其他进程释放资源，但没有一个进程会主动释放它占有的资源，导致所有相关进程都无法向前推进。死锁是并发编程中需要避免的一种情况，因为它会导致程序部分或全部停止响应。

### 死锁的四个必要条件

死锁发生需要同时满足以下四个条件，这些条件也被称为死锁的四个必要条件：

1. **互斥条件**：至少有一个资源必须处于非共享模式，即一次只有一个进程可以使用。如果其他进程请求该资源，请求进程必须等待直到资源被释放。
2. **占有和等待条件**：一个进程至少持有一个资源，并且正在等待获取额外的资源，这些额外资源被其他进程占有。
3. **不可抢占条件**：资源不能被抢占，也就是说，资源只能由占有它的进程主动释放，不能被其他进程强行夺取。
4. **循环等待条件**：发生死锁时，必须存在一种进程资源的循环等待链，每个进程持有另一进程所需的至少一个资源。

### 如何避免死锁

避免或预防死锁的策略通常是破坏死锁的四个必要条件中的一个或多个：

- **破坏互斥条件**：这通常很难实现，因为某些资源天生就是非共享的（例如打印机）。
- **破坏占有和等待条件**：一种方法是要求所有进程一开始就请求它们需要的所有资源，并且只在所有请求都能同时被满足时才分配资源。这种方法可以减少效率，因为它可能导致资源长时间未被使用。
- **破坏不可抢占条件**：如果一个进程请求的资源被另一个进程占有，则系统可以抢占当前占有资源的进程，将资源分配给请求者。被抢占的进程稍后再恢复执行。
- **破坏循环等待条件**：对所有资源类型进行排序，并要求每个进程按照这种固定的顺序请求资源，这样可以避免循环等待的发生。

### 死锁的处理

在实际应用中，系统设计者可以选择死锁预防、死锁避免或死锁检测与恢复的策略。死锁预防通过破坏死锁的四个必要条件之一来设计系统，从而确保死锁无法发生。死锁避免使用算法（如银行家算法）动态检查资源分配状态，以避免进入不安全状态。死锁检测与恢复则允许死锁发生，但系统会定期检测死锁，并通过某种机制（如资源抢占、进程终止）来恢复。

总的来说，虽然死锁是并发系统中的一个复杂问题，但通过合理的设计和策略，可以有效地避免或处理死锁，保证系统的正常运行。

## 网络模型：OSI和TCP/IP

- **OSI模型**：是一个七层框架，用于理解和设计网络系统的工作流程。
- **TCP/IP模型**：是一种四层通信协议集合，用于互联网的数据传输。它简化自OSI模型，包括应用层、传输层、网络层和网络接口层。

## 云平台三种类型

- **IaaS（基础设施即服务）**：提供虚拟化的计算资源（如虚拟机和存储）作为服务。用户管理操作系统、软件和数据。例子：AWS EC2。
- **PaaS（平台即服务）**：提供编程环境的平台，让开发者可以构建、部署和管理应用程序，而不用管理底层的基础设施。例子：Heroku。
- **SaaS（软件即服务）**：提供通过互联网访问的软件应用，服务提供商管理基础设施和平台。例子：Google Workspace (前Google G Suite)。
- ![image-20240311151307508](/Users/teresa/Library/Application Support/typora-user-images/image-20240311151307508.png)





**I'm truly sorry to hear that your experience has not met your expectations thus far. It's our goal to ensure you feel supported and valued at every step. **If you're open to it,**I would like to hear more about your concerns**, **as your feedback is invaluable for us to improve our service. **However, I completely understand if you prefer to speak with another representative. I'll make the necessary arrangements immediately to connect you with another member of our team who can assist you further. Your satisfaction is our top priority, and we're committed to resolving any issues you may face. Please hold for a moment while I transfer your call. **Thank you for your patience and for giving us the opportunity to make this right. **



Thank you for that information. Let's start by checking the current status of our cloud services to see if there's a reported downtime or performance degradation. **I'll also review the application and infrastructure logs around the time the issue started.** Meanwhile, could you confirm if the problem is global or if it seems to be affecting users in a specific location?



Firstly, **I would like to thank you for taking the time to raise this question with us. **I understand your concern about service performance, especially when it comes to your application and business continuity. Indeed, as one of the world's largest cloud service providers, **AWS has significant advantages in scale and performance. But what I want to emphasize is that the services provided by our company also have their unique value and advantages.**
Customer: Okay, I would like to hear your opinion.
You: From the beginning of our cloud service design, we focused on providing more personalized and flexible solutions. This means that we can adjust and optimize services based on the specific needs of each customer. Moreover, we have invested a significant amount of resources in customer service to ensure quick response and resolution of any issues or challenges faced by our customers.
In terms of performance, we continue to invest in optimizing technology and infrastructure to ensure that our services are both efficient and reliable. We understand that any downtime is unacceptable, so our team is constantly working to minimize these impacts through real-time monitoring and automated recovery processes.
Customer: What about the problems I am currently facing?
You: For the access issue you are currently facing, I have marked it as an urgent matter, and our technical team is making every effort to investigate it. Our goal is to quickly identify the root cause and resolve it. At the same time, we will also conduct a comprehensive service review to prevent such incidents from happening again.
**In addition, as compensation and thank you for your patience, we will provide a certain service discount or additional service time after resolving the issue. **We value the business of every customer, and your satisfaction and success are crucial to us.
Customer: I hope this situation will not happen again.
You: I fully understand, and we will take all necessary measures to prevent this situation from happening again. At the same time, I will ensure to maintain communication with you, update the progress of problem handling and subsequent improvement measures in a timely manner. If you have any questions or need further assistance, please feel free to contact us at any time.



**控制密度：在给定的计算资源上合理；合理分配和运行app数量的策略；目的：防止资源过载，确保每个应用获得所需资源高效运行；提高资源利用率和应用稳定性。方式：应用隔离、自动缩放、应用分组、性能监控**



**scale unit**是服务器集群，实现啊规模经济和共享基础设施的重用。



**前端在Azure App Service架构中是一种七层负载平衡器，充当代理，负责在多个应用程序及其相应的工作实例之间分发传入的HTTP(S)请求**。它是应用程序服务规模单元的关键组成部分，确保用户请求被有效地路由到正确的应用程序实例，从而优化性能和资源利用率。通过使用前端负载平衡器，Azure App Service能够提供高可用性、可扩展性和安全性，同时对客户端透明地处理请求。、



**API控制器**在Azure App Service架构中充当**管理操作的协调者，负责实施对应用程序执行的管理任务**。当App Service的全球**Geo-Master**接收到例如创建新应用程序、配置更改或缩放操作的API调用时，**这些调用被转发到特定的规模单元上的API控制器**。API控制器随后协调这些请求在规模单元内的具体实施，如配置应用程序环境或启动和停止应用程序实例，确保管理操作的顺利执行。



**出版商**在Azure App Service中负责处理**应用程序的内容发布和访问，使开发人员能够通过FTP或其他传输协议上传和更新网站内容**。作为应用程序服务的一部分，出版商角色管理着应用程序代码和资料的存储，确保开发者可以轻松部署和更新他们的应用程序。**此外，出版商还负责应用程序日志文件的访问**，为开发者提供了一种方便的方式来检索和分析应用程序运行时的日志数据，帮助监控应用程序的性能和诊断问题。



**网络工作者**（Web Workers）是Azure App Service架构中的核心组件，负责**托管和运行客户的应用程序**。作为应用服务规模单元的一部分，网络工作者是一组专门配置的Windows服务器，直接执行应用程序代码，处理来自互联网的请求并返回响应。根据所选择的应用服务计划，网络工作者可以是共享的，托管来自多个客户的应用程序，或是专用的，仅运行单个客户的一个或多个应用程序，确保应用程序的性能和稳定性。



**应用插槽**是Azure App Service中提供的一项功能，**允许开发人员拥有除生产环境外的额外部署环境**。每个应用插槽都像是应用服务的一个独立实例，可以用于部署测试、预生产或不同版本的应用程序，而不影响生产环境。这使得开发团队可以在不同的环境中构建、测试和预热应用程序，然后通过简单的“交换”操作，将应用程序从一个插槽无缝迁移到另一个，例如从测试插槽移动到生产插槽，实现零停机部署。



**每个应用程序的缩放**是Azure App Service中的一个特性，**允许开发者为每个独立部署的应用程序定义和控制最大服务器实例数量，**从而实现**精细化的资源管理和负载处理能力。**通过这项功能，开发者可以根据各个应用程序的实际需求和性能目标，单独设置和调整其缩放参数，如CPU使用率和内存需求，确保应用程序在需求增加时自动增加资源，而在低负载时减少资源使用，进而优化成本效率并提高应用性能。



**文件服务器**在Azure App Service架构中扮演了存储和共享应用程序内容的关键角色。它通过挂载Azure存储解决方案，adure storage blog存储块，并将其以网络驱动器的形式公开给Web Workers，从而允许应用程序存储HTML、脚本、图片和代码文件等内容。这种配置使得所有运行在同一规模单元内的应用程序能够访问和共享文件，就如同这些文件存储在本地硬盘上一样，进而简化了文件管理，并支持应用程序的高效运行和扩展。



**公共贵宾（VIP）是指在Azure App Service架构中，所有入站HTTP流量通过一个公共虚拟IP地址访问服务的配置。**这个公共VIP是规模单元的云服务部署所分配的，代表了托管在该规模单元上的所有应用程序的入口点。使用公共VIP，**用户和客户可以通过互联网访问托管在Azure App Service上的应用程序，而无需知道后端服务器的实际IP地址，**从而简化了访问并提高了安全性。



**出境贵宾**则是用于Azure App Service中的应用程序进行**出站网络调用**时所使用的一组特定的**虚拟IP地址**。这些出站VIP**用于从应用程序向外部服务发起请求，例如连接到数据库、API调用或访问外部资源。**出境VIP确保了出站连接的来源可以被外部服务识别和验证，同时也支持在需要时将特定的出站流量源地址列入白名单，以满足安全和合规性要求。每个规模单元最多可以有五个出站VIP，它们共同支持应用程序的所有出站通信需求。



Density control is a strategy for the reasonable allocation and running of a number of applications on given computing resources, aiming to prevent resource overload, ensure each app obtains the necessary resources to run efficiently, while also improving resource utilization and application stability. Through strategies such as application isolation, auto-scaling, application grouping, and performance monitoring, resource utilization can be optimized, enhancing application performance and service reliability.

Public VIP refers to a configuration in the Azure App Service architecture where all inbound HTTP traffic accesses services through a common virtual IP address. This public VIP, assigned to a scale unit's cloud service deployment, represents the entry point for all applications hosted on that scale unit. Using the public VIP, users and customers can access applications hosted on Azure App Service via the internet without needing to know the actual IP address of the backend servers, simplifying access and enhancing security.

Outbound VIPs are a set of specific virtual IP addresses used by applications in Azure App Service for making outbound network calls, such as connecting to databases, making API calls, or accessing external resources. These outbound VIPs ensure that the source of outbound connections can be recognized and validated by external services, and also support whitelisting specific outbound traffic source addresses to meet security and compliance requirements when necessary. Each scale unit can have up to five outbound VIPs, collectively supporting all outbound communication needs of the applications.

The Frontend in the Azure App Service architecture is a layer seven load balancer that acts as a proxy, distributing incoming HTTP(S) requests among multiple applications and their respective worker instances. It is a key component of the application service scale unit, ensuring that user requests are efficiently routed to the correct application instance, thus optimizing performance and resource utilization. By using the Frontend load balancer, Azure App Service can provide high availability, scalability, and security while transparently handling requests for the client.

The API Controller acts as a coordinator of management operations within the Azure App Service architecture, responsible for implementing management tasks performed on applications. When the global Geo-Master of App Service receives API calls such as creating new applications, configuration changes, or scaling operations, these calls are forwarded to the API Controller on a specific scale unit. The API Controller then coordinates the implementation of these requests within the scale unit, such as configuring the application environment or starting and stopping application instances, ensuring the smooth execution of management operations.

The Publisher is responsible for handling the content publishing and access of applications in Azure App Service, enabling developers to upload and update website content via FTP or other transfer protocols. As part of the application service, the Publisher role manages the storage of application code and materials, ensuring developers can easily deploy and update their applications. Additionally, the Publisher is responsible for accessing application log files, providing developers with a convenient way to retrieve and analyze log data from the application runtime, aiding in monitoring application performance and diagnosing issues.

Web Workers are core components in the Azure App Service architecture, responsible for hosting and running customers' applications. As part of the application service scale unit, Web Workers are a group of specially configured Windows servers that directly execute application code, handle requests from the internet, and return responses. Depending on the chosen application service plan, Web Workers can be shared, hosting applications from multiple customers, or dedicated, running only one or more applications from a single customer, ensuring the performance and stability of the applications.

Application Slots are a feature provided in Azure App Service, allowing developers to have additional deployment environments beyond the production environment. Each application slot is like an independent instance of the application service, which can be used for deploying testing, pre-production, or different versions of applications without affecting the production environment. This enables development teams to build, test, and pre-warm applications in different environments, and then seamlessly migrate the application from one slot to another, such as from a testing slot to a production slot, achieving zero downtime deployment.

Per-app scaling is a feature in Azure App Service that allows developers to define and control the maximum number of server instances for each independently deployed application, thus achieving fine-grained resource management and load handling capability. Through this feature, developers can set and adjust the scaling parameters for each application based on actual needs and performance goals, such as CPU utilization and memory requirements, ensuring applications automatically increase resources when demand rises and reduce resource use during low load, thereby optimizing cost efficiency and enhancing application performance.





















