## 列表推导式

列表推导式可读性

```
In [1]: a=[-1,2,3,-10,-30]

In [2]: b = [abs(item) for item in a]

In [3]: b
Out[3]: [1, 2, 3, 10, 30]
```

列表推导同filter和map的比较

```
In [13]: symbols = '$¢£¥€¤'

In [14]: codes = [ord(s) for s in symbols if ord(s) > 127]

In [15]: codes
Out[15]: [162, 163, 165, 8364, 164]
```

```
In [16]: codes = list(filter(lambda c: c > 127, map(ord, symbols)))

In [17]: codes
Out[17]: [162, 163, 165, 8364, 164]
```

使用列表推导计算笛卡儿积

```
In [19]: colors = ['black', 'white']

In [20]: sizes = ['S', 'M', 'L']

In [21]: tshirts = [(color, size) for color in colors for size in sizes]

In [22]: tshirts
Out[22]:
[('black', 'S'),
 ('black', 'M'),
 ('black', 'L'),
 ('white', 'S'),
 ('white', 'M'),
 ('white', 'L')]
```

注意：

> 列表推导的作用只有一个:生成列表。如果想生成其他类型的序列，可以使用生成器



