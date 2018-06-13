### deque

deque：collections模块中提供的工具。

collections.deque类\(双向队列\)是一个线程安全、可以快速从两端添加或者删除元素的 数据类型。

使用`list`存储数据时，按索引访问元素很快，但是插入和删除元素就很慢了，因为`list`是线性存储，数据量大的时候，插入和删除效率很低。

`deque`是为了高效实现插入和删除操作的双向列表，适合用于队列和栈：

```
>>> from collections import deque
>>> q = deque(['a', 'b', 'c'])
>>> q.append('x')
>>> q.appendleft('y')
>>> q
deque(['y', 'a', 'b', 'c', 'x'])
```

`deque`除了实现list的`append()`和`pop()`外，还支持`appendleft()`和`popleft()`，这样就可以非常高效地往头部添加或删除元素。



使用双向队列：

```
>>> from collections import deque
>>> dq = deque(range(10), maxlen=10) ➊
>>> dq
deque([0, 1, 2, 3, 4, 5, 6, 7, 8, 9], maxlen=10) 
>>> dq.rotate(3) ➋
>>> dq
deque([7, 8, 9, 0, 1, 2, 3, 4, 5, 6], maxlen=10) 
>>> dq.rotate(-4)
>>> dq
deque([1, 2, 3, 4, 5, 6, 7, 8, 9, 0], maxlen=10) 
>>> dq.appendleft(-1) ➌
>>> dq
deque([-1, 1, 2, 3, 4, 5, 6, 7, 8, 9], maxlen=10) 
>>> dq.extend([11, 22, 33]) ➍
>>> dq
deque([3, 4, 5, 6, 7, 8, 9, 11, 22, 33], maxlen=10) 
>>> dq.extendleft([10, 20, 30, 40]) ➎
>>> dq
deque([40, 30, 20, 10, 3, 4, 5, 6, 7, 8], maxlen=10)
```

➊maxlen是一个可选参数，代表这个队列可以容纳的元素的数量，而且一旦设定，这个 属性就不能修改了。

➋队列的旋转操作接受一个参数n，当n &gt; 0时，队列的最右边的n个元素会被移动到队 列的左边。当n &lt; 0时，最左边的n个元素会被移动到右边。

➌当试图对一个已满\(len\(d\) == d.maxlen\)的队列做头部添加操作的时候，它尾部的元 素会被删除掉。注意在下一行里，元素0被删除了。

➍在尾部添加3个元素的操作会挤掉-1、1和2。  
➎extendleft\(iter\)方法会把迭代器里的元素逐个添加到双向队列的左边，因此迭代器里

的元素会逆序出现在队列里。  


