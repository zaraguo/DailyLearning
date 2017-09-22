# Mysql explain

在查看某个 sql 语句的执行效率的时候我们可以用 explain 来进行查看分析

```
explain <table> 
describe <table>
explain <sql>
```

## 字段解释

| id     | select_type | table | type | possible_keys | key | key_len | ref | rows | Extra |
|--------|-------------|-------|------|---------------|-----|---------|-----|------|-------|

* id 执行顺序，从大到小执行
* select_type
    * SIMPLE
    * PRIMARY
    * UNION
    * DEPENDENT UNION
    * UNION RESULT
    * SUBQUERY
    * DEPENDENT SUBQUERY
    * DERIVED 派生的子查询
* table
    * 是关于哪张表的
    * derived[x]
* type 连接类型，有无索引，const、eq_ref、ref、range、indexhe、ALL 
    * const 根据主键或者唯一索引查找
        * system 所查找的范围只有一条记录
    * eq_ref
    * ref
    * range
    * indexhe
    * ALL
* possible_keys 本次查找中可能用作索引的键，无视表的次序?
* key 查找实际使用的键（索引），没有则为 NULL
* key_len 实际所使用的键长度, 在不损失精度的情况下，长度越短越好
* ref 显示哪个列或者常数与 key 一起从表中选择行
* rows 认为得到查询结果所必须检查的行数
* extra
    * using where
    * distinct
    * not exist
    * range checked for each
    * using index
    * using temporary
    * using filesort

## 关于 explain count 返回的 rows 数量与 count() 执行结果不一致

explain 的执行结果是一个作为你该条 sql 语句执行情况的预估，他并不会真的去执行你的语句。这个语句是建立在表的一些信息上的 [推测](https://lists.mysql.com/commits/115810)。

## 参考

[Mysql Explain 详解](http://www.cnitblog.com/aliyiyi08/archive/2008/09/09/48878.html)
