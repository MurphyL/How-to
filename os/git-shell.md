---
description: 命令行中的Git
---

## 生成一个新的`SSH`密钥

```shell
  ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
```

## 常见错误处理

### 索引文件错误 - `index file corrupt`

#### 错误信息：

```shell
  error: index uses  extension, which we do not understand
  fatal: index file corrupt
```

#### 处理方法：

```shell
  rm .git/index.lock .git/index
  git reset
```