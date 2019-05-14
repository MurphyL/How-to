---
description: Hive Query Language
---


## 导入数据到`Hive`

```sql
-- 导入本地数据
LOAD DATA LOCAL INPATH '/home/csv_file.csv' OVERWRITE INTO TABLE csv_test_table;
-- 导入HDFS数据
LOAD DATA INPATH '/test/dc_web' OVERWRITE INTO TABLE dp_daily;
```

## 分区操作
```sql
-- 列出所有分区
SHOW PARTITIONS table_name;
-- 删除分区
ALTER TABLE test_table DROP IF EXISTS PARTITION(dt = 20171225);
```

## 行转列

```sql
SELECT explode(split('北京,天津,河北,山西,内蒙古,辽宁,吉林,黑龙江,上海,江苏,浙江,安徽,福建,江西,山东,河南,湖北,湖南,广东,广西,海南,重庆,四川,贵州,云南,西藏,陕西,甘肃,青海,宁夏,新疆,香港,澳门,台湾', ','))
```

## 分组取`TopN`

```sql
SELECT *
  FROM (SELECT label,
               row_number () OVER (PARTITION BY label ORDER BY num DESC) rn,
               num
          FROM test.group_top_n) a
 WHERE a.rn <= 3
```


