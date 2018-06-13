# 模块制作 {#模块制作}

### &lt;1&gt;定义自己的模块

在Python中，每个Python文件都可以作为一个模块，模块的名字就是文件的名字。

比如有这样一个文件Test.py，在Test.py中定义了函数add

```
    def add(a,b):
        return a+b
```

### &lt;2&gt;调用自己定义的模块

那么在其他文件中就可以先import test，然后通过test.add\(a,b\)来调用了，当然也可以通过from test import add来引入

```
    import Test
    result = Test.add(11,22)
    print(result)
```

## &lt;3&gt;测试模块 {#测试模块}

Test.py: 模块

```
def add(a, b): # 模块中的函数
    return a+b


def main(): # 测试模块中函数是否正确
    ret = add(10, 20)
    print('a+b = %d'%ret)

if __name__ == '__main__': # 测试入口函数。只有开发者进行测试时执行，发布之后，不会执行
    main()
```

## &lt;4&gt;导出指定模块中的元素 {#测试模块}

可以通过`__all__`变量，导出指定模块中的元素

如：

```
#如果一个模块中有__all__变量，那么也就意味着这个变量中的元素，不会被from xxx import * 时导入
__all__=['add', 'Person', 'test1']

def add(a, b):
    return a+b

class Person(object):
    def test(self):
        pass
def test1():
    pass

def test2():
    pass

def main():
    ret = add(10, 20)
    print('a+b = %d'%ret)

if __name__ == '__main__':
    main()
```

注意事项：

**如果使用from Test import \* 导入模块中的所有元素时，此时\_\_all\_\_ 变量就会生效。**

**如果 import Test 直接导入模块，此时\_\_all\_\_ 变量就不再生效**

## &lt;5&gt;发布模块 {#测试模块}

#### 编辑setup.py文件：

py\_modules需指明所需包含的py文件

```
from distutils.core import setup
# py_modules:指定模块名
setup(name="modules", version="1.0", description="Test module", author="test", py_modules=['Test')
```

#### 构建模块

命令： python setup.py build

构建后目录结构：

![](/assets/Snip20180208_2.png)

#### 生成发布压缩包

命令： python setup.py sdist

打包后,生成最终发布压缩包Test-1.0.tar.gz , 目录结构

![](/assets/Snip20180208_3.png)

## &lt;6&gt;模块安装、使用

#### 1.安装的方式

1. 找到模块的压缩包
2. 解压
3. 进入文件夹
4. 执行命令
   `python setup.py install`

注意：

* 如果在install的时候，执行目录安装，可以使用
  `python setup.py install --prefix=安装路径`

#### 2.模块的引入

在程序中，使用from import 即可完成对安装的模块使用

`from 模块名 import 模块名或者*`

```
ywfdeMBP:dist ywf$ tar -xvf modules-1.0.tar.gz  # 解压
x modules-1.0/
x modules-1.0/PKG-INFO
x modules-1.0/Test.py
x modules-1.0/setup.py
ywfdeMBP:dist ywf$ cd modules-1.0 # 进入解压轴的目录
ywfdeMBP:modules-1.0 ywf$ ls
PKG-INFO        Test.py         setup.py

ywfdeMBP:modules-1.0 ywf$ python setup.py install # 执行安装
running install
running build
running build_py
creating build
creating build/lib
copying Test.py -> build/lib
running install_lib
copying build/lib/Test.py -> /Library/Frameworks/Python.framework/Versions/3.6/lib/python3.6/site-packages
byte-compiling /Library/Frameworks/Python.framework/Versions/3.6/lib/python3.6/site-packages/Test.py to Test.cpython-36.pyc
running install_egg_info
Writing /Library/Frameworks/Python.framework/Versions/3.6/lib/python3.6/site-packages/modules-1.0-py3.6.egg-info
ywfdeMBP:modules-1.0 ywf$
```

安装成功之后的模块目录：

```
/Library/Frameworks/Python.framework/Versions/3.6/lib/python3.6/site-packages/modules-1.0-py3.6.egg-info
```

#### 3.模块的使用

```
 # from Test import * # 导入定义的模块
import Test 
result = Test.add(10, 10)
print (result)
```



