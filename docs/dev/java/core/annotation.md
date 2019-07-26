---
description: Java注解，通常配合反射来使用。
---

在程序中的嵌入元数据，可以使用注解解析工具或编译器对其进行解析，也可以指定注解在编译期或运行期有效。这些元数据与程序业务逻辑无关，并且是供指定的工具或框架使用的。

## 元注解

`@Target`指定注解使用的目标范围（类、方法、字段等），其参考值见类的定义`java.lang.annotation.ElementType`；

`@Documented`指定被标注的注解会包含在javadoc中；

`@Retention`指定注解的生命周期（源码、class文件、运行时），其参考值见类的定义：`java.lang.annotation.RetentionPolicy`；

`@Inherited`指定子类可以继承父类的注解，只能是类上的注解，方法和字段的注解不能继承。即如果父类上的注解是`@Inherited`修饰的就能被子类继承；

### `JDK 1.8`新增的元注解

`@Native`指定字段是一个常量，其值引用`native code`；

`@Repeatable`注解上可以使用重复注解，即可以在一个地方可以重复使用同一个注解，像`Spring`中的包扫描注解就使用了这个。

## `Java`内置`Annotation`

JavaSE中内置三个标准Annotation，定义在java.lang中：

- `@Override`是一个标记型`Annotation`，说明了被标注的方法覆盖了父类的方法，起到了断言的作用。如果给一个非覆盖父类方法的方法添加该`Annotation`，编译器将报编译错误。它有两个典型的使用场景，一是在试图覆盖父类方法却写错了方法名时报错，二是删除已被子类覆盖（且用`Annotation`修饰）的父类方法时报错。
- `@Deprecated`标记型`Annotation`，说明被修改的元素已被废弃并不推荐使用，编译器会在该元素上加一条横线以作提示。该修饰具有一定的“传递性”：如果我们通过继承的方式使用了这个弃用的元素，即使继承后的元素（类，成员或者方法）并未被标记为`@Deprecated`，编译器仍然会给出提示。
- `@SuppressWarnnings`用于通知`Java`编译器关闭对特定类、方法、成员变量、变量初始化的警告。此种警告一般代表了可能的程序错误，例如当我们使用一个`generic collection`类而未提供它的类型时，编译器将提示`unchecked warning`的警告。通常当这种情况发生时，我们需要查找引起警告的代码，如果它真的表示错误，我们就需要纠正它。然而，有时我们无法避免这种警告，例如，我们使用必须和非`generic`的旧代码交互的`generic collection`类时，我们无法避免这个`unchecked warning`，此时可以在调用的方法前增加`@SuppressWarnnings`通知编译器关闭对此方法的警告。

## 参考资料

- [Java进阶（一）Annotation（注解）](http://www.jasongj.com/2016/01/17/Java1_%E6%B3%A8%E8%A7%A3Annotation/)