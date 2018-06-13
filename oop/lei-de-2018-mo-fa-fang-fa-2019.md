# 常见类的魔法方法

## &lt;1&gt;  `__init__()方法`

### 特征和作用：

* `__init__(self)`方法，在创建一个对象时默认被调用，不需要手动调用
* `__init__(self)`中，默认有1个参数名字为self，如果在创建对象时传递了2个实参，那么`__init__(self)`中出了self作为第一个形参外还需要2个形参，例如`__init__(self,x,y)`
* `__init__(self)`中的self参数，不需要开发者传递，python解释器会自动把当前的对象引用传递进去

### 使用方式

```
def 类名:
    #初始化函数，用来完成一些默认的设定
    def __init__():
        pass
```

### `__init__()`方法的调用

```
# 定义汽车类
class Car:

    def __init__(self):
        self.wheelNum = 4
        self.color = '蓝色'

    def move(self):
        print('车在跑，目标:夏威夷')

# 创建对象
BMW = Car()

print('车的颜色为:%s'%BMW.color)
print('车轮胎数量为:%d'%BMW.wheelNum)
```

# &lt;2&gt; `__str__()`方法

### 作用：

* 当使用print输出对象的时候，只要自己定义了`__str__(self)`方法，那么就会打印从在这个方法中return的数据

### 定义`__str__(self)`

```
class Car:

    def __init__(self, newWheelNum, newColor):
        self.wheelNum = newWheelNum
        self.color = newColor

    def __str__(self):
        msg = "嘿。。。我的颜色是" + self.color + "我有" + int(self.wheelNum) + "个轮胎..."
        return msg

    def move(self):
        print('车在跑，目标:夏威夷')


BMW = Car(4, "白色")
print(BMW)
```

# &lt;3&gt; `__del__()`方法

### 作用：

当删除一个对象时，python解释器也会默认调用一个方法，这个方法为`__del__()`方法

### 定义`__del__()`方法：

```
import time
class Animal(object):

    # 初始化方法
    # 创建完对象后会自动被调用
    def __init__(self, name):
        print('__init__方法被调用')
        self.__name = name

    # 当对象被删除时，会自动被调用
    def __del__(self):
        print("__del__方法被调用")
        print("%s对象马上被干掉了..."%self.__name)

# 创建对象
dog = Animal("哈皮狗")
# 删除对象
del dog
```

# &lt;3&gt;`__new__()`方法 {#new方法}

### 作用和特征：

* `__new__`至少要有一个参数cls，代表要实例化的类，此参数在实例化时由Python解释器自动提供

* `__new__`必须要有返回值，返回实例化出来的实例，这点在自己实现`__new__`时要特别注意，可以return父类`__new__`出来的实例，或者直接是object的`__new__`出来的实例

* `__init__`有一个参数self，就是这个`__new__`返回的实例，`__init__`在`__new__`的基础上可以完成一些其它初始化的动作，`__init__`不需要返回值

* 我们可以将类比作制造商，`__new__`方法就是前期的原材料购买环节，`__init__`方法就是在有原材料的基础上，加工，初始化商品环节

### `__new__的定义`

```
class A(object):
    def __init__(self):
        print("这是 init 方法")

    def __new__(cls):
        print("这是 new 方法")
        return object.__new__(cls)

A()
```



