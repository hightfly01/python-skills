## fork\( \) {#2-fork-}

Python的os模块封装了常见的系统调用，其中就包括fork，可以在Python程序中轻松创建子进程：

```
import os
import time

num = 0

# 注意，fork函数，只在Unix/Linux/Mac上运行，windows不可以
pid = os.fork()

if pid == 0:
    num+=1
    print('哈哈1---num=%d'%num)
    print("我是子进程（%s），我的父进程是（%s）"%(os.getpid(),os.getppid()))
else:
    time.sleep(1)
    num+=1
    print('哈哈2---num=%d'%num)
    print("我是父进程（%s），我的子进程是（%s）"%(os.getpid(),rpid))
```

说明：

* ##### 程序执行到os.fork\(\)时，操作系统会创建一个新的进程（子进程），然后复制父进程的所有信息到子进程中
* ##### 然后父进程和子进程都会从fork\(\)函数中得到一个返回值，在子进程中这个值一定是0，而父进程中是子进程的 id号。因此，`子进程永远返回0，而父进程返回子进程的ID`。
* ##### getpid\(\):获取当前进程的ID。getppid\(\)：获取当前进程父进程的ID.
* ##### 多进程中，每个进程中所有数据（包括全局变量）都各有拥有一份，互不影响。
* ##### 父进程、子进程执行顺序没有规律，完全取决于操作系统的调度算法

## 多次fork\(\)

多次fork\(\)多个进程时的，序列图：![](/assets/Snip20180227_4.png)

