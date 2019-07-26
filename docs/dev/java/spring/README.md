---
description: Spring 大家族
---

## [Spring IoC](spring-ioc.md)

控制反转（Inversion of Control）是面向对象编程中的一种设计原则，可以用来减低计算机代码之间的耦合度。其中最常见的方式叫做依赖注入（Dependency Injection，简称DI），还有一种方式叫“依赖查找”（Dependency Lookup）。通过控制反转，对象在被创建的时候，由一个调控系统内所有对象的外界实体，将其所依赖的对象的引用传递给它。也可以说，依赖被注入到对象中。

## [Spring AOP](spring-aop.md)

面向切面的程序设计（Aspect-orientedPprogramming）是计算机科学中的一种程序设计范型，旨在将横切关注点与业务主体进行进一步分离，以提高程序代码的模块化程度。

AOP思想的实现一般都是基于`代理模式` 。`Spring AOP` 同时支持 `CGLIB`、`ASPECTJ`、JDK动态代理。

## [Spring MVC](spring-mvc.md)

以请求为驱动，基于 `Servlet` 设计的 Web MVC 框架。控制器接收、处理请求，然后通过模型对象、分派器展示请求结果。

- 模型（Model） 用于封装与应用程序的业务逻辑相关的数据以及对数据的处理方法。
- 视图（View）能够实现数据有目的的显示（理论上，这不是必需的）。在 View 中一般没有程序上的逻辑。
- 控制器（Controller）起到不同层面间的组织作用，用于控制应用程序的流程。它处理事件并作出响应。

## [Spring Boot](spring-boot.md)

Spring Boot 提供了一组工具，以便快速构建容易配置的 Spring 应用程序。大多数情况下，只需极少的配置，就可以快速获得一个正常运行的 Spring 应用程序。

## [基于 Java 的配置](spring-java-config.md)

Spring 4 以后，官方推荐我们使用 `Java Config` 来代替 `applicationContext.xml`，声明将Bean交给容器管理。

> Spring Boot 已不再推荐使用 `XML` 配置。
