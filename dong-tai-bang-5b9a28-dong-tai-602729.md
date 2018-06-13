# python是动态语言-动态绑定 {#python是动态语言}

```
动态语言： 程序在运行时可以改变其结构的语言
```

### &lt;1&gt;运行的过程中给类绑定\(添加\)`实例`属性 {#2-运行的过程中给对象绑定添加属性}

```
>>> class Person(object):
    def __init__(self, name = None, age = None):
        self.name = name
        self.age = age

>>> P = Person("小明", "24")
>>> P.sex = "male"   # sex属性动态绑定
>>> P.sex
'male'
>>>
```

### &lt;2&gt;运行的过程中给类绑定\(添加\)`类`属性 {#3-运行的过程中给类绑定添加属性}

```
>>> class Person(object):
    def __init__(self, name = None, age = None):
        self.name = name
        self.age = age

>>>> Person.sex = None #给类Person添加一个属性
>>> P1 = Person("小丽", "25")
>>> print(P1.sex) #如果P1这个实例对象中没有sex属性的话，那么就会访问它的类属性
None #可以看到没有出现异常
>>>
```

### &lt;3&gt;运行的过程中给类绑定\(添加\)&lt;实例/静态/类&gt;方法 {#4-运行的过程中给类绑定添加方法}

```
import types  # 导入types模块

#定义了一个类
class Person(object):
    num = 0
    def __init__(self, name = None, age = None):
        self.name = name
        self.age = age
    def eat(self):
        print("eat food")

#定义一个实例方法
def run(self, speed):
    print("%s在移动, 速度是 %d km/h"%(self.name, speed))

#定义一个类方法
@classmethod
def testClass(cls):
    cls.num = 100

#定义一个静态方法
@staticmethod
def testStatic():
    print("---static method----")

#创建一个实例对象
P = Person("老王", 24)
#调用在class中的方法
P.eat()

#给这个对象添加实例方法
P.run = types.MethodType(run, P)
#调用实例方法
P.run(180)

#给Person类绑定类方法
Person.testClass = testClass
#调用类方法
print(Person.num)
Person.testClass()
print(Person.num)

#给Person类绑定静态方法
Person.testStatic = testStatic
#调用静态方法
Person.testStatic()
```

注意：

_**想要给类动态绑定**_`实例`_**方法，需要types模块下的MethodType\(\)方法，进行动态绑定。**_

_**静态/类方法,只需要赋值操作就可以了**_



