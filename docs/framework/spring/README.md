---
description: Spring 有可能成为所有企业应用程序的一站式服务端点。然而，Spring 是模块化的，允许你挑选和选择适用于你的模块，不必要把剩余部分也引入。
---

## Spring IoC 容器

`Spring IoC` 容器是 Spring 框架的核心。它包揽了受管理的应用程序的组件（Spring Bean）的创建，装配，销毁等一些列动作。



## 基于 Java 的配置

### @Configuration 注解

带有 @Configuration 的注解类表示这个类可以使用 Spring IoC 容器作为 bean 定义的来源。

### @Bean 注解

@Bean 注解告诉 Spring，一个带有 @Bean 的注解方法将返回一个对象，该对象应该被注册为在 Spring 应用程序上下文中的 bean。

带有 @Bean 注解的方法名称作为 bean 的 ID，它创建并返回实际的 bean。你的配置类可以声明多个 @Bean。

@Bean 注解支持指定任意的初始化和销毁的回调方法。

### @Import、@ImportResource 注解

`@import` 注解允许从另一个配置类中加载 @Bean 定义。

最简单可行的 @Configuration 类如下所示：

```java
package com.murphyl;

import org.springframework.context.annotation.*;

@Configuration
public class HelloWorldConfig {

   @Bean
   public HelloWorld helloWorld(){
      return new HelloWorld();
   }

}
```

上面的代码将等同于下面的 XML 配置：

```xml
<beans>
   <bean id="helloWorld" class="com.murphyl.HelloWorld" />
</beans>
```

引入其他配置：

```java
package com.murphyl;

import org.springframework.context.annotation.*;

@Import(ConfigTestImport.class)
@Configuration
public class HelloWorldConfig {

   @Bean(initMethod = "init", destroyMethod = "cleanup")
   public HelloWorld helloWorld(){
      return new HelloWorld();
   }

}

public class HelloWorld {
   public void init() {
      // initialization logic
   }
   public void cleanup() {
      // destruction logic
   }
}
```