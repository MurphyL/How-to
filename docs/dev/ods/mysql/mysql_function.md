
## 通过SQL创建function

```sql
DROP FUNCTION IF EXISTS get_path;
DELIMITER //
CREATE FUNCTION get_path (target varchar(50)) 
RETURNS varchar(200) DETERMINISTIC
BEGIN
	-- code全路径
	DECLARE path varchar(200);
	DECLARE i int;
	-- 限制查询层级、避免出现 bug
	SET i = 0;
	SET path = '';
	-- 递归寻找父级ID
	WHILE target is not null AND i < 10 DO

		SET path = concat(target, ',', path);
		SET i = i + 1;
		-- 查询父级编码
		SELECT father_code INTO target
		FROM org 
		WHERE code = target;

	END WHILE;
	-- 移除最后面的逗号
	RETURN TRIM(TRAILING ',' FROM path);

END //

SELECT get_path('0250020197') ;
```

## 通过JDBC创建function

```sql
CREATE FUNCTION emp.get_org_route(target varchar(50)) RETURNS varchar(200) DETERMINISTIC
BEGIN
  DECLARE path varchar(200);
  DECLARE temp varchar(50);
  DECLARE i int;
  SET i = 0;
  SET path = '';
  SET temp = target;
  WHILE target is not null AND i < 10 DO
    SET path = concat(target, ',', path);
    SET i = i + 1;
    SELECT father_code INTO target
    FROM emp.org
    WHERE code = target;
  END WHILE;
  RETURN TRIM(TRAILING ',' FROM path);
END;;
```