## 生成器表达式

虽然也可以用列表推导来初始化元组、数组或其他序列类型，但是生成器表达式是更好的 选择。这是**因为生成器表达式背后遵守了迭代器协议，可以逐个地产出元素，而不是先建 立一个完整的列表，然后再把这个列表传递到某个构造函数里**。



_**生成器表达式的语法跟列表推导差不多，只不过把方括号换成圆括号而已。**_



```
In [24]: symbols = '$¢£¥€¤'

In [26]: sc = (ord(symbol) for symbol in symbols)
In [27]: sc
Out[27]: <generator object <genexpr> at 0x10623ee60>  # 生成器

In [28]: tuple(sc)  # 转换为元组
Out[28]: (36, 162, 163, 165, 8364, 164)

In [36]: list(ord(symbol) for symbol in symbols) # 转换为列表
Out[36]: [36, 162, 163, 165, 8364, 164]
```

使用生成器表达式计算笛卡儿积：

```
>>> colors = ['black', 'white']
>>> sizes = ['S', 'M', 'L']
>>> for tshirt in ('%s %s' % (c, s) for c in colors for s in sizes): ➊ 
        ... print(tshirt)
...
black S
black M
black L
white S
white M
white L
```

➊生成器表达式逐个产出元素，从来不会一次性产出一个含有6个T恤样式的列表。  


