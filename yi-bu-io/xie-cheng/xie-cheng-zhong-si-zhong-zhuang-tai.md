```
from inspect import getgeneratorstate # 通过getgeneratorstate查看协程状态

def simple_coroutine():
    while True:#这个无限循环表明，只要调用方不断把值发给这个协程，它就会一直接收值，然后生成 结果。
               #仅当调用方在协程上调用 .close() 方法，或者没有对协程的引用而被垃圾回收 程序回收时，这个协程才会终止。
        print('--> coroutine started...')
        x = yield
        print('--> coroutine received:', x)


my_coro = simple_coroutine()
print('status ---等待开始执行-(gen_created)', getgeneratorstate(my_coro))
next(my_coro)
print('status ---在yeild表达式暂停(gen_suspended)', getgeneratorstate(my_coro))
my_coro.send(8) # 解析器正在执行状态（gen_running）
my_coro.close()
print('status ---执行结束(gen_close)', getgeneratorstate(my_coro))
```

运行结果：

```
status ---等待开始执行-(gen_created) GEN_CREATED
--> coroutine started...
status ---在yeild表达式暂停(gen_suspended) GEN_SUSPENDED
--> coroutine received: 8
--> coroutine started...
status ---执行结束(gen_close) GEN_CLOSED
```

总结：

协程有四种状态，可以通过inspect.getgeneratorstate\(\)查看当前协程的状态。

GEN\_CREATED:等待开始执行

GEN\_RUNNING:解析器正在执行

GEN\_SUSPENDED:在yeild表达式处暂停

GEN\_CLOSE:执行结束

 

