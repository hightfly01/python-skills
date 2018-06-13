## **+=符号说明：**

* 是**+**的一种升级版本, 具有能把执行后的结果再写回传递来的变量本身的功能

* 可变类型的变量自身有比不可变类型变量多一个魔法方法\_\__iadd_\_\_。当使用

**+=**操作首先会调用\_\__iadd_\_方法，没有该方法时，再尝试调用\_\__add_\_\_方法。

* 不可变类型变量没有\_\__iadd_\_\__方法。直接调用_\_\_add\_\_方法

#### 可变类型实现：a += a 操作

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

##### 强调说明：

对于可变类型变量进行 a += a 操作，**+=**操作会调用a.\_\_iadd\_\_\(a\)方法，直接在原对象a变量上进行更新。

#### 可变类型变量实现：a = a+a 操作

```
>>> def selfAdd(a):
...     """自增"""
...     a = a + a  # 注意这里
...
>>> a_list = [1, 2]
>>> a_list
[1, 2]
>>> selfAdd(a_list)
>>> a_list
[1, 2]      # a_list并没有累加
```

##### 强调说明：

对于可变类型变量进行 a = a + a 操作，是不会有a.\_\_iadd\_\_\(a\)方法，而是调用\_\__add_\_\_方法，返回一个新对象，原对象不做修改。因为a被重新赋值，指向了新对象a.因此原对象没有发生变化。

_**总结：对于可变类型变量进行累加操作，一定要是使用 += 运算符**_
