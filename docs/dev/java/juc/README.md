---
description: 多线程
---


`volatile` 解决多线程内存不可见问题。对于一写多读，是可以解决变量同步问题，但是如果多写，同样无法解决线程安全问题。如果是 `count++` 操作，使用如下类实现：

```java
AtomicInteger count = new AtomicInteger(); 
count.addAndGet(1); 
```

如果是 JDK8，推荐使用 `LongAdder` 对象，比 `AtomicLong` 性能更好（减少乐观锁的重试次数）。


## 参考文档

1. [JavaGuide - 并发](https://github.com/Snailclimb/JavaGuide#%E5%B9%B6%E5%8F%91)
2. [JavaGuide - 原子类型](https://github.com/Snailclimb/JavaGuide/blob/master/docs/java/Multithread/Atomic.md)