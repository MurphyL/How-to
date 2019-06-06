---
description: Spring IoC 容器是 Spring 框架的核心。它包揽了受管理的应用程序的组件（Spring Bean）的创建，装配，销毁等一些列动作。
---

## Spring Bean 生命周期

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