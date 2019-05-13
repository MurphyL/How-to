---
description: 使用JDBC访问Hive
---

# Hive JDBC

## 连接串

原生`JDBC`连接串

```text
jdbc:hive2://<host1>:<port1>,<host2>:<port2>/dbName;initFile=<file>;sess_var_list?hive_conf_list#hive_var_list
```

使用`Zookeeper HA` 连接串

```text
jdbc:hive2://<zookeeper quorum>/;serviceDiscoveryMode=zooKeeper;zooKeeperNamespace=zk_namespace;initFile=<file>;sess_var_list?hive_conf_list#hive_var_list
```

