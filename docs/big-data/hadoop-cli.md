---
description: Hadoop命令行
---

# Hadoop CLI

## 格式化文件系统

```text
$HADOOP_HOME/bin/hadoop namenode -format
```

## 启动/停止`HDFS`/`YARN`服务

```text
# HDFS
$HADOOP_HOME/bin/start-dfs.sh
$HADOOP_HOME/bin/stop-dfs.sh
# YARN
$HADOOP_HOME/bin/start-yarn.sh
$HADOOP_HOME/bin/stop-yarn.sh
```

## 当前正在运行的`Map/Reduce`任务

```text
$HADOOP_HOME/bin/mapred job -list
```

## 报告`Hadoop HDFS`状况

```text
$HADOOP_HOME/bin/hadoop dfsadmin -report
```

