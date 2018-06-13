# 类的私有实例属性和方法的定义

```
class Animal(object):

    def __init__(self, name='动物', color='白色'):
        self.__name = name # 私有属性
        self.color = color

    def __test(self): # 私有方法
        print(self.__name)
        print(self.color)

    def test(self):
        print(self.__name)
        print(self.color)


A = Animal()
#print(A.__name) #程序出现异常，不能访问私有属性
print(A.color)
#A.__test() #程序出现异常，不能访问私有方法
A.test()
```

注意事项：

* 私有的属性，不能通过对象直接访问，但是可以通过方法访问

* 私有的方法，不能通过对象直接访问

* 私有的属性、方法，不会被子类继承，也不能被访问

* 一般情况下，私有的属性、方法都是不对外公布的，往往用来做内部的事情，起到安全的作用



