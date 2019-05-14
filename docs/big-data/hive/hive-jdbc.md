---
description: 使用JDBC访问Hive
---

# Hive JDBC

## 连接串格式

原生`JDBC`连接串

```text
jdbc:hive2://<host1>:<port1>,<host2>:<port2>/dbName;
```

使用`Zookeeper HA` 连接串

```text
jdbc:hive2://<quorum>/dbName;serviceDiscoveryMode=zooKeeper;zooKeeperNamespace=namespace;
```

## 参数部分

```text
initFile=<file>;sess_var_list?hive_conf_list#hive_var_list
```

