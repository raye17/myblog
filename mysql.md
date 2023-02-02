#### 查询结果去重

```
distinct 
只能放在查询字段最前面，对后面所有字段均起作用
group by
对后面所有字段均起作用，可放在查询字段后面
```
#### 查询结果限制返回

```
返回前两行
select id FROM tableNmae WHERE id in(1,2)
select id FROM tableNmae WHERE id <= 2 
select id FROM tableNmae limit 2 
select id FROM tableNmae limit 0,2 
```
#### 查询后的列重命名

```
select id as user_infos_example from tablename limit 2
```

