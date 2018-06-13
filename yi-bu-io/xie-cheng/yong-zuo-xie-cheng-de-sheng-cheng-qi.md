```
def simple_coroutine():# 协程使用生成器定义：定义体中有yeild关键字
    print('--> coroutine started...')
    x = yield #在表达式中使用，如果协程只需要从客户那里接收数据，那么产出的值是None--这个值是隐式指定的。
              #因为yeild关键字右边没有表达式。
    print('--> coroutine received:', x)


my_coro = simple_coroutine()
next(my_coro) # 启动生成器。因为没在yeild语句暂停，一开始是无法发送数据。
my_coro.send(4)# 向协程送数据，协程定义体中的yeild表达式会计算出4，并赋值给x。协程会恢复，一直运行到下一个yeild表达式，或终止。
```

打印结果：

```
--> coroutine started...
--> coroutine received: 4
  File "/Users/ywf/Desktop/process/simple_coroutine.py", line 11, in <module>
    my_coro.send(4)
StopIteration
```



