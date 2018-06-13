qqqq

```
class DemoException(Exception):
    """An exception type for the demonstration."""


def demo_finally():
    print('-> coroutine started')
    try:
        while True:
            try:
                x = yield
            except DemoException:
                print('*** DemoException handled. Continuing...')
            else:
                print('-> coroutine received: {!r}'.format(x))
    finally: # 不管协程如何结束，做清理工作。
        print('-> coroutine ending')


fin_coro = demo_finally()
next(fin_coro)
fin_coro.send(11)
fin_coro.send(12)

fin_coro.throw(DemoException) 

fin_coro.close()
```

打印结果：

```
-> coroutine started
-> coroutine received: 11
-> coroutine received: 12
*** DemoException handled. Continuing...
-> coroutine ending
```



