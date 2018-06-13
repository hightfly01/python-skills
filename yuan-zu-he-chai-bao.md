## 元组和拆包

元组其实是对数据的记录:元组中的每个元素都存放了记录中一个字段的数据，外加这个

字段的位置。

#### 把元组用作记录：

```
In [38]: coords = (2,3,-1,10) # 定义元组

In [39]: tras = [item for item in sorted(coords)] # 对元组中的元素排序，生成一个新的列表

In [40]: tras
Out[40]: [-1, 2, 3, 10]
```

#### 元组拆包

元组拆包可以应用到任何可迭代对象上，唯一的硬性要求是，被可迭代对象 中的元素数量必须要跟接受这些元素的元组的空档数一致

```
>>> lax_coordinates = (33.9425, -118.408056)
>>> latitude, longitude = lax_coordinates # 元组拆包 >>> latitude
33.9425
>>> longitude
-118.408056
```

### 还可以用\*运算符把一个可迭代对象拆开作为函数的参数:

```
     >>> t = (20, 8)
     >>> divmod(*t)
     (2, 4)
     >>> quotient, remainder = divmod(*t)
     >>> quotient, remainder
     (2, 4)
```

### 用\*来处理剩下的元素

在Python中，函数用\*args来获取不确定数量的参数算是一种经典写法了。

```
     >>> a, b, *rest = range(5)
     >>> a, b, rest
     (0, 1, [2, 3, 4])
     >>> a, b, *rest = range(3)
     >>> a, b, rest
     (0, 1, [2])
     >>> a, b, *rest = range(2)
     >>> a, b, rest
     (0, 1, [])
```

### 嵌套元组拆包

用嵌套元组来获取经度

```
In [48]: metro_areas = [
    ('Tokyo','JP',36.933,(35.689722,139.691667)),
    ('Delhi NCR', 'IN', 21.935, (28.613889, 77.208889)), 
    ('Mexico City', 'MX', 20.142, (19.433333, -99.133333)), 
    ('New York-Newark', 'US', 20.104, (40.808611, -74.020386)), 
    ('Sao Paulo', 'BR', 19.649, (-23.547778, -46.635833)),
   ]

In [50]: for name, cc, pop, (lat,long) in metro_areas: # 嵌套拆包
    ...:     print(name, cc,pop,(lat,long))
    ...:
Tokyo JP 36.933 (35.689722, 139.691667)
Delhi NCR IN 21.935 (28.613889, 77.208889)
Mexico City MX 20.142 (19.433333, -99.133333)
New York-Newark US 20.104 (40.808611, -74.020386)
Sao Paulo BR 19.649 (-23.547778, -46.635833)
```

### 具名元组 

collections.namedtuple是一个工厂函数，它可以用来构建一个带字段名的元组和一个有名字的类。

新建一个Car类：

```
Card = collections.namedtuple('Card', ['rank', 'suit'])
```

定义和使用具名元组：

```
>>> from collections import namedtuple
>>> City = namedtuple('City', 'name country population coordinates') ➊ 
>>> tokyo = City('Tokyo', 'JP', 36.933, (35.689722, 139.691667)) ➋
>>> tokyo
City(name='Tokyo', country='JP', population=36.933, coordinates=(35.689722, 139.691667))
>>> tokyo.population ➌
36.933
>>> tokyo.coordinates
(35.689722, 139.691667)
>>> tokyo[1]
'JP'
```

➊创建一个具名元组需要两个参数，一个是类名，另一个是类的各个字段的名字。后者可 以是由数个字符串组成的可迭代对象，或者是由空格分隔开的字段名组成的字符串。

➋存放在对应字段里的数据要以一串参数的形式传入到构造函数中\(注意，元组的构造函 数却只接受单一的可迭代对象\)。

➌你可以通过字段名或者位置来获取一个字段的信息。



### 























