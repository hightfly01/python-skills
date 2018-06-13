# 多线程-threading {#多线程threading}

python的thread模块是比较底层的模块，python的threading模块是对thread做了一些包装的，可以更加方便的被使用。

```
#coding=utf-8
import threading
from time import sleep,ctime

def sing():
    for i in range(3):
        print("正在唱歌...%d"%i)
        sleep(1)

def dance():
    for i in range(3):
        print("正在跳舞...%d"%i)
        sleep(1)

if __name__ == '__main__':
    print('---开始---:%s'%ctime())

    t1 = threading.Thread(target=sing)
    t2 = threading.Thread(target=dance)

    t1.start()
    t2.start()

    #sleep(5) # 屏蔽此行代码，试试看，程序是否会立马结束？
    print('---结束---:%s'%ctime())
```

说明：

* 可以明显看出使用了多线程并发的操作，花费时间要短很多

* 创建好的线程，需要调用`start()`方法来启动
* 主线程会等待所有的子线程结束后才结束



