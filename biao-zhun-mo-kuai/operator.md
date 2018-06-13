operator模块为**多个算术运算符提供了对应的函数**，从而避免编写lambda a, b: a\*b这种 平凡的匿名函数。

### operator.mul函数

示例：使用reduce和operator.mul函数计算阶乘

```
from functools import reduce
     from operator import mul
     def fact(n):
         return reduce(mul, range(1, n+1))
```

使用reduce函数和一个匿名函数计算阶乘：

```
from functools import reduce
def fact(n):
         return reduce(lambda a, b: a*b, range(1, n+1))
```

### operator.itemgetter函数

operator.itemgetter函数：能够从序列中取出元素。

itemgetter的常见用途:根据元组的某个字段给元组列表排序。

示例：使用itemgetter排序一个元组列表：

```
     >>> metro_data = [
     ...     ('Tokyo', 'JP', 36.933, (35.689722, 139.691667)),
     ...     ('Delhi NCR', 'IN', 21.935, (28.613889, 77.208889)),
     ...     ('Mexico City', 'MX', 20.142, (19.433333, -99.133333)),
     ...     ('New York-Newark', 'US', 20.104, (40.808611, -74.020386)),
     ...     ('Sao Paulo', 'BR', 19.649, (-23.547778, -46.635833)),
     ... ]
     >>>
     >>> from operator import itemgetter
     >>> for city in sorted(metro_data, key=itemgetter(1)):
     ...     print(city)
     ...
     ('Sao Paulo', 'BR', 19.649, (-23.547778, -46.635833))
     ('Delhi NCR', 'IN', 21.935, (28.613889, 77.208889))
     ('Tokyo', 'JP', 36.933, (35.689722, 139.691667))
     ('Mexico City', 'MX', 20.142, (19.433333, -99.133333))
     ('New York-Newark', 'US', 20.104, (40.808611, -74.020386))
```

在这个示 例中，按照国家代码\(第2个字段\)的顺序打印各个城市的信息。

其实，itemgetter\(1\)的 作用与lambda fields: fields\[1\]一样:创建一个接受集合的函数，返回索引位1上的元 素。

如果把多个参数传给itemgetter，它构建的函数会返回提取的值构成的元组:

```
     >>> cc_name = itemgetter(1, 0)
     >>> for city in metro_data:
     ...     print(cc_name(city))
     ...
     ('JP', 'Tokyo')
     ('IN', 'Delhi NCR')
     ('MX', 'Mexico City')
     ('US', 'New York-Newark')
     ('BR', 'Sao Paulo')
     >>>
```

### operator.attrgetter函数

attrgetter与itemgetter作用类似，它创建的函数根据名称提取对象的属性。

如果把 多个属性名传给attrgetter，它也会返回提取的值构成的元组。此外，如果参数名中包 含.\(点号\)，attrgetter会深入嵌套对象，获取指定的属性。

示例：定义一个namedtuple，名为metro\_data\(与示例5-23中的列表相同\)，演示使 用attrgetter处理它：

```
>>> from collections import namedtuple
>>> metro_data = [
     ...     ('Tokyo', 'JP', 36.933, (35.689722, 139.691667)),
     ...     ('Delhi NCR', 'IN', 21.935, (28.613889, 77.208889)),
     ...     ('Mexico City', 'MX', 20.142, (19.433333, -99.133333)),
     ...     ('New York-Newark', 'US', 20.104, (40.808611, -74.020386)),
     ...     ('Sao Paulo', 'BR', 19.649, (-23.547778, -46.635833)),
     ... ]
>>>
>>> LatLong = namedtuple('LatLong', 'lat long') # ➊
>>> Metropolis = namedtuple('Metropolis', 'name cc pop coord') # ➋

>>> metro_areas = [Metropolis(name, cc, pop, LatLong(lat, long)) # ➌
... for name, cc, pop, (lat, long) in metro_data]

>>> metro_areas[0]
Metropolis(name='Tokyo', cc='JP', pop=36.933, coord=LatLong(lat=35.689722, long=139.691667))
>>> metro_areas[0].coord.lat # ➍
35.689722

>>> from operator import attrgetter

>>> name_lat = attrgetter('name','coord.lat') #5
>>>
>>> for city in sorted(metro_data, key=attrgetter('coord.lat')) #6
...     print(name_lat(city)) #7
...
('Sao Paulo', -23.547778)
('Mexico City', 19.433333)
('Delhi NCR', 28.613889)
('Tokyo', 35.689722)
('New York-Newark', 40.808611)
```

➊使用namedtuple定义LatLong。  
➋再定义Metropolis。  
➌使用Metropolis实例构建metro\_areas列表;注意，我们使用嵌套的元组拆包提取

\(lat, long\)，然后使用它们构建LatLong，作为Metropolis的coord属性。

➍深入metro\_areas\[0\]，获取它的纬度。  
➎定义一个attrgetter，获取name属性和嵌套的coord.lat属性。  
➏再次使用attrgetter，按照纬度排序城市列表。

➐使用标号➎中定义的attrgetter，只显示城市名和纬度。

### operator.methodcaller函数

methodcaller。它的作用与attrgetter和itemgetter类似，它会自行创建函数。methodcaller创建的函数会在对象上调用参数指 定的方法，如示例所示:

```
      >>> from operator import methodcaller
      >>> s = 'The time has come'
      >>> upcase = methodcaller('upper')
      >>> upcase(s)
      'THE TIME HAS COME'
      >>> hiphenate = methodcaller('replace', ' ', '-')
      >>> hiphenate(s)
      'The-time-has-come'
```



