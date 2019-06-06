---
description: Java并发工具类
---

## CountDownLatch - 闭锁

CountDownLatch(闭锁)是一个很有用的工具类，利用它我们可以拦截一个或多个线程使其在某个条件成熟后再执行。它的内部提供了一个计数器，在构造闭锁时必须指定计数器的初始值，且计数器的初始值必须大于0。另外它还提供了一个countDown方法来操作计数器的值，每调用一次countDown方法计数器都会减1，直到计数器的值减为0时就代表条件已成熟，所有因调用await方法而阻塞的线程都会被唤醒。

```java
// TODO
```

## ReentranLock - 重入锁

在Java5.0中增加了一种新的机制：ReentrantLock。ReentrantLock类实现了Lock接口，并提供了与synchronized相同的互斥性和内存可见性，它的底层是通过AQS来实现多线程同步的。与内置锁相比ReentrantLock不仅提供了更丰富的加锁机制，而且在性能上也不逊色于内置锁(在以前的版本中甚至优于内置锁)。

```java
// TODO
```

## CyclicBarrier - 栅栏

栅栏机制可以实现多个线程的同步协调。

```java
// TODO
```

## Semaphore - 信号量

信号量主要有两种用途：

- 保护一个重要(代码)部分防止一次超过 N 个线程进入；
- 在两个线程之间发送信号。

如果你将信号量用于保护一个重要部分，试图进入这一部分的代码通常会首先尝试获得一个许可，然后才能进入重要部分(代码块)，执行完之后，再把许可释放掉。

- `tryAcquire`方法，获得锁；
- `release`方法，释放锁；

```java
// TODO
```

## Exchanger - 交换机

```java
// TODO
```

## CompletionService

## 工具类

[Java进阶（七）正确理解Thread Local的原理与适用场景](http://www.jasongj.com/java/threadlocal/)
