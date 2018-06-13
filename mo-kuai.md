# 模块

定义：

说的通俗点：模块就好比是工具包，要想使用这个工具包中的工具\(就好比函数\)，就需要导入这个模块

### 导入模块：

在Python中用关键字`import`来引入某个模块，比如要引用模块math，就可以在文件最开始的地方用import math来引入。

如：

```
 import module1,mudule2...
```

当解释器遇到import语句，如果模块在当前的搜索路径就会被导入。

在调用模块中的函数时，必须这样引用：

```
模块名.函数名
```

比如：

```
    import math
    #这样才能正确输出结果
    print math.sqrt(2)
```

### 导入模块中某个或者多个函数

有时候我们只需要用到模块中的某个函数，只需要引入该函数即可，此时可以用下面方法实现：

```
from 模块名 import 函数名1,函数名2....
```

例如，要导入模块fib的fibonacci函数，使用如下语句：

```
    from fib import fibonacci
```

##### 注意

* 不会把整个fib模块导入到当前的命名空间中，它只会将fib里的fibonacci单个引入

### 导入模块中的所有内容

把一个模块的所有内容全都导入到当前的命名空间也是可行的，只需使用如下声明：

```
 from modname import *
```

### 导入的模块定义别名

使用**as**关键字：

```
    In [1]: import time as tt # time模块定义了一个别名。通过别名调用函数

    In [2]: time.sleep(1)
    ---------------------------------------------------------------------------
    NameError                                 Traceback (most recent call last)
    <ipython-input-2-07a34f5b1e42> in <module>()
    ----> 1 time.sleep(1)

    NameError: name 'time' is not defined

    In [3]: tt.sleep(1)
```

### 定位模块

当你导入一个模块，Python解析器对模块位置的搜索顺序是：

1. 当前目录
2. 如果不在当前目录，Python则搜索在shell变量PYTHONPATH下的每个目录。
3. 如果都找不到，Python会察看默认路径。UNIX下，默认路径一般为/usr/local/lib/python/
4. 模块搜索路径存储在system模块的sys.path变量中。变量里包含当前目录，PYTHONPATH和由安装过程决定的默认目录。



