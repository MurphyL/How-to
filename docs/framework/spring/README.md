---
description: Spring 有可能成为所有企业应用程序的一站式服务端点。然而，Spring 是模块化的，允许你挑选和选择适用于你的模块，不必要把剩余部分也引入。
---

## Spring IoC 容器

`Spring IoC` 容器是 Spring 框架的核心。它包揽了受管理的应用程序的组件（Spring Bean）的创建，装配，销毁等一些列动作。

### Spring Bean 生命周期

### InitializingBean、DisposableBean

`InitializingBean` 接口为 bean 提供了定义初始化方法的方式。`InitializingBean` 仅仅包含一个方法`afterPropertiesSet()`。

`DisposableBean` 接口允许在容器销毁 bean 的时候获得一次回调。`DisposableBean` 接口也只规定了一个方法`destroy()`。

要避免使用 `InitializingBean`和 `DisposableBean` 标志接口，因为这样会将代码与Spring耦合在一起。可以分别使用 `Spring` 提供的 `init-method` 和 `destroy-method` 的功能来执行一个bean 定义的初始化和销毁方法。

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