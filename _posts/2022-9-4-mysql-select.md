---
layout: post
title: MySQL--Select语句
subtitle: MySQL第一篇
cover-img: /assets/img/four.png
share-img: /assets/img/four.png
tags: [MySQL]
---
# 前言
MySQL当时只照着一个初学者网站敲了一天，学完顺着就去学JDBC了，现在只会一个CRUD了，好多什么函数啊分页啥的都忘了个大概，所谓基础不牢地动山摇，这次来重头好好学学！
# SQL的分类
+ DDL(数据定义语言)
~~~SQL
CREATE \ ALTER \ DROP \ RENAME \TRUNCATE
~~~
+ DML(数据操作语言)
~~~SQL
INSERT \ DELETE \ UPDATE \ SELECT
~~~

+ DCL(数据控制语言)
~~~SQL
COMMIT \ ROLLBACK \ SAVEPOINT \GRANT \REVOKE
~~~
# 最基本的SELECT语句
## 用于运算
~~~SQL
SELECT 1+2+3;//查询结果为6
~~~
## 从表中查询某个数据
~~~SQL
# 基本格式
SELECT 字段1，字段2，... FROM 表名

# 从employee表中查询全部字段
SELECT * FROM employee

~~~
# 查询过程中的几个操作
## 列的别名
~~~SQL
# 从emloyeee表中查询小明的序号和薪水(字段名由employee_id变为id,employee_salary变为salary)
SELECT employee_id AS "id",employee_salary AS "salary" FROM emploee;
~~~
## 去除重复行
~~~SQL
# 查询员工表中一共有哪些部门
SELECT DISTINCT department_id AS "id" FROM emploee;
~~~
## 空值NULL参与运算
NULL不等同于0，不等同于'NULL'，只是还未填入的数据。且NULL参与任何运算运算结果都为NULL

## 着重号 ``
``里面的东西是字段名，避免在执行时被当作sql语句关键字

## 查询常数
~~~SQL
# 查询出来的结果前每一条都放一个常数
SELECT 1,emploee_id,employee_salary FROM emploee;
~~~
## 显示表结构
~~~SQL
DESCRIBE employee;
# 不要认为这玩意和SELECT * FROM employee 一样，这玩意只是会打印出来每个字段名是什么数据类型，有没有空值，默认是什么啊这种东西，不是来查数据的
~~~
## 过滤数据WHERE
~~~SQL
SELECT employee_id AS id,employee_salary AS salary FROM employees WHERE name = '小强';
~~~

# 结语
嘶，怎么说呢，感觉幸好我又重头复习了，都记忆模糊了
