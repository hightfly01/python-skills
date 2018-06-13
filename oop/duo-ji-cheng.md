# 多继承

定义：子类有多个父类，并且具有它们的特征

Python中多继承的格式如下:

```
# 定义一个父类
class A:
    def printA(self):
        print('----A----')

# 定义一个父类
class B:
    def printB(self):
        print('----B----')

# 定义一个子类，继承自A、B
class C(A,B):
    def printC(self):
        print('----C----')

obj_C = C()
obj_C.printA()
obj_C.printB()
```

#### 说明 {#说明}

* python中是可以多继承的
* 父类中的方法、属性，子类会继承



