---
description: Spring 有可能成为所有企业应用程序的一站式服务端点。然而，Spring 是模块化的，允许你挑选和选择适用于你的模块，不必要把剩余部分也引入。
---

## Spring IoC 容器

Spring 容器是 Spring 框架的核心。容器将创建对象，把它们连接在一起，配置它们，并管理他们的整个生命周期从创建到销毁。Spring 容器使用依赖注入（DI）来管理组成一个应用程序的组件（Spring Beans）。

IOC 容器具有依赖注入功能的容器，它可以创建对象，IOC 容器负责实例化、定位、配置应用程序中的对象及建立这些对象间的依赖。通常new一个实例，控制权由程序员控制，而"控制反转"是指new实例工作不由程序员来做而是交给Spring容器来做。

### Spring Bean 生命周期

### InitializingBean

InitializingBean 为bean提供了定义初始化方法的方式。InitializingBean是一个接口，它仅仅包含一个方法`afterPropertiesSet()`。

通常情况下不建议bean直接实现InitializingBean，因为没有必要把代码通Spring耦合起来。可以使用Spring提供的init-method的功能来执行一个bean 子定义的初始化方法。

### DisposableBean

DisposableBean接口的bean允许在容器销毁该bean的时候获得一次回调。DisposableBean接口也只规定了一个方法`destroy()`。要避免使用DisposableBean标志接口，因为这样会将代码与Spring耦合在一起，有一个可选的方案是，在bean定义中指定一个普通的析构方法，然后Bean声明时通过指定destroy-method属性来完成。


### BeanFactoryAware、BeanNameAware、BeanClassLoaderAware

实现BeanFactoryAware接口，其中只有一个方法即setFactory(BeanFactory factory)。使用上与BeanNameAware接口无异，只不过BeanFactoryAware注入的是个工厂，

> - `BeanNameAware`注入的是Bean的名字;
> - `BeanClassLoaderAware`注入的是Bean的ClassLoader。

###  BeanPostProcessor

接口定义回调方法，你可以实现该方法来提供自己的实例化逻辑，依赖解析逻辑等。


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