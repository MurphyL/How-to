---
description: Java枚举
---

{% hint style="info" %}
枚举是类的语法糖；
{% endhint %}

```java
package com.murphyl.demo.core.javap;
public enum SeasonEnum {

    SPRING, SUMMER, AUTUMN, WINTER

}
```

```java
// javap -c SeasonEnum.class
public final class com.murphyl.demo.core.javap.SeasonEnum extends java.lang.Enum<com.murphyl.demo.core.javap.SeasonEnum> {

    public static final com.murphyl.demo.core.javap.SeasonEnum SPRING;

    public static final com.murphyl.demo.core.javap.SeasonEnum SUMMER;

    public static final com.murphyl.demo.core.javap.SeasonEnum AUTUMN;

    public static final com.murphyl.demo.core.javap.SeasonEnum WINTER;

    public static com.murphyl.demo.core.javap.SeasonEnum[] values();

    public static com.murphyl.demo.core.javap.SeasonEnum valueOf(java.lang.String);

    // 初始化
    static {};

}
```

## 剖析枚举

1. Enum类有两个成员变量：name（名字）和ordinal（顺序，从0开始）；
1. Enum类有一个构造函数，它有两个入参，分别为name和ordianl赋值；
1. Enum类重写了toString()方法，返回枚举常量的name值；
1. Enum类重写了equals()方法，直接用等号比较；
1. Enum类不允许克隆，clone()方法直接抛出异常。（保证枚举永远是单例的；
1. Enum类实现了Comparable接口，直接比较枚举常量的ordinal的值；
1. Enum类有一个静态的valueOf()方法，可以根据枚举类型以及name返回对应的枚举常量；
1. Enum类不允许反序列化，为了保证枚举永远是单例的；

## 枚举的特点

1. 枚举不允许继承类。JVM在生成枚举时已经继承了Enum类；
1. 枚举允许实现接口。因为枚举本身就是一个类，类是可以实现多个接口的；
1. 不可以继承枚举。因为JVM在生成枚举类时，将它声明为final；
1. 枚举可以用等号比较。JVM会为每个枚举实例对应生成一个类对象，这个类对象是用public static final修饰的，在static代码块中初始化，是一个单例；
1. 枚举本身就是一种对单例设计模式友好的形式，它是实现单例模式的一种很好的方式；
1. 枚举类型的compareTo()方法比较的是枚举类对象的ordinal的值；
1. 枚举类型的equals()方法比较的是枚举类对象的内存地址，作用与等号等价；