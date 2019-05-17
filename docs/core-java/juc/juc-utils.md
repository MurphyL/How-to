---
description: Java并发工具类
---

## ExecutorService - 线程池

### 线程池的作用

在程序启动的时候就创建若干线程来响应处理，它们被称为线程池，里面的线程叫工作线程：

1. 降低资源消耗。通过重复利用已创建的线程降低线程创建和销毁造成的消耗；
1. 提高响应速度。当任务到达时，任务可以不需要等到线程创建就能立即执行；
1. 提高线程的可管理性。 

### ThreadPoolExecutor

#### 构造方法参数说明

`corePoolSize`：核心线程数，默认情况下核心线程会一直存活，即使处于闲置状态也不会受存`keepAliveTime`限制。除非将`allowCoreThreadTimeOut`设置为`true`。
 
`maximumPoolSize`：线程池所能容纳的最大线程数。超过这个数的线程将被阻塞。当任务队列为没有设置大小的`LinkedBlockingDeque`时，这个值无效。 

`keepAliveTime`：非核心线程的闲置超时时间，超过这个时间就会被回收。 

`unit`：指定`keepAliveTime`的单位，如`TimeUnit.SECONDS`。当将`allowCoreThreadTimeOut`设置为`true`时对`corePoolSize`生效。 

`workQueue`：线程池中的任务队列（`SynchronousQueue`、`LinkedBlockingDeque`、`ArrayBlockingQueue`）。

`threadFactory`：线程工厂，提供创建新线程的功能。`ThreadFactory`是一个接口，只有一个方法

#### Executor拒绝策略

1. `AbortPolicy`：为`Java`线程池默认的阻塞策略，不执行此任务，而且直接抛出一个运行时异常，切记`ThreadPoolExecutor.execute`需要`try catch`，否则程序会直接退出；
2. `DiscardPolicy`：直接抛弃，任务不执行，空方法；
3. `DiscardOldestPolicy`：从队列里面抛弃`head`的一个任务，并再次`execute`此任务；
4. `CallerRunsPolicy`：在调用`execute`的线程里面执行此`command`，会阻塞入；
5. 用户自定义拒绝策略：实现`RejectedExecutionHandler`，并自己定义策略模式；

```java
// TODO
```

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

```java
// TODO
```

## Exchanger - 交换机

```java
// TODO
```
