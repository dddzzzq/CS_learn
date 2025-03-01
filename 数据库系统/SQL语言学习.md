# SQL基础语言学习

***基础知识：一个数据库通常包括一个表或多个表，每个表由一个名字标识，表包含带有数据的记录（行）。***

## 1. CREATE TABLE-创建表

### 1.1 语法

```sql
CREATE TABLE 表名称 
(
列名称1 数据类型，
列名称2 数据类型，
....
);
```

### 1.2 常见数据类型

| 数据类型                                             | 描述                                                         |
| ---------------------------------------------------- | ------------------------------------------------------------ |
| integer(size),int(size),smallint(size),tinyint(size) | 仅容纳整数，size为规定数字的最大位数                         |
| decimal(szie, d),numeric(size, d)                    | 容纳带有小数的数字，‘size‘为数字的最大位数，'d'表示小数点右侧的最大位数 |
| char(size)                                           | 容纳固定长度字符串，size为字符串长度                         |
| varchar(size)                                        | 容纳可变长度字符串，size表示字符串最大长度                   |
| date(yyyymmdd)                                       | 容纳日期                                                     |

### 1.3 实例

![image-20241014195158425](C:\Users\dgzsz\AppData\Roaming\Typora\typora-user-images\image-20241014195158425.png)

创建上图的表

#### 1.3.1 创建表

```sql
CREATE TABLE PERSONS
(
Id int,
LastName varchar(10),
FirstName varchar(10),
Address varchar(100),
City varchar(100)
);
```

## 2. INSERT - 插入数据

***INSERT TO 语句用于向表格插入新的行。***

### 2.1 语法

```sql
INSERT INTO 表名称 VALUES (值1,值2,...)
```

或者指定所要插入数据的列：

```SQL
INSERT INTO table_name (列1, 列2,...) VALUE
```

### 2.2 实例

- 插入新的列

```sql
INSERT INTO Persons VALUES (1, 'Gates', 'Bill', 'Xuanwumen 10', 'Beijing');
```

- 在指定的列中插入数据

```sql
INSERT INTO Persons (LastName, Address) VALUES ('Wilson', 'Champs');
```

## 3. SELECT - 查询数据

### 3.1 语法

***SELECT语句用于从表中选取数据，结果被存储在一个结果表（成为结果集）。***

```sql
SELECT * FROM 表名称;
```

也可以指定所要查询的数据的列：

```sql
SELECT 列名称 FROM 表名称;
```

*SQL语句对大小写不敏感，SELECT等效于select。*

### 3.2 实例

```sql
SELECT * FROM Persons;
```

```sql
SELECT LastName, FirstName FROM Persons;
```

## 4. DISTINCT - 去除重复值

***如果一张表有多行重复数据，如何去重显示呢***

### 4.1 语法

```sql
SELECT DISTINCT 列名称 FROM Persons;
```

### 4.2 实例

```sql
SELECT DISTINCT LastName FROM Persons;
```

## 5. WHERE - 条件过滤

***如果需要从表中选取指定的数据，可将WHERE子句添加到SELECT语句。***

### 5.1 语法

```sql
SELECT 列名称 FROM 表名称 WHERE 列 运算符 值;
```

### 5.2 运算符

- =
- \>
- <
- \>=
- <=
- BETWEEN
- LIKE*搜索某种模式*

### 5.3 实例

```sql
SELECT * FROM Persons WHERE CITY='Beijing';
```

## 6.  AND & OR - 运算符

***WHERE多重条件***

## 7. ORDER BY - 排序

***ORDER BY 语句用于根据指定的列对结果集进行排序，默认按照升序对记录进行排序，如果您希望按照降序对记录进行排序，可以使用 DESC 关键字。***

### 7.1 语法

```SQL
SELECT * FROM 表名称 ORDER BY 列1,列2 DESC;
```

### 7.2 实例

以字母顺序显示LastName名称

```sql
SELECT * FROM Persons ORDER BY LASTNAME;
```

## 8. UPDATE - 更新数据

### 8.1 语法

- 更新单列

```sql
UPDATE 表名称 SET 列名称 = 新值 WHERE 列名称 = 某值;
```

- 更新多列

```SQL
UPDATE 表名称 SET 列名称1 = 新值1, 列名称2 = 新值2 WHERE 列名称 = 某值;
```



### 8.2 实例

​	目前 `Persons` 表有很多字段为 `null `的数据，可以通过 `UPDATE` 为 LASTNAME 是 “Wilson” 的人添加FIRSTNAME：

```sql
UPDATE Persons SET FirstName = 'Fred' WHERE LastName = 'Wilson';
```

```sql
UPDATE Persons SET ID_P = 6,city= 'London' WHERE LastName = 'Wilson';
```

## 9. DELETE - 删除数据

***DELETE用于删除表中的行***

### 9.1 语法

```sql
DELETE FROM 表名称 WHERE 列名称 = 值;
```

### 9.2 实例

删除Persons表中LastName为'Fred Wilson'的行：

```SQL
DELETE FROM Persons WHERE LastName = 'Fred Wilson';
```

删除所有行

```sql
DELETE FROM Persons;
```

## 10. TRUNCATE TABLE - 删除表数据

***仅仅删除表内数据，但并不删除表本身***

### 10.1 语法

```sql
TRUNCATE TABLE 表名称;
```

### 10.2 实例

```sql
TRUNCATE TABLE Persons;
```

## 11. DROP TABLE - 删除表

### 11.1 语法

```sql
DROP TABLE 表名称;
```

### 11.2 实例

```sql
DROP TABLE Persons;
```

## 12. ALTER - 修改表中的列

### 12.1 语法

​	在现有表中添加新列：

```sql
ALTER TABLE table_name
ADD column_name datatype;
```

# SQL高级语言学习

## 1. LIKE - 查找类似值

***LIKE操作符用于在WHERE子句中搜索列中的指定模式。***

### 1.1 语法

```sql
SELECT 列名 FROM 表名 WHERE 列名称 LIKE 值；
```

### 1.2 实例

选择Persons表中的居住在以N开头的城市里的人。

```SQL
SELECT * FROM Persons WHERE City LIKE 'N%';
```

以g结尾

```sql
SELECT * FROM Persons WHERE City LIKE '%g';
```

包含on

```SQL
SELECT * FROM Persons WHERE City like '%on%';
```

不包含

```sql
SELECT * FROM Persons WHERE NOT LIKE '%on%';
```

**注意：'%'可用来定义通配符**

 

## 2. IN - 锁定多个值

IN操作符允许我们在WHERE子句中规定多个值。

### 2.1  语法

```sql
SELECT * FROM 表名 WHERE 列名 IN (值1，值2，值3);
```

### 2.2 实例

我们希望从Persons表中选取姓氏为Adams和Carter的人

```sql
SELECT * FROM Persons WHERE LastName IN ('Adams', 'Carter');
```

## 3. BETWEEN - 选取区间数据

***操作符BETWEEN ... AND ... 会选取介于两个值之间的数据范围。这些值可能是数值、文本或者日期。***

### 3.1 语法

```sql
SELECT * FROM 表名 WHERE 列名 BETWEEN 值1 AND 值2；
```

### 3.2 实例

查询以字母顺序显示介于Adams(包括)和Carter(不包括)之间的人

```sql
SELECT * FROM Persons WHERE LastName BETWEEN 'Adams' AND 'Carter';
```

查询与上述结果相反的结果

```sql
SELECT * FROM Persons WHERE LastName NOT BETWEEN 'Adams' AND 'Carter';
```

## 4. AS - 别名

### 4.1 语法

表别名：

```SQL
SELECT 列名称 FROM 表名称 AS 别名;
```

列别名：

```sql
SELECT 列名称 AS 别名 FROM 表名称;
```

### 4.2 实例

使用表名别名

```sql
SELECT p.LastName, p.FirstName
FROM Persons AS p
WHERE p.LastName='Adams' AND p.FirstName='John';
```

使用列名别名

```sql
SELECT LastName AS "Family", FirstName "Name" FROM Persons;
```

**注意**：实际应用时，这个AS可以省略，但是列别名需要加引号。

## 5. JOIN - 多表关联

**JOIN**用于根据两个或多个表中的列之间的关系，从这些表中查询数据。

### 5.1 语法

```sql
SELECT 列名
FROM 表A
INNER|LEFT|RIGHT|FULL JOIN 表B
ON 表A主键列 = 表B外键列;
```

**不同的SQL join**

- JOIN: 如果表中有至少一个匹配，则返回行
- INNER JOIN: 内部连接，返回两表中匹配的行
- LEFT JOIN: 即使右表中没有匹配，也从左表返回所有的行
- RIGHT JOIN: 即使左表中没有匹配，也从右表返回所有的行
- FULL JOIN: 只要其中一个表中存在匹配，就返回行

### 5.2 实例

如果我们希望列出所有人的订购，可以使用下面的SELECT语句：

```sql
SELECT p.LastName, p.FirstName, o.OrderNo
FROM Persons p
INNER JOIN Orders o
ON p.Id_P = o.Id_P
ORDER BY p.LastName DESC;
```



## 6. UNION - 合并结果集

UNION操作符用于合并两个或多个SELECT语句的结果集。

### 6.1 语法

```sql
SELECT 列名 FROM 表A
UNION|UNION ALL
SELECT 列名 FROM 表B；
```

**注意**：UNION操作符默认选取不同的值，如果查询加过需要显示重复的值，使用`UNION ALL`。

## 7. NOT NULL - 非空

### 7.1 语法

```sql
CREATE TABLE 表
{
列 int NOT NULL；
};
```

**拓展**：`NOT NULL`也可以用来查询条件

```sql
SELECT * FROM Persons WHERE FirstName is NOT NULL;
```

同理，NULL也可以：

```sql
SELECT * FROM Persons WHERE FirstName is NULL;
```

## 8. GRANT - 授权

GRANT用于授予用户对数据库的访问权限

### 8.1 语法

```SQL
GRANT SELECT, UPDATE ON TABLE1 TO USER1, USER2;
```

## 9. REVOKE - 撤权

撤销对用户的给定访问权限

```sql
REVOKE SELECT, UPDATE ON TABLE1 FROM USER1, USER2;
```

## 10. 交易控制语言（TCL）

​	TCL命令的目的是维护数据库的一致性，这些命令通常与DML命令一起使用，DML命令所做的修改要么由TCL命令提交，要么由TCL命令回滚。

### 10.1 提交 - COMMIT

语法：

```sql
COMMIT;
```

实例

```SQL
UPDATE STUDENT
SET NAME = 'HELLO'
WHERE NAME = 'CPS';
COMMIT;
```

经由COMMIT命令提交后，可以将这些更改永久保存在表中。

### 10.2 ROLLBACK - 回滚

回滚命令用于临时撤销对数据库所做的更改。

语法：

```sql
ROLLBACK;
```

实例：

```sql
DELETE FROM STUDENT
WHERE AGE > 15;
ROLLBACK
```

上述命令原本从表中删除年龄大于15的所有学生，但是经由ROLLBACK命令后，撤销更改，实际上并未删除。

### 10.3 SAVEPOINT 

​	此命令有助于将事务回滚到某个点，例如，一个事务由多个DML命令组成，我们希望回退更改知道某个点而不是完全撤销，这时可以通过SAVEPOINT实现。

语法：

```sql
SAVEPOINT SAVEPOINT_NAME;
```

实例：

```sql
INSERT INTO EMPLOYEE (NAME, AGE)
VALUES ("HHHH", 23);

COMMIT;

UPDATE EMPLOYEE 
SET NAME = "AAA"
WHERE AGE = 88;

SAVEPOINT A;

DELETE FROM EMPLOYEE
WHERE AGE = 21;

SAVEPOINT B;
```

接下俩，如果我们想回滚某些DML命令，我们可以用ROLLBACK来实现。

回滚到保存点A：

```sql
ROLLBACK TO A;
```

# SQL语言的注意事项

- 不等于运算符：<>
- 逻辑运算符：

```sql
The subquery will fetch the student ids for all the students from SCHOOL table where age is greater than 18, these ids will be used by main query that will fetch the name of these students from STUDENT table:

SELECT name FROM STUDENT
WHERE studentID = ALL (
SELECT studentID FROM SCHOOL WHERE age > 18
);

This will fetch the records of students where city is 'Agra' and country is 'INDIA'. This will only fetch those records where both of these conditions are true, for example it will not fetch the record where country is 'INDIA' but city is other than 'Agra':

SELECT * FROM STUDENT
WHERE City = "Agra" AND Country = "INDIA";

This will fetch all the records where student age lies between 18 and 22:

SELECT * FROM STUDENT
WHERE age BETWEEN 18 AND 22;

The following query demonstrate the use of NOT and LIKE operator. It will fetch the names of the students from STUDENT table where name does not start with letter 'a' or 'A':

SELECT name FROM STUDENT
WHERE name NOT LIKE 'a%';
```

​                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                          
