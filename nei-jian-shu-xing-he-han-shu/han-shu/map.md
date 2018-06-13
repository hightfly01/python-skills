#### map函数 {#map函数}

map函数会根据提供的函数对指定序列做映射。

```
map(function, sequence[, sequence, ...]) -> list
```

* function:是一个函数

* sequence:是一个或多个序列,取决于function需要几个参数

* 返回值是一个list

```
#函数需要一个参数
map(lambda x: x*x, [1, 2, 3])
#结果为:[1, 4, 9]

#函数需要两个参数
map(lambda x, y: x+y, [1, 2, 3], [4, 5, 6])
#结果为:[5, 7, 9]


def f1( x, y ):  
    return (x,y)

l1 = [ 0, 1, 2, 3, 4, 5, 6 ]  
l2 = [ 'Sun', 'M', 'T', 'W', 'T', 'F', 'S' ]
l3 = map( f1, l1, l2 ) 
print(list(l3))
#结果为:[(0, 'Sun'), (1, 'M'), (2, 'T'), (3, 'W'), (4, 'T'), (5, 'F'), (6, 'S')]
```

参数序列中的每一个元素分别调用function函数，返回包含每次function函数返回值的list。

