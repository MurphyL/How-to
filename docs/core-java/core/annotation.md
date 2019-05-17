---
description: Java注解，通常配合反射来使用。
---

## 元注解

`@Target`指定注解使用的目标范围（类、方法、字段等），其参考值见类的定义`java.lang.annotation.ElementType`；

`@Documented`指定被标注的注解会包含在javadoc中；

`@Retention`指定注解的生命周期（源码、class文件、运行时），其参考值见类的定义：`java.lang.annotation.RetentionPolicy`；

`@Inherited`指定子类可以继承父类的注解，只能是类上的注解，方法和字段的注解不能继承。即如果父类上的注解是`@Inherited`修饰的就能被子类继承；

### `JDK 1.8`新增了两个元注解

`@Native`指定字段是一个常量，其值引用`native code`；

`@Repeatable`注解上可以使用重复注解，即可以在一个地方可以重复使用同一个注解，像`Spring`中的包扫描注解就使用了这个。