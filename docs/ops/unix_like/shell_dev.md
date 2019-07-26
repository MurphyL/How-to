---
title: Shell编程
---

## 最佳实践

1. `source /etc/profile`：避免执行环境和测试用的执行环境不一致；
2. `set -o errexit`：遇到执行错误即退出；
3. `set -o nounset`：遇到不存在的变量即退出；


## 常用实现

### 脚本后台执行

```shell
    # https://zhuanlan.zhihu.com/p/68488382
    nohup command>/dev/null 2>&1 &
```
