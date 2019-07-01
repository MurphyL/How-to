---
description: Intellij IDEA技巧
---


## 有用的设置

### 代码自动编译

首先，设置自动编译：

> File | Settings | Build, Execution, Deployment | Compiler | Build project automatically

其次，设置运行是 编译：

> 双击Shift搜索进入Registry ，找到compiler.automake.allow.when.app.running ，然后勾选上。

## Live Template

### 生成`serialVersionUID`

```java
// Edit variables: groovyScript("new Random().nextLong().abs()")
private static final long serialVersionUID = $serialVersionUID$L;
```
