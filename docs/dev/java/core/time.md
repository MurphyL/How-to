```
title: Java核心
```

在 JDK8 中，针对统计时间等场景，推荐使用 Instant 类。

## 获取时间戳

获取当前毫秒数 System.currentTimeMillis()；而不是 new Date().getTime()；

如果想获取更加精确的纳秒级时间值，使用 System.nanoTime()的方式。


