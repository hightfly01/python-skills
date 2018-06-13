# 属性property {#属性property}

### 1. 私有属性添加getter和setter方法 {#1-私有属性添加getter和setter方法}

```
class Money(object):
    def __init__(self):
        self.__money = 0

    def getMoney(self):
        return self.__money

    def setMoney(self, value):
        if isinstance(value, int):
            self.__money = value
        else:
            print("error:不是整型数字")
```

### 3. 使用property取代getter和setter方法 {#3-使用property取代getter和setter方法}

`@property`成为属性函数，可以对属性赋值时做必要的检查，并保证代码的清晰短小，主要有2个作用

* 将方法转换为只读
* 重新实现一个属性的设置和读取方法,可做边界判定

```
class Money(object):
    def __init__(self):
        self.__money = 0

    @property
    def money(self):
        return self.__money

    @money.setter
    def money(self, value):
        if isinstance(value, int):
            self.__money = value
        else:
            print("error:不是整型数字")
```

运行结果：

```
In [3]: a = Money()

In [4]: 

In [4]: 

In [4]: a.money
Out[4]: 0

In [5]: a.money = 100

In [6]: a.money
Out[6]: 100
```



