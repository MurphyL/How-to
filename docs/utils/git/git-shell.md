---
description: 命令行中的Git
---

# Git CLI

## 生成一个新的`SSH`密钥

```text
  ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

## 常见错误处理

### 索引文件错误 - `index file corrupt`

#### 错误信息：

```text
  error: index uses  extension, which we do not understand
  fatal: index file corrupt
```

#### 处理方法：

```text
  rm .git/index.lock .git/index
  git reset
```

## 参考文档

1. [JavaGuide - Git](https://github.com/Snailclimb/JavaGuide/blob/master/docs/tools/Git.md)