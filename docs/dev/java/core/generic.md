```
title: 泛型设计
```

泛型通配符<? extends T>来接收返回的数据，此写法的泛型集合不能使用 add 方法，而<? super T>不能使用 get 方法，作为接口调用赋值时易出错。

## PECS原则

> Producer Extends Consumer Super

- 频繁往外读取内容的，适合用<? extends T>。
- 经常往里插入的，适合用<? super T>。
