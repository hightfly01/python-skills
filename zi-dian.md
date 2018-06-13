# 字典介绍

## 定义：

```
info = {'name':'班长', 'id':100, 'sex':'f', 'address':'地球亚洲中国北京'}
```

## 根据键访问值 {#根据键访问值}

```
    info = {'name':'班长', 'id':100, 'sex':'f', 'address':'地球亚洲中国北京'}

    print(info['name'])
    print(info['address'])
```

注意：在我们不确定字典中是否存在某个键而又想获取其值时，可以使用get方法，还可以设置默认值：

```
>>> age = info.get('age')
>>> age #'age'键不存在，所以age为None
>>> type(age)
<type 'NoneType'>
>>> age = info.get('age', 18) # 若info中不存在'age'这个键，就返回默认值18
>>> age
18
```

## 遍历字典

#### &lt;1&gt; 遍历字典的key（键） {#遍历字典的key（键）}

```
Out[180]: info={'age': 10, 'name': 'ywf'}
In [188]: for key in info.keys():
     ...:     print(key)
     ...:
name
age
```

#### &lt;2&gt; 遍历字典的value（值） {#遍历字典的value（值）}

```
Out[180]: info={'age': 10, 'name': 'ywf'}

In [189]: for value in info.values():
     ...:     print(value)
     ...:
     ...:
ywf
10

In [190]:
```

#### &lt;3&gt; 遍历字典的项（元素） {#遍历字典的项（元素）}

```
Out[180]: info={'age': 10, 'name': 'ywf'}

In [190]: for item in info.items():
     ...:     print(item)
('name', 'ywf')
('age', 10)

In [191]:
```

#### &lt;4&gt; 遍历字典的key-value（键值对） {#遍历字典的项（元素）}

```
Out[180]: info={'age': 10, 'name': 'ywf'}

In [191]: for key,value in info.items():
     ...:     print(key,value)
     ...:
name ywf
age 10

In [192]:
```

#### &lt;4&gt; 带下标索引的遍历 {#遍历字典的项（元素）}

enumerate\(\):函数可以生产带有下标的索引

```
In [193]: for i,item in enumerate(info.items()):
     ...:     print(i,item)
     ...:
0 ('name', 'ywf')
1 ('age', 10)
```

## 字典的常见操作

### &lt;1&gt;修改元素

字典的每个元素中的数据是可以修改的，只要通过key找到，即可修改

```
    info = {'name':'班长', 'id':100, 'sex':'f', 'address':'地球亚洲中国北京'}
    info['id'] = 200
```

### &lt;2&gt;添加元素

如果在使用**变量名\['键'\] = 数据**时，这个“键”在字典中，不存在，那么就会新增这个元素

```
info = {'name':'班长', 'sex':'f', 'address':'地球亚洲中国北京'}
info['id'] = 100
```

### &lt;3&gt;删除元素

对字典进行删除操作，有一下几种：

* del
* clear\(\)
* pop\(key\) 根据key移除元素，移除的key不存在，抛出异常

```
    info = {'name':'班长', 'sex':'f', 'address':'地球亚洲中国北京'}
    del info['name'] # 删除指定元素
    del info # 删除整个字典
    info.clear() # 清空整个字典
    info.pop('name') # 根据key移除元素
```

### &lt;4&gt;len\(\) {#len}

测量字典中，键值对的个数

```
In [133]: info={'name':'ywf', 'age':10,'sex':1}

In [134]: len(info)
Out[134]: 3

In [135]:
```

### &lt;5&gt;keys {#keys}

返回一个包含字典所有KEY的列表

```
In [133]: info={'name':'ywf', 'age':10,'sex':1}

In [136]: info.keys()
Out[136]: dict_keys(['name', 'age', 'sex'])

In [137]:
```

### &lt;6&gt;values {#values}

返回一个包含字典所有value的列表

```
In [133]: info={'name':'ywf', 'age':10,'sex':1}

In [137]: info.values()
Out[137]: dict_values(['ywf', 10, 1])

In [138]:
```

### &lt;7&gt;items {#items}

返回一个包含所有（键，值）元组的列表

```
In [133]: info={'name':'ywf', 'age':10,'sex':1}
In [138]: info.items()
Out[138]: dict_items([('name', 'ywf'), ('age', 10), ('sex', 1)])

In [139]:
```

### &lt;8&gt; in 判断是否包含key {#haskey}

使用 in 判断是否包含key。

如：

```
In [133]: info={'name':'ywf', 'age':10,'sex':1}

In [149]: 'name' in info.keys()
Out[149]: True

In [150]: 'addr' in info.keys()
Out[150]: False
```

### &lt;9&gt;clear\(\)

清空整个字典

```
info = {'name':'班长', 'sex':'f', 'address':'地球亚洲中国北京'}
info.clear() # 清空整个字典
```

### &lt;10&gt;get\(key\)

根据key，获取对应的value.如果字典中不存在key，返回None

```
In [163]: info
Out[163]: {'age': 10, 'sex': 1}

In [164]: info.get('name')

In [165]: info.get('age')
Out[165]: 10
```

### &lt;11&gt;pop\(key\)

根据key移除元素，移除的key不存在，抛出异常

```
Out[163]: info={'age': 10, 'sex': 1}

In [166]: info.pop('name') # 移除的key在字典中不存在
---------------------------------------------------------------------------
KeyError                                  Traceback (most recent call last)
<ipython-input-166-e15d6171392a> in <module>()
----> 1 info.pop('name')

KeyError: 'name'

In [167]: info.pop('age')
Out[167]: 10

In [168]: info
Out[168]: {'sex': 1}

In [169]:
```

### &lt;12&gt;popitem\(\)

从字典中移除包含（key:value）的一组元组

```
Out[163]: info={'sex': 1}

In [171]: info.popitem()
Out[171]: ('sex', 1)

In [172]: info
Out[172]: {}
```



