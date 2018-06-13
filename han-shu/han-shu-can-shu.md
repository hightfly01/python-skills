## &lt;1&gt; 定义带有参数的函数 {#定义带有参数的函数}

```
    def add2num(a, b):
        c = a+b
        print c
```

## &lt;2&gt; 调用带有参数的函数 {#调用带有参数的函数}

```
    def add2num(a, b):
        c = a+b
        print c

    add2num(11, 22) #调用带有参数的函数时，需要在小括号中，传递数据
```

## 注意 {#小总结}

* 定义时小括号中的参数，用来接收参数用的，称为 “形参”
* 调用时小括号中的参数，用来传递给函数用的，称为 “实参”

## &lt;3&gt; 缺省参数 {#1-缺省参数}

**调用函数时，缺省参数的值如果没有传入**，则被认为是默认值。

下例会打印默认的age，如果age没有被传入：

```
def printinfo( name, age = 35 ):
   # 打印任何传入的字符串
   print "Name: ", name
   print "Age ", age

# 调用printinfo函数
printinfo(name="miki" )
printinfo( age=9,name="miki" )
```

#### 注意：带有默认值的参数一定要位于参数列表的最后面。 {#注意：带有默认值的参数一定要位于参数列表的最后面。}

```
>>> def printinfo(name, age=35, sex):
...     print name
...
  File "<stdin>", line 1
SyntaxError: non-default argument follows default argument
```

## &lt;4&gt;不定长参数 {#2不定长参数}

函数能处理比当初声明时更多的参数且声明时不会命名，这些参数叫做不定长参数

基本语法：

```
    def functionname([formal_args,] *args, **kwargs):
       "函数_文档字符串"
       function_suite
       return [expression]
```

#### 强调说明：

**加了星号（\*）的变量args会存放所有未命名的变量参数，args为元组**；

**而加\*\*的变量kwargs会存放命名参数，即形如key=value的参数， kwargs为字典**。

如：

```
>>> def fun(a, b, *args, **kwargs):
...     """可变参数演示示例"""
...     print "a =", a
...     print "b =", b
...     print "args =", args
...     print "kwargs: "
...     for key, value in kwargs.items():
...         print key, "=", value
...
>>> fun(1, 2, 3, 4, 5, m=6, n=7, p=8)  # 注意传递的参数对应
```

#### 对参数为元组和字典进行拆包

```
>>> def fun(a, b, *args, **kwargs):
...     """可变参数演示示例"""
...     print "a =", a
...     print "b =", b
...     print "args =", args
...     print "kwargs: "
...     for key, value in kwargs.items():
...         print key, "=", value
...
>>> A=(3,4,5)
>>> B={m=6,n=7,p=8}
>>> fun(1, 2, *A,**B)  # 对A元组和B字典进行拆包
```

## &lt;5&gt;引用传参 {#3-引用传参}

**Python中函数参数是引用传递（注意不是值传递）。**

**对于不可变类型，因变量不能修改，所以运算不会影响到变量自身；**

**而对于可变类型来说，函数体中的运算有可能会更改传入的参数变量。**

如：

参数为：不可变类型

```
>>> def selfAdd(a):
...     """自增"""
...     a += a   
...
>>> a_int = 1
>>> a_int
1
>>> selfAdd(a_int)
>>> a_int
1
```

参数为：可变类型

```
>>> def selfAdd(a):
...     """自增"""
...     a += a   
...
>>> a_list = [1, 2]
>>> a_list
[1, 2]
>>> selfAdd(a_list)
>>> a_list
[1, 2, 1, 2]
```



