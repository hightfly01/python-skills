## 产出两个值的协程

```
>>> def simple_coro2(a):
     ...     print('-> Started: a =', a)
... b = yield a
     ...     print('-> Received: b =', b)
     ...     c = yield a + b
     ...     print('-> Received: c =', c)
     ...
     >>> my_coro2 = simple_coro2(14)
     >>> from inspect import getgeneratorstate
>>> getgeneratorstate(my_coro2) ➊ 'GEN_CREATED'
>>> next(my_coro2) ➋
-> Started: a = 14
14
>>> getgeneratorstate(my_coro2) ➌ 'GEN_SUSPENDED'
>>> my_coro2.send(28) ➍
-> Received: b = 28
42
>>> my_coro2.send(99) ➎
-> Received: c = 99
Traceback (most recent call last):
File "<stdin>", line 1, in <module> StopIteration
>>> getgeneratorstate(my_coro2) ➏ 'GEN_CLOSED'
```

执行流程分析：

➊inspect.getgeneratorstate函数指明，处于GEN\_CREATED状态\(即协程未启动\)。

➋向前执行协程到第一个yield表达式，打印-&gt; Started: a = 14消息，然后产出a的值，并且暂停，等待为b赋值。  
➌getgeneratorstate函数指明，处于GEN\_SUSPENDED状态\(即协程在yield表达式处暂停\)。

➍把数字28发给暂停的协程;计算yield表达式，得到28，然后把那个数绑定给b。打印-&gt; Received: b = 28消息，产出a + b的值\(42\)，然后协程暂停，等待为c赋值。

➎把数字99发给暂停的协程;计算yield表达式，得到99，然后把那个数绑定给c。打印-&gt; Received: c = 99消息，然后协程终止，导致生成器对象抛出StopIteration异常。

➏getgeneratorstate函数指明，处于GEN\_CLOSED状态\(即协程执行结束\)。



**关键的一点是，**协程在yield关键字所在的位置暂停执行。前面说过，在赋值语句中，=右边的代码在赋值之前执行。因此，对于b = yield a这行代码来说，等到客户端代码再 激活协程时才会设定b的值。





**simple\_coro2协程的执行过程分为3个阶段。**

如图所示。

![](/assets/Snip20180228_1.png)

\(1\)调用next\(my\_coro2\)，打印第一个消息，然后执行yield a，产出数字14。

\(2\)调用my\_coro2.send\(28\)，把28赋值给b，打印第二个消息，然后执行yield a + b，产出数字42。  
\(3\)调用my\_coro2.send\(99\)，把99赋值给c，打印第三个消息，协程终止。

