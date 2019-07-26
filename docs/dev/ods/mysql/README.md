```
title: MySQL
```

## 事务隔离机制


### Java 代码设置

```java
con.setAutoCommit(false);
conn.setTransactionIsolation(Connection.TRANSACTION_SERIALIZABLE);
```

### SQL 设置

```sql
SET SESSION TRANSACTION ISOLATION LEVEL READ COMMITTED
```

## `SQL`语句

### 数据的插入

`insert ignore`与`insert into`的区别在于：

1. `insert ignore`会忽略数据库中已经存在的数据，如果数据库没有数据，就插入新的数据，如果有数据的话就跳过这条数据；
2. 这样就可以保留数据库中已经存在数据，达到在间隙中插入数据的目的。

`replace into`跟`insert into`功能类似，不同点在于： 

1. `replace into`首先尝试插入数据到表中，如果发现表中已经有此行数据（根据主键或者唯一索引判断）则先删除此行数据，然后插入新的数据。 
2. 否则，直接插入新数据。

`ON DUPLICATE KEY UPDATE`批量插入数据，自动解决索引冲突。

## 参考文档

1. [MySQL - 大表优化](https://mp.weixin.qq.com/s/BMQC2oJlhLoeBDtveXgHpw)
2. [JavaGuide - MySQL事务隔离](https://github.com/Snailclimb/JavaGuide/blob/master/docs/database/%E4%BA%8B%E5%8A%A1%E9%9A%94%E7%A6%BB%E7%BA%A7%E5%88%AB(%E5%9B%BE%E6%96%87%E8%AF%A6%E8%A7%A3).md)