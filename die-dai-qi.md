# 迭代器 {#迭代器}

**迭代是访问集合元素的一种方式。**

**迭代器是一个可以记住遍历位置的对象并且**_**可以被next\(\)函数调用并不断返回下一个值的对象称为迭代器：Iterato**_\)。

**迭代器对象从集合的第一个元素开始访问，直到所有的元素被访问完结束。迭代器只能往前不会后退。**

## 1. 可迭代对象 {#1-可迭代对象}

以直接作用于 for 循环的数据类型有以下几种：

一类是**集合数据类型**，如 list 、 tuple 、 dict 、 set 、 str 等；

一类是 generator\(生成器\) ，包括生成器和带 yield 的generator function。

这些可以直接作用于 for 循环的对象统称为可迭代对象： Iterable 。

### 特殊强调：

* 可迭代对象，不一定是迭代器。

* 比如集合数据类型\(list 、 tuple 、 dict 、 set 、 str\), 它们是可以迭代，属于可迭代对象，但不是迭代器。如果想让可迭代对象成为迭代器，需要使用`iter()`函数进行转换。

```
iter([1,2])
iter('abc')
iter((1,2))
iter({})
```

* 生成器是一个迭代器，可以迭代，因此也属于可迭代对象

## 2. 判断是否可迭代对象 {#2-判断是否可以迭代}

可以使用 `isinstance()` 判断一个对象是否是 Iterable 对象：

```
In [50]: from collections import Iterable

In [51]: isinstance([], Iterable)
Out[51]: True

In [52]: isinstance({}, Iterable)
Out[52]: True

In [53]: isinstance('abc', Iterable)
Out[53]: True

In [54]: isinstance((x for x in range(10)), Iterable)
Out[54]: True

In [55]: isinstance(100, Iterable)
Out[55]: False
```

## 3.迭代器 {#3迭代器}

可以被next\(\)函数调用并不断返回下一个值的对象称为迭代器：Iterator。

可以使用 isinstance\(\) 判断一个对象是否是 Iterator 对象：

```
In [56]: from collections import Iterator

In [57]: isinstance((x for x in range(10)), Iterator)
Out[57]: True

In [58]: isinstance([], Iterator)
Out[58]: False

In [59]: isinstance({}, Iterator)
Out[59]: False

In [60]: isinstance('abc', Iterator)
Out[60]: False

In [61]: isinstance(100, Iterator)
Out[61]: False
```

## 4.iter\(\)函数将迭代对象转换为迭代器 {#4iter函数}

生成器都是 Iterator 对象，但 list 、 dict 、 str 虽然是 Iterable ，却不是 Iterator 。

把 list 、 dict 、 str 等 Iterable 变成 Iterator 可以使用 iter\(\) 函数：

```
In [62]: isinstance(iter([]), Iterator)
Out[62]: True

In [63]: isinstance(iter('abc'), Iterator)
Out[63]: True
```

## 总结 {#总结}

* 凡是可作用于 for 循环的对象都是 Iterable 类型；
* 凡是可作用于 next\(\) 函数的对象都是 Iterator 类型
* 集合数据类型如 list 、 dict 、 str 等是 Iterable 但不是 Iterator ，不过可以通过 iter\(\) 函数获得一个 Iterator 对象。



