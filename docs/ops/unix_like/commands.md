---
title: 常用命令
---

## 文件/目录操作

### 创建文件/目录

```shell
    # 文件
    touch new_file
    # 目录
    mkdir new_dir
```

### 删除文件/目录

```shell
    # 文件
    rm target_file       # 删除目标文件
    # 目录
    rmdir target_dir     # 删除目标目录，目录必须为空
    # 文件以及目录
    rm -rf target        # 递归删除target文件，或者target目录下的所有文件以及target目录
```

### 操作文件/目录

### 查看文件/目录内容

```shell
    # 文件
    cat target_file                # 全文查看目标文件内容，参数n可以展示行号
    # 分页
    less target_file               # 分页查看目标文件内容
    more target_file               # 分页查看模板文件内容
    # 指定位置
    head target_file               # 查看文件顶端
    tail target_file               # 查看文件末端，-f可以滚动显示最新追加的内容
    # 目录
    ls                             # 列出当前目录下的所有内容
    ls .                           # 指定路径，列出当前目录下的所有内容
    ls /target_file /target_dir    # 列出target_file，以及target_dir目录下的内容
```

### 编辑文件内容