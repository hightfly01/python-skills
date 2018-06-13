# 排序\(sort, reverse\)

sort方法：是将list按特定顺序重新排列，默认为由小到大，参数reverse=True可改为倒序，由大到小。

reverse方法：是将list逆置。

## 简单列表排序

```
>>> a = [1, 4, 2, 3]
>>> a
[1, 4, 2, 3]
>>> a.reverse()
>>> a
[3, 2, 4, 1]
>>> a.sort()
>>> a
[1, 2, 3, 4]
>>> a.sort(reverse=True)
>>> a
[4, 3, 2, 1]
```

## 复杂列表排序

按照每个元素中name进行排序：

```
stus = [
    {"name":"zhangsan", "age":18}, 
    {"name":"lisi", "age":19}, 
    {"name":"wangwu", "age":17}
]

>>> stus.sort(key = lambda x:x['name']) # 通过指定key，按照name进行排序
>>> stus
[{'age': 19, 'name': 'lisi'}, {'age': 17, 'name': 'wangwu'}, {'age': 18, 'name': 'zhangsan'}]
```

按照每个元素中age进行排序：

```
stus = [
    {"name":"zhangsan", "age":18}, 
    {"name":"lisi", "age":19}, 
    {"name":"wangwu", "age":17}
]

# 按照age进行降序排序
>>> stus.sort(reverse=True, key = lambda x:x['age']) # 通过指定key，按照age进行降序排序
>>> stus
[{'age': 19, 'name': 'lisi'}, {'age': 17, 'name': 'wangwu'}, {'age': 18, 'name': 'zhangsan'}]



#按照age进行升序排序
>>> stus.sort(reverse=False, key = lambda x:x['age']) # 通过指定key，按照age进行升序排序
>>> stus
[{'age': 19, 'name': 'lisi'}, {'age': 17, 'name': 'wangwu'}, {'age': 18, 'name': 'zhangsan'}]
```



