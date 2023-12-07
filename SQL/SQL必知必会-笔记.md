# SQL必知必会

- [SQL必知必会](#sql必知必会)
  - [Basics](#basics)
  - [Wildcard](#wildcard)
  - [Functions](#functions)
  - [Group](#group)
  - [Subquery](#subquery)
  - [Join](#join)
  - [Union](#union)
  - [Insert](#insert)
  - [Update and Delete](#update-and-delete)
  - [Create and ALT](#create-and-alt)
  - [View 视图](#view-视图)
  - [Procedure 存储过程](#procedure-存储过程)
  - [Transaction processing 事务处理](#transaction-processing-事务处理)
  - [Constraint 约束](#constraint-约束)
    - [Primary Key](#primary-key)
    - [Foreign Key](#foreign-key)
    - [Unique](#unique)
    - [Check](#check)
  - [OLTP vs. OLAP](#oltp-vs-olap)

## Basics

- Primary Key 主键，表中的任何列都可以作为主键，只要它满足以下条件:
  
  - 任意两行都不具有相同的主键值;
  - 每一行都必须具有一个主键值(主键列不允许 NULL 值);
  - 主键列中的值不允许修改或更新;
  - 主键值不能重用(如果某行从表中删除，它的主键不能赋给以后的新行)。

- SQL 关键字不区分大小写

- DISTINCT 关键字作用于所有的列，不仅仅是跟在其后的那一列

- 第一个被检索的行是第 0 行，而不是第 1 行。因此，LIMIT 1 OFFSET 1 会检索第 2 行，而不是第 1 行

- Comment
  - `-- This is a comment.`
  - `/* This is a comment in different lines. */`

- Order
  - 关系数据库设计理论认为，如果不明确 规定排序顺序，则不应该假定检索出的数据的顺序有任何意义
  - 子句的位置：在指定一条 ORDER BY 子句时，应该保证它是 SELECT 语句中最后一 条子句。如果它不是最后的子句，将会出现错误消息
  - 在字典(dictionary)排序顺序中，A 被视为与 a 相同，这是大多数数 据库管理系统的默认行为。但是，许多 DBMS 允许数据库管理员在需要时改变这种行为

- Where
  - `<>`, `!=`, `!>`, `BETWEEN`, `IS NULL`，`IS NOT NULL`
  - `BETWEEN A AND B` 匹配范围包括开始值和结束值
  - 优先处理 AND 操作符，再处理 OR 操作符
  - IN 的最大优点是可以包含其他 SELECT 语句，能够更动态地建立 WHERE 子句, `WHERE vend_id IN ( 'DLL01', 'BRS01' )`

## Wildcard

- 通配符搜索只能用于文本字段(字符串)，非文本数据类型字段不能使用通配符搜索
- `%` 表示任何字符出现任意次数 `WHERE prod_name LIKE 'Fish%'`
  - 注意空格：存储的文本填满该列需要在文本后附加空格，可能对 SQL 语句有负面影响。子句 WHERE prod_name LIKE 'F%y'只匹配以F开头、以y结尾的prod_name。如果值后面跟空格，则不是以 y 结尾。简单的解决办法是给搜索模式再增加一个%号:'F%y%' 匹配 y 之后的字符(或空格)。更好的解决办法是用函数去掉空格。
  - `LIKE '%'` 不会匹配为 NULL 的行
- `_` 只匹配单个字符
- `[]` 指定一个字符集，它必须匹配指定位置(通配符的位置)的一个字符
- `[^M]` 此通配符可以用前缀字符^(脱字号)来否定
- Tips
  - 尽量不要把通配符用在搜索模式的开始处。把通配符置于开始处，搜索起来是最慢的
  - 不要过度使用通配符。如果其他操作符能达到相同的目的，应该使用其他操作符。

## Functions

- Concatenate 拼接：`SELECT Concat(vend_name, ' (', vend_country, ')')`, `SELECT vend_name + ' (' + vend_country + ')'`,  `SELECT vend_name || ' (' || vend_country || ')'`
- 许多数据库(不是所有)保存填充为列宽的文本值，而实际上的结果不需要这些空格: `SELECT RTRIM(vend_name) + ' (' + RTRIM(vend_country) + ')'` RTRIM()函数去掉值右边的所有空格, LTRIM()去掉字符串左边的空格以及 TRIM()去掉字符 串左右两边的空格
- String
  - SUBSTRING(), SUBSTR(), MID()
  - UPPER(), LOWER()
  - LENGTH() 字节数, CHAR_LENGTH() 字符数，英文字符每个占一字节
  - LEFT(), RIGHT()
  - CONVERT(), CAST()
- Date
  - YEAR()
  - CURDATE(), CURRENT_DATE(), SYSDATE(), GETDATE(), DATE(), NOW()
- Number
  - ABS(), SQRT()
  - COS(), SIN(), TAN()
  - EXP()
  - PI()
- Aggregate
  - AVG(DISTINCT prod_price), 忽略值为NULL的行
  - COUNT()，COUNT(*)包括NULL，COUNT(column)忽略NULL
  - MAX(), MIN()
  - SUM()

## Group

- GROUP BY 子句可以包含任意数目的列，因而可以对分组进行嵌套，更细致地进行数据分组。
- 如果在 GROUP BY 子句中嵌套了分组，数据将在最后指定的分组上进行汇总。换句话说，在建立分组时，指定的所有列都一起计算(所以 不能从个别的列取回数据)。
- GROUP BY 子句中列出的每一列都必须是检索列或有效的表达式(但不能是聚集函数)。如果在 SELECT 中使用表达式，则必须在 GROUP BY 子句中指定相同的表达式。不能使用别名。
- 大多数 SQL 实现不允许 GROUP BY 列带有长度可变的数据类型(如文 本或备注型字段)。
- 除聚集计算语句外，SELECT 语句中的每一列都必须在 GROUP BY 子句中给出。
- 如果分组列中包含具有 NULL 值的行，则 NULL 将作为一个分组返回。如果列中有多行 NULL 值，它们将分为一组。
- GROUP BY子句必须出现在WHERE子句之后，ORDER BY子句之前。WHERE 在数据分组前进行过滤，HAVING 在数据分组后进行过滤

## Subquery

- 作为子查询的 SELECT 语句只能查询单个列
- 作为计算字段使用子查询

## Join

- 笛卡儿积(cartesian product)：由没有联结条件的表关系返回的结果为笛卡儿积。检索出的行的数目将是第一个表中的行数乘以第二个表中的行数

## Union

- UNION 必须由两条或两条以上的 SELECT 语句组成，语句之间用关键字 UNION 分隔
- UNION 中的每个查询必须包含相同的列、表达式或聚集函数
- 列数据类型必须兼容:类型不必完全相同，但必须是 DBMS 可以隐含转换的类型
- UNION 从查询结果集中自动去除了重复的行;换句话说，它的行为与一条 SELECT 语句中使用多个 WHERE 子句条件一样; 如果想返回所有的匹配行，可使用UNION ALL而不是UNION。

## Insert

- insert into values

```sql
INSERT INTO Customers(cust_id,
                      cust_name,
                      cust_address,
                      cust_city,
                      cust_state,
                      cust_zip,
                      cust_country)
VALUES('1000000006',
       'Toy Land',
       '123 Any Street',
       'New York',
       'NY',
       '11111',
       'USA');
```

- insert select

```sql
INSERT INTO Customers(cust_id,
                      cust_contact,
                      cust_email,
                      cust_name,
                      cust_address,
                      cust_city,
                      cust_state,
                      cust_zip,
                      cust_country)
SELECT cust_id,
       cust_contact,
       cust_email,
       cust_name,
       cust_address,
       cust_city,
       cust_state,
       cust_zip,
       cust_country
FROM CustNew;
```

- select into

```sql
SELECT *
INTO CustCopy
FROM Customers;
```

## Update and Delete

## Create and ALT

```sql
alter table Vendors
add vend_phone char(20);
```

## View 视图

视图不包含任何列或数据，包含的是一个查询

作用：

- 重用 SQL 语句
- 简化复杂的 SQL 操作。在编写查询后，可以方便地重用它而不必知道其基本查询细节。
- 使用表的一部分而不是整个表。
- 保护数据。可以授予用户访问表的特定部分的权限，而不是整个表的访问权限。
- 更改数据格式和表示。视图可返回与底层表的表示和格式不同的数据。

## Procedure 存储过程

简单、安全、高性能

## Transaction processing 事务处理

通过确保成批的 SQL 操作要么完全执行，要么完全不执行，来维护数据库的完整性。管理insert，update和delete语句

术语：事务、回退、提交、保留点(savepoint)

## Constraint 约束

### Primary Key

### Foreign Key

外键是表中的一列，其值必须列在另一表的主键中。外键是保证引用完整性的极其重要部分。

```sql
ALTER TABLE Orders
ADD CONSTRAINT
FOREIGN KEY (cust_id) REFERENCES Customers (cust_id)
```

### Unique

- 唯一约束列可包含 NULL 值。
- 唯一约束列可修改或更新。
- 唯一约束列的值可重复使用。

### Check

```sql
ADD CONSTRAINT CHECK (gender LIKE '[MF]')
```

## OLTP vs. OLAP

OLTP（Online Transaction Processing）和 OLAP（Online Analytical Processing）是两种不同类型的数据处理系统，它们在数据处理和业务应用场景上有着根本的区别。

OLTP（在线事务处理）

- 定义：OLTP 是一种面向事务的数据处理方式，主要用于处理日常的业务交易。它通常用于处理大量的短小、简单的查询和更新操作。
- 特点：
  - 操作类型：处理频繁的插入、更新、删除操作。
  - 数据特性：OLTP 系统中的数据通常是当前的、操作性的，而且经常变化。
  - 性能需求：强调处理速度和数据的一致性，以支持日常业务操作。
  - 例子：银行系统中的账户交易、电子商务网站中的订单处理等。

OLAP（在线分析处理）

- 定义：OLAP 是一种面向分析的数据处理方式，用于快速分析大量的信息。它专注于对数据的复杂查询，以支持决策制定。
- 特点：
  - 操作类型：主要用于执行复杂的查询，特别是涉及到大量数据的聚合和汇总。
  - 数据特性：OLAP 系统中的数据通常是历史数据，更加稳定，用于分析和报告。
  - 性能需求：强调查询速度和数据的多维分析能力。
  - 例子：财务报告系统、销售数据分析、市场研究等。

对比总结

- 应用焦点不同：OLTP 主要关注日常事务处理，而 OLAP 关注的是数据分析和决策支持。
- 数据处理方式：OLTP 系统强调快速、高效的事务处理，而 OLAP 系统设计用来进行复杂的数据查询和分析。
- 数据的组织和结构：OLTP 系统中数据通常以行为中心的格式存储（便于快速处理事务），而 OLAP 系统则倾向于列式存储或多维数据结构（优化查询性能）。

在实际的业务环境中，OLTP 和 OLAP 系统通常是互补的，两者共同支持组织的运营和决策制定过程。
