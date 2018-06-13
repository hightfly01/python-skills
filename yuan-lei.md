# 元类

元类：用于创建类\(对象\)的类。也可以理解为：元类就是类的类

python中提供了type\(\)内建函数来创建类。

## &lt;1&gt;type动态创建类

通过type我们可以动态的创建类。

type语法：

```
type(类名, 由父类名称组成的元组（针对继承的情况，可以为空），包含属性的字典（名称和值）)
```

如：

```
Test2 = type("Test2",(),{}) #定了一个Test2类
In [5]: Test2() #创建了一个Test2类的实例对象
Out[5]: <__main__.Test2 at 0x10d406b38>
```

以上代码：通过type动态的创建了一个Test2类。

### &lt;2&gt;使用type创建含有继承关系的类 {#4-使用type创建带有属性的类}

```
>>> Foo = type('Foo', (), {})  # 父类
```

```
>>> FooChild = type('FooChild', (Foo,),{})  # 子类 继承 Foo
```

#### 注意： {#注意：}

* type的第2个参数，元组中是_**父类的名字，而不是字符串**_

### &lt;3&gt;使用type创建带有属性的类 {#4-使用type创建带有属性的类}

type 接受一个字典来为类定义属性，因此:

```
>>> Foo = type('Foo', (), {'bar':True})
```

可以翻译为：

```
>>> class Foo(object):
…       bar = True
```

并且可以将Foo当成一个普通的类一样使用：

```
>>> print Foo
<class '__main__.Foo'>
>>> print Foo.bar
True
>>> f = Foo()
>>> print f
<__main__.Foo object at 0x8a9b84c>
>>> print f.bar
True
```

#### 注意： {#注意：}

* 添加的属性是_**类属性**_，并不是实例属性

### &lt;4&gt;使用type创建带有方法的类 {#5-使用type创建带有方法的类}

##### 添加实例方法 {#添加实例方法}

```
In [46]: def echo_bar(self): #定义了一个普通的函数
    ...:     print(self.bar)
    ...:
In [47]: FooChild = type('FooChild', (Foo,), {'echo_bar': echo_bar}) #让FooChild类中的echo_bar属性，指向了上面定义的函数

In [48]: hasattr(Foo, 'echo_bar') #判断Foo类中，是否有echo_bar这个属性
Out[48]: False
In [49]:
In [49]: hasattr(FooChild, 'echo_bar') #判断FooChild类中，是否有echo_bar这个属性
Out[49]: True

In [50]: my_foo = FooChild()

In [51]: my_foo.echo_bar()
True
```

##### 添加静态方法 {#添加静态方法}

```
In [36]: @staticmethod
    ...: def testStatic():
    ...:     print("static method ....")
    ...:

In [37]: Foochild = type('Foochild', (Foo,), {"echo_bar":echo_bar, "testStatic":testStatic})

In [38]: fooclid = Foochild()

In [39]: fooclid.testStatic
Out[39]: <function __main__.testStatic>

In [40]: fooclid.testStatic()
static method ....

In [41]: fooclid.echo_bar()
True
```

##### 添加类方法 {#添加类方法}

```
In [42]: @classmethod
    ...: def testClass(cls):
    ...:     print(cls.bar)
    ...:

In [43]:

In [43]: Foochild = type('Foochild', (Foo,), {"echo_bar":echo_bar, "testStatic":testStatic, "testClass":testClass})

In [44]:

In [44]: fooclid = Foochild()

In [45]: fooclid.testClass()
```

### 总结:

_**Python中所有的东西，注意:是指所有的东西——都是对象。这包括整数、字符串、函数以及类。它们全部都是对象，而且它们都是从一个类创建而来，这个类就是type**_。

```
>>> age = 35
>>> age.__class__ 
<type 'int'>
>>> name = 'bob'
>>> name.__class__
<type 'str'>
>>> def foo(): pass
>>>foo.__class__
<type 'function'>
>>> class Bar(object): pass
>>> b = Bar()
>>> b.__class__
<class '__main__.Bar'>
```

现在，对于任何一个\_\_class\_\_的\_\_class\_\_属性又是什么呢？

```
>>> age.__class__.__class__ # age类的类：其实就是元类（type）
<type 'type'>
>>> name.__class__.__class__ 
<type 'type'>
>>> foo.__class__.__class__
<type 'type'>
>>> b.__class__.__class__
<type 'type'>
```

因此，_**元类就是创建类这种对象的东西。type就是Python的内建元类，当然了，你也可以创建自己的元类**_。

