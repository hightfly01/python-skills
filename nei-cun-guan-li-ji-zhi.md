Python的内存管理机制可以从三个方面来讲：

### 垃圾回收

* 引用计数
* 标记-清除
* 分代收集

### 内存池

Python的内存机制以金字塔行进行管理：如图所示：

![](/assets/Snip20180226_3.png)

* -1，-2层主要有操作系统进行操作。

* 0层是C中的malloc，free等内存分配和释放函数进行操作；

* 1层和2层是内存池，有Python的接口函数PyMem\_Malloc函数实现，当对象小于256K时有该层直接分配内存。避免为频繁申请和销毁内存空间

  ```
  小整数对象池：
     Python 对小整数的定义是 [-5, 257) 这些整数对象是提前建立好的，不会被垃圾回收。
     在一个 Python 的程序中，所有位于这个范围内的整数使用的都是同一个对象.

  大整数对象池：每一个大整数，均创建一个新的对象
  ```

* 第3层是最上层，也就是我们对Python对象的直接操作；

### intern机制

```
a1 = "HelloWorld"
a2 = "HelloWorld"
a3 = "HelloWorld"
a4 = "HelloWorld"
a5 = "HelloWorld"
a6 = "HelloWorld"
a7 = "HelloWorld"
a8 = "HelloWorld"
a9 = "HelloWorld"
```

以上定义了9个对象，由于intern机制，让每个对象占用一个`HelloWorld`所占用的内存空间。靠引用计数去维护何时释放

![](/assets/Snip20180226_2.png)

`注意：对于大整数对象以及包含空格字符串对象，不共享内存。`

