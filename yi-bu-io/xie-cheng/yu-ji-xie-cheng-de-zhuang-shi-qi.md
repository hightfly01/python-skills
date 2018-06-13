如果不预激，那么协程没什么用。调用coroutine.send\(x\)之前，记住一定要调用next\(coroutine \)。为了简化协程的用法，有时会使用一个预激装饰器。

#### 预激装饰器的定义：

    from functools import wraps

    def coroutine(func):
        """装饰器:向前执行到第一个`yield`表达式，预激`func`"""

        @wraps(func) #wraps修饰器作用：就是将 被修饰的函数(func) 的一些属性值赋值给 修饰器函数(coroutine) ，最终让属性的显示更符合我们的直觉。
        def primer(*args,**kwargs): ➊
            gen = func(*args,**kwargs) ➋ next(gen) ➌
            return gen ➍

        return primer

➊把被装饰的生成器函数替换成这里的primer函数;调用primer函数时，返回预激后的 生成器。

➋调用被装饰的函数，获取生成器对象。

➌预激生成器。  
➍返回生成器

#### 使用预激装饰：

```
“”“
用于计算移动平均值的协程
>>> coro_avg = averager() ➊
>>> from inspect import getgeneratorstate >>> getgeneratorstate(coro_avg) ➋ 'GEN_SUSPENDED'
>>> coro_avg.send(10) ➌
10.0
>>> coro_avg.send(30)
20.0
>>> coro_avg.send(5)
15.0
"""

from coroutil import coroutine ➍
@coroutine ➎
def averager(): 
         total = 0.0
         count = 0
         average = None
         while True:
             term = yield average
             total += term
             count += 1
             average = total/count
```

➊调用averager\(\)函数创建一个生成器对象，在coroutine装饰器的primer函数中已经 预激了这个生成器。

➋getgeneratorstate函数指明，处于GEN\_SUSPENDED状态，因此这个协程已经准备好，可 以接收值了。

➌可以立即开始把值发给coro\_avg——这正是coroutine装饰器的目的。

➍导入coroutine装饰器。  
➎把装饰器应用到averager函数上。

