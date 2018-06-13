# 多态 {#多态}

多态的概念是应用于Java和C\#这一类强类型语言中，而Python崇尚“鸭子类型”。

所谓多态：定义时的类型和运行时的类型不一样，此时就成为多态。

```
java中的多态：

定义：父类引用指向子类对象。也就是指在执行期间判断所引用对象的实际类型，根据其实际的类型调用其相应的方法

实现多态的技术称为：
    动态绑定（dynamic binding），是指在执行期间判断所引用对象的实际类型，根据其实际的类型调用其相应的方法。

多态存在的三个必要条件：
    一、要有继承；
    二、要有重写；
    三、父类引用指向子类对象。

多态的作用：
    消除类型之间的耦合关系。

多态的好处：

    可扩充性：多态对代码具有可扩充性。增加新的子类不影响已存在类的多态性、继承性，以及其他特性的运行和操作
```

## python中的多态\(鸭子类型\)

```
class F1(object):
    def show(self):
        print 'F1.show'

class S1(F1):

    def show(self):
        print 'S1.show'

class S2(F1):

    def show(self):
        print 'S2.show'

def Func(obj): # 多态的实现
    print obj.show()

s1_obj = S1()
Func(s1_obj) 

s2_obj = S2()
Func(s2_obj)
```



