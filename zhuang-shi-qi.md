# 装饰器

#### 定义

在代码运行期间动态增加功能的方式，称之为“装饰器”（Decorator）。

#### 使用场景\(功能\)：

1. 引入日志
2. 函数执行时间统计
3. 执行函数前预备处理
4. 执行函数后清理功能
5. 权限校验等场景
6. 缓存
7. 用户登录验证机制

#### 装饰器分类：

1. 函数装饰器
2. 类装饰器

## 函数装饰器

装饰器函数其实是这样一个接口约束，它必须接受一个callable对象作为参数，然后返回一个callable对象。

### &lt;1&gt; 被装饰的有参函数 {#例2被装饰的函数有参数}

```
from time import ctime, sleep

def timefun(func):
    def wrappedfunc(a, b):
        print("%s called at %s"%(func.__name__, ctime()))
        print(a, b)
        func(a, b)
    return wrappedfunc

@timefun
def foo(a, b):
    print(a+b)

foo(3,5)
```

强调：装饰器的调用过程：

```
foo = timefun(foo)
#foo函数先作为实参赋值给timefun函数的func后。
#foo变量接收指向timefun函数返回的wrappedfunc
foo()
#调用foo(),即等价调用wrappedfunc()
#内部函数wrappedfunc被引用，所以外部函数的func变量(自由变量)并没有释放
#func里保存的是原foo函数对象
```

### &lt;2&gt; 被装饰的不定长参数函数 {#例2被装饰的函数有参数}

```
from time import ctime, sleep

def timefun(func):
    def wrappedfunc(*args, **kwargs):
        print("%s called at %s"%(func.__name__, ctime()))
        func(*args, **kwargs)
    return wrappedfunc

@timefun
def foo(a, b, c):
    print(a+b+c)

foo(3,5,7)
```

### &lt;3&gt;装饰器中的return {#例4装饰器中的return}

装饰器\(内部函数\),没有使用return 返回函数：

```
from time import ctime, sleep

def timefun(func):
    def wrappedfunc():
        print("%s called at %s"%(func.__name__, ctime()))
        func()
    return wrappedfunc

@timefun
def getInfo():
    return '----hahah---'


print(getInfo()) # 调用被装饰的函数
```

打印结果：

```
getInfo called at Fri Nov  4 21:55:37 2016
None  # 如果没有return 并不会打印出内容
```

装饰器\(内部函数\),使用`return func()` 返回函数：

```
from time import ctime, sleep

def timefun(func):
    def wrappedfunc():
        print("%s called at %s"%(func.__name__, ctime()))
        return func()
    return wrappedfunc

@timefun
def getInfo():
    return '----hahah---'

print(getInfo()) # 调用被装饰的函数
```

打印结果：

```
getInfo called at Fri Nov  4 21:55:59 2016
----hahah---   #修改装饰器为return func()，就可以打印出相应的内容
```

#### 总结： {#总结：}

* 一般情况下为了让装饰器更通用，可以有return

### &lt;3&gt;含有参数的装饰器 {#例4装饰器中的return}

```
from time import ctime, sleep

def timefun_arg(pre="hello"):
    def timefun(func):
        def wrappedfunc():
            print("%s called at %s %s"%(func.__name__, ctime(), pre))
            return func()
        return wrappedfunc
    return timefun

@timefun_arg("python")
def too():
    print("I am too")

foo() # 调用(可以理解为：foo()==timefun_arg("python")(foo)())
```

## 类装饰器

我们知道，装饰器其实就是对一个接口的约束，必须接受一个callable对象作为参数，然后返回一个callable对象。

python解析器就会调用返回的callable对象。并且callable对象内部实现了`__call__()`方法。

如果让一个类成为callable对象，我们只需要类重写`__call__()`方法,即可。

```
class Test(object):
    def __init__(self, func):
        print("---初始化---")
        print("func name is %s"%func.__name__)
        self.__func = func
    def __call__(self):
        print("---装饰器中的功能---")
        self.__func()


@Test
def test():
    print("----test---")
test()
showpy()#如果把这句话注释，重新运行程序，依然会看到"--初始化--"
```

说明：

```
#说明：
#1. 当用Test来装作装饰器对test函数进行装饰的时候，首先会创建Test的实例对象
#    并且会把test这个函数名当做参数传递到__init__方法中
#    即在__init__方法中的func变量指向了test函数体
#
#2. test函数相当于指向了用Test创建出来的实例对象
#
#3. 当在使用test()进行调用时，就相当于让这个对象()，因此会调用这个对象的__call__方法
#
#4. 为了能够在__call__方法中调用原来test指向的函数体，所以在__init__方法中就需要一个实例属性来保存这个函数体的引用
#    所以才有了self.__func = func这句代码，从而在调用__call__方法中能够调用到test之前的函数体
```



