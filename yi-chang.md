# 异常

### 定义**:**

> 当Python检测到一个错误时，解释器就无法继续执行了，反而出现了一些错误的提示，这就是所谓的"异常"

### 捕获异常

异常捕获格式：

```
try:
    pass # 执行代码块
except expression as identifier: # 捕获到异常。expression：异常类型   identifier：异常信息
    pass
else: # 没有异常信息
    pass
finally: # 是否有异常，最终都会执行finally语句
    pass
```

### 捕获多个异常

```
try:
     # 执行代码块     
     num = 100/0
except (NameError, ValueError,ZeroDivisionError) as identifier: # 捕获到异常。expression：异常类型   identifier：异常信息
    print('异常信息:%s'%identifier)
else: # 没有异常信息
     print('未发现异常信息')
finally: # 是否有异常，最终都会执行finally语句
   print('finally')
```

### 全局异常捕获

```
try:
     # 执行代码块     
     num = 100/0
except Exception as identifier: # 捕获到异常。expression：异常类型   identifier：异常信息
    print('异常信息:%s'%identifier)
else: # 没有异常信息
     print('未发现异常信息')
finally: # 是否有异常，最终都会执行finally语句
   print('finally')
```

### try嵌套

```
try:
     # 执行代码块     
   try:
      num = 100 / 0
   finally:
       pass

except Exception as identifier: # 捕获到异常。expression：异常类型   identifier：异常信息
    print('异常信息:%s'%identifier)
else: # 没有异常信息
     print('未发现异常信息')
finally: # 是否有异常，最终都会执行finally语句
   print('finally')
```

总结：

* 如果try嵌套，那么如果里面的try没有捕获到这个异常，那么外面的try会接收到这个异常，然后进行处理，如果外边的try依然没有捕获到，那么再进行传递。。。

### 异常传递

```
def test():
    num = 100 / 0

try:
     # 执行代码块     
    test()
except Exception as identifier: # 捕获到异常。expression：异常类型   identifier：异常信息
    print('异常信息:%s'%identifier)
else: # 没有异常信息
     print('未发现异常信息')
finally: # 是否有异常，最终都会执行finally语句
   print('finally')
```

总结：

* 如果一个异常是在一个函数中产生的，例如函数A----&gt;函数B----&gt;
  函数C,而异常是在函数C中产生的，那么如果函数C中没有对这个异常进行处理，那么这个异常会传递到函数B中，如果函数B有异常处理那么就会按照函数B的处理方式进行执行；如果函数B也没有异常处理，那么这个异常会继续传递，以此类推。。。如果所有的函数都没有处理，那么此时就会进行异常的默认处理，即通常见到的那样

### 抛出自定义异常

可以用raise语句来引发一个异常。异常/错误对象必须有一个名字，且它们应是Error或Exception类的子类

```
class MyException(Exception): # 定义的类需要继承Exception
    '''自定义的异常类'''
    def __init__(self, message):
        #super().__init__()
        self.info = message

try:
     # 执行代码块     

    # 抛出自定义异常信息
    raise MyException('自定义异常') 

except Exception as identifier: # 捕获到异常。expression：异常类型   identifier：异常信息
    print('异常信息:%s'%identifier)
else: # 没有异常信息
     print('未发现异常信息')
finally: # 是否有异常，最终都会执行finally语句
   print('finally')
```

### 异常处理中抛出异常

```
class Test(object):
    def __init__(self, switch):
        self.switch = switch #开关
    def calc(self, a, b):
        try:
            return a/b
        except Exception as result:
            if self.switch:
                print("捕获开启，已经捕获到了异常，信息如下:")
                print(result)
            else:
                #重新抛出这个异常，此时就不会被这个异常处理给捕获到，从而触发默认的异常处理
                raise

a = Test(True)
a.calc(11,0)
```



