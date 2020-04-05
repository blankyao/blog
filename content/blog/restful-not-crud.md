---
title: REST != CRUD
date: "2020-04-05 21:50:00"
description: "当我们在说 RESTful 时我们在说什么？"
---
在做接口设计时大家应该都会经常听到 RESTful 这个东西，随着前后端分离以及开放平台的发展，RESTful 已经普遍到成为了互联网软件开发者的基本常识，然而，在大部分时候，其实大家都没理解到底什么是 RESTful.

REST 是 Roy Thomas Fielding 在他的论文 [Architectural Styles and the Design of Network-based Software Architectures](https://www.ics.uci.edu/~fielding/pubs/dissertation/top.htm) 提到的概念，这篇论文在我大三的时候就看到过，当时好像是 Javaeye 社区的 robbinfan 推荐的，当时还打印了中文版，但是随便浏览了一下就没有再看了，因为觉着没必要花时间看这么简单的东西，然而，当我今年春节重新去看时却感觉看起来很吃力。

相信很多人都没看过这篇经典的论文，或者压根都没听过 [Roy Thomas Fielding](https://roy.gbiv.com/untangled/) 这个人，但是总该听说过 Apache 吧？实在不行的话，HTTP 总该知道吧？Roy Thomas Fielding 是 Apache 的作者，也是 HTTP 规范的制定者之一，为互联网的发展做出了非常巨大的贡献，单纯从这一点来说，这篇论文还是非常值得一读的。

> REST emphasizes scalability of component interactions, generality of interfaces, independent deployment of components, and intermediary components to reduce interaction latency, enforce security, and encapsulate legacy systems. I describe the software engineering principles guiding REST and the interaction constraints chosen to retain those principles, contrasting them to the constraints of other architectural styles. **Finally, I describe the lessons learned from applying REST to the design of the Hypertext Transfer Protocol and Uniform Resource Identifier standards, and from their subsequent deployment in Web client and server software**.

这是论文摘要里面的一段话，从这里就能看出来，我们平时大部分时候所理解的 REST 都是错误的。REST 不是一个接口规范，不是对资源的 CRUD，而是网络应用的一种架构风格。另外，作者提到在论文里描述了将 REST 应用到 HTTP 以及 URI 规范的过程中所吸取的经验，我把这一句话加粗了，是为了强调 REST 的重要性，也是为了强调这篇论文的价值。

作者在论文里介绍了什么是软件架构：
> A software architecture is an abstraction of the run-time elements of a software system during some phase of its operation. A system may be composed of many levels of abstraction and many phases of operation, each with its own software architecture.

架构的组成元素：
> A software architecture is defined by a configuration of architectural elements—components, connectors, and data—constrained in their relationships in order to achieve a desired set of architectural properties.

1. A component is an abstract unit of software instructions and internal state that provides a transformation of data via its interface.
2. A connector is an abstract mechanism that mediates communication, coordination, or cooperation among components.
3. A datum is an element of information that is transferred from a component, or received by a component, via a connector.

结构：
> A configuration is the structure of architectural relationships among components, connectors, and data during a period of system run-time.

属性：
> The set of architectural properties of a software architecture includes all properties that derive from the selection and arrangement of components, connectors, and data within the system. Examples include both the functional properties achieved by the system and nonfunctional properties, such as relative ease of evolution, reusability of components, efficiency, and dynamic extensibility, often referred to as quality attributes.

风格：
> An architectural style is a coordinated set of architectural constraints that restricts the roles/features of architectural elements and the allowed relationships among those elements within any architecture that conforms to that style.

然后介绍了一下什么是 Network-based Application Architectures，以及需要关注的架构属性：
1. Performance
2. Scalability
3. Simplicity
4. Modifiability
5. Visibility
6. Portability
7. Reliability

然后介绍了下设计 Web Architecture 的一些问题和想法，最后，通过以下 6 个基本约束推导出了 REST：
1. Client-Server
2. Stateless
3. Cache
4. Uniform Interface
5. Layered System
6. Code-On-Demand

只要满足这 6 条基本原则，就是符合 REST 风格的架构，这其中的每一条都值得花大精力去研究，等未来有空我也会一条条的深入去探索一下，探索一下技术的发展以及发展过程中的故事。

到了这里，值得再强调一下，REST 不是 CRUD! REST 里面的 R 也不是 resource 的简写，而是 Representational 的简写（其实是 Resource Representational，省略了 Resource）, REST 的全称是 Representational State Transter, 什么意思呢？还是继续看论文：
> The name "Representational State Transfer" is intended to evoke an image of how a well-designed Web application behaves: a network of web pages (a virtual state-machine), where the user progresses through the application by selecting links (state transitions), resulting in the next page (representing the next state of the application) being transferred to the user and rendered for their use.

是不是也可以把整个 WWW 理解为一个状态机呢？

另外，Roy 也有在 blog 里写了一篇文章 [It is okay to use POST](https://roy.gbiv.com/untangled/2009/it-is-okay-to-use-post) 来澄清大家的误解。

> Please, let’s move on. We don’t need to use PUT for every state change in HTTP. REST has never said that we should.

关于这篇文章提到的这个问题，也可以看下 [RFC](https://www.w3.org/Protocols/rfc2616/rfc2616-sec9.html).