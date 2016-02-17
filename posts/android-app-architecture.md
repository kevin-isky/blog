## Android应用架构入坑指南

写了一段时间的Android应用，功能都实现了，但总觉得代码写得乱到一起，没有层次感，所以自己到网上看看有没有啥好的架构可以拿来用。

下面是正文。

---

在知乎上找到了这个问题：

+ [Android 开发有什么好的架构么](https://www.zhihu.com/question/21406685)
 
[豆沙包](https://www.zhihu.com/people/dou-sha-bao-31)同学的回答里有两个好东西：

其一，

+ [Google I/O 2015 Android APP 的源码](https://github.com/google/iosched)

关于这个APP源码使用方法，官方是这么说的：

> We hope the source code for this app is useful for you as a reference or starting point for creating your own apps.

原汁原味的谷歌官方源码可以拿来学习研究，也可以作为自己开发APP时的一个Starting Point。

其二，

+ [The Clean Architecture](https://blog.8thlight.com/uncle-bob/2012/08/13/the-clean-architecture.html)

> By separating the software into layers, and conforming to The Dependency Rule, you will create a system that is intrinsically testable, with all the benefits that implies.

这篇文章介绍了[Uncle Bob](https://en.wikipedia.org/wiki/Robert_Cecil_Martin)的The Clean Architecture，核心思想是利用分层（separating the software into layers）和依赖规则（The Dependency Rule）实现应用架构不依赖于具体的开发框架/UI组件/数据库等各种外部的具体技术实现。

+ Independent of Frameworks
+ Independent of UI
+ Independent of Database
+ Independent of any external agency

该应用架构划分为业务逻辑（Business Rules）、接口适配（Interface Adapters）、框架和组件（Frameworks and Drivers）等部分。

> The concentric circles represent different areas of software. In general, the further in you go, the higher level the software becomes. The outer circles are mechanisms. The inner circles are policies.

**业务逻辑**（Business Rules）分为了两层：

+ [领域](https://en.wikipedia.org/wiki/Domain-driven_design)业务逻辑层（Enterprise Business Rules），封装了业务实体对象（Entities）。
+ 应用业务逻辑层（Application Business Rules），封装并实现了系统用例（Use Cases）。

*Entities*
> Entities encapsulate Enterprise wide business rules.

*Use Cases*
> The software in this layer contains application specific business rules. 

**接口适配**（Interface Adapters）可以理解为中间层，负责业务逻辑与外部框架及组件（如数据库，UI组件等）之间的数据转换和交换工作。

> The software in this layer is a set of adapters that convert data from the format most convenient for the use cases and entities, to the format most convenient for some external agency such as the Database or the Web.

**框架和组件**（Frameworks and Drivers）主要是应用程序开发过程中所涉及到的各类框架和工具，包括数据库、Web开发框架
及UI组件等。

> This layer is where all the details go. 

---

对Android应用架构感兴趣的同学，可以把知乎的这个问题作为一个知识挖掘的Starting Point，根据自己的实际情况进行更深入的研究学习和实践。
