# 单继承

定义：子类只能继承一个父类

如：

```
# 定义一个父类，如下:
class Cat(object):

    def __init__(self, name, color="白色"):
        self.name = name
        self.color = color

    def run(self):
        print("%s--在跑"%self.name)

# 定义一个子类，继承Cat类如下:
class Bosi(Cat):

    def setNewName(self, newName):
        self.name = newName

    def eat(self):
        print("%s--在吃"%self.name)
```

#### 总结 {#总结}

* 子类在继承的时候，在定义类时，小括号\(\)中为父类的名字
* 父类的属性、方法，会被继承给子类

# 子类无法继承父类的私有属性和私有方法

如：

```
class Animal(object):
    def __init__(self, name='动物', color='白色'):
        self.__name = name
        self.color = color

    def __test(self):
        print(self.__name)
        print(self.color)

    def test(self):
        print(self.__name)
        print(self.color)

class Dog(Animal):
    def dogTest1(self):
        #print(self.__name) #不能访问到父类的私有属性
        print(self.color)


    def dogTest2(self):
        #self.__test() #不能访问父类中的私有方法
        self.test()

A = Animal()
#print(A.__name) #程序出现异常，不能访问私有属性
print(A.color)
#A.__test() #程序出现异常，不能访问私有方法
A.test()
```

总结：

* 私有的属性，不能通过对象直接访问，但是可以通过方法访问

* 私有的方法，不能通过对象直接访问
* 私有的属性、方法，不会被子类继承，也不能被访问
* 一般情况下，私有的属性、方法都是不对外公布的，往往用来做内部的事情，起到安全的作用



