#### filter函数 {#filter函数}

```
filter(function or None, sequence) -> list, tuple, or string
```

参数说明：

* function:接受一个参数，返回布尔值True或False

* sequence:序列可以是str，tuple，list

特点：

filter函数会对序列参数sequence中的每个元素调用function函数，最后返回的结果包含调用结果为True的元素。

返回值的类型和参数sequence的类型相同

```
filter(lambda x: x%2, [1, 2, 3, 4])
[1, 3]

filter(None, "she")
'she'
```

####  {#reduce函数}



