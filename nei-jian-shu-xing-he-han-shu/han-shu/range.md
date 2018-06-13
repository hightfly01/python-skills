#### range {#range}

```
range(stop) -> list of integers
range(start, stop[, step]) -> list of integers
```

* start:计数从start开始。默认是从0开始。例如range（5）等价于range（0， 5）;

* stop:到stop结束，但不包括stop.例如：range（0， 5） 是\[0, 1, 2, 3, 4\]没有5

* step:每次跳跃的间距，默认为1。例如：range（0， 5） 等价于 range\(0, 5, 1\)

python2中range返回列表，python3中range返回一个迭代值。如果想得到列表,可通过list函数

```
a = range(5)
list(a)

或者

In [21]: testList = [x+2 for x in range(5)]
In [22]: testList
Out[22]: [2, 3, 4, 5, 6]
```

####  {#map函数}



