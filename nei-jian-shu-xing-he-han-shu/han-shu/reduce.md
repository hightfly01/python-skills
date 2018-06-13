#### reduce函数 {#reduce函数}

reduce函数，reduce函数会对参数序列中元素进行累积

```
reduce(function, sequence[, initial]) -> value
```

参数说明：

* function:该函数有两个参数

* sequence:序列可以是str，tuple，list

* initial:固定初始值

```
reduce(lambda x, y: x+y, [1,2,3,4])
10

reduce(lambda x, y: x+y, [1,2,3,4], 5)
15

reduce(lambda x, y: x+y, ['aa', 'bb', 'cc'], 'dd')
'ddaabbcc'
```

注意：

> 在Python3里,reduce函数已经被从全局名字空间里移除了, 它现在被`放置在fucntools模块里`用的话要先引入：
>
> `from functools import reduce`



使用reduce和sum计算0~99之和:

```
>>> from functools import reduce ➊
>>> from operator import add ➋
>>> reduce(add, range(100)) ➌
4950
>>> sum(range(100)) ➍ 4950
>>>
```

➊从Python 3.0起，reduce不再是内置函数了。  
➋导入add，以免创建一个专求两数之和的函数。  
➌计算0~99之和。  
➍使用sum做相同的求和;无需导入或创建求和函数。

