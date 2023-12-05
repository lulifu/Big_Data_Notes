# SQL必知必会

- [SQL必知必会](#sql必知必会)
  - [Basics](#basics)
  - [Wildcard](#wildcard)
  - [Functions](#functions)
  - [Group](#group)
  - [TODO List](#todo-list)

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
  - LENGTH()
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

## TODO List

- OLTP, OLAP
