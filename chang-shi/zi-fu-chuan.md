### 字符串的输出

```
    name = '新锐'
    print('--------------------------------------------------')
    print("姓名：%s"%name)
    print('--------------------------------------------------')
```

### 字符串的输入

```
    userName = input('请输入用户名:')
    print("用户名为：%s"%userName)
```

注意：input获取的数据，都以字符串的方式进行保存，即使输入的是数字，那么也是以字符串方式保存

### 字符串的小标和切片

#### "下标"的使用

**字符串：实际上就是字符的数组，所以也支持下标索引。**

如：

```
   name = 'abcdef'
   print(name[0])
   print(name[1])
   print(name[2])
```

#### 切片的使用

切片是指对操作的对象截取其中一部分的操作。**字符串、列表、元组**都支持切片操作。

#### 切片的语法：\[起始:结束:步长\] {#切片的语法：起始结束步长}

**注意：选取的区间属于左闭右开型，即从"起始"位开始，到"结束"位的前一位结束（不包含结束位本身\)。**

如：

```
>>> name = 'abcdef'
>>> print(name[0:3]) # 取 下标0~2 的字符
```

```
 >>> a = "abcdef"
 >>> a[:3] #下标0开始，去0-3的字符
 'abc'
```

```
 >>> a = "abcdef"
 >>> a[::2] #取0-最后的字符，且步长为2
 'ace'
```

```
 >>> a = "abcdef"
 >>> a[::-2] # 取 从右边 下标为：-1 到 最左边 ，且步长为2的值 
 'fdb'
```

```
>>> a='abcdfe'
>>> a[::-1] # 反转字符串
'efdcba'
```

### 字符串常见的操作函数

#### &lt;1&gt;find {#find}

作用：检测 str 是否包含在 mystr中，如果是返回开始的索引值，否则返回-1

```
In [10]: name='hellow fly'

In [11]: name.find('fly',0, len(name))
Out[11]: 7

In [12]: name.find('ywf',0, len(name))
Out[12]: -1
```

#### &lt;2&gt;index {#index}

跟find\(\)方法一样，只不过如果str不在 mystr中会报一个异常.

如：

```
In [10]: name='hellow fly'

In [13]: name.index('ywf',0, len(name))
---------------------------------------------------------------------------
ValueError                                Traceback (most recent call last)
<ipython-input-13-584e280768fb> in <module>()
----> 1 name.index('ywf',0, len(name))

ValueError: substring not found

In [14]:
```

#### &lt;3&gt;count {#count}

返回 str在字符串start和end之间出现的次数

```
In [10]: name='hellow fly'
In [14]: name.count('ywf',0, len(name))
Out[14]: 0
In [15]: name.count('fly',0, len(name))
Out[15]: 1
```

#### &lt;4&gt;replace {#replace}

把 mystr 中的 str1 替换成 str2,如果 count 指定，则替换不超过 count 次.

```
In [10]: name='hellow fly'
In [16]: name.replace('fly','ywf', name.count('fly'))
Out[16]: 'hellow ywf'
```

#### &lt;5&gt;split {#split}

以 str 为分隔符切片 mystr，如果 maxsplit有指定值，则仅分隔 maxsplit 个子字符串

```
In [20]: name='yuan wen fei'

In [21]: name.split(' ') # 以空格(' ')进行分隔
Out[21]: ['yuan', 'wen', 'fei']

In [22]: name.split(' ',1) # 以空格(' ')进行分隔，且最大分隔次数1
Out[22]: ['yuan', 'wen fei']

In [23]: name.split('',1) # 字符串中未找到要分隔的字符，抛出异常
---------------------------------------------------------------------------
ValueError                                Traceback (most recent call last)
<ipython-input-23-20ac7dc6cace> in <module>()
----> 1 name.split('',1)

ValueError: empty separator

In [24]:
```

#### 注意： {#capitalize}

如果字符串中包含 '  ' 或者  \t 或者  \n 特殊字符时：可以直接使用myStr.split\(\)进行分隔，生产一个新的列表返回。

**在不传递任何分隔字符时，split\(\)函数默认会以' ' 或者 \t 或者 \n 进行分隔。**

```
In [116]: name='123 456\t 789\n abc\t\n fly\t\n'
In [117]: name.split() # split()方法中不需要传递任何特殊字符。
Out[117]: ['123', '456', '789', 'abc', 'fly']

In [118]:
```

#### &lt;6&gt;capitalize {#capitalize}

字符串的第一个字符大写

```
In [20]: name='yuan wen fei'
In [25]: name.capitalize()
Out[25]: 'Yuan wen fei'
```

#### &lt;7&gt;title {#title}

把字符串的每个单词首字母大写

```
In [20]: name='yuan wen fei'
In [26]: name.title()
Out[26]: 'Yuan Wen Fei'
```

#### &lt;8&gt;startswith {#startswith}

检查字符串是否是以 obj 开头, 是则返回 True，否则返回 False

```
In [20]: name='yuan wen fei'
In [28]: name.startswith('yuan')
Out[28]: True
```

#### &lt;9&gt;endswith {#endswith}

检查字符串是否以obj结束，如果是返回True,否则返回 False.

```
In [20]: name='yuan wen fei'

In [29]: name.endswith('fei')
Out[29]: True

In [30]: name.endswith('fei2')
Out[30]: False
```

#### &lt;10&gt;lower {#lower}

将 字符串 中所有大写字符转换为小写

```
In [32]: name='yuan WEN fei'

In [33]: name.lower()
Out[33]: 'yuan wen fei'

In [34]:
```

#### &lt;11&gt;upper {#upper}

将 字符串 中所有小写字符转换为大写

```
In [32]: name='yuan WEN fei'

In [34]: name.upper()
Out[34]: 'YUAN WEN FEI'

In [35]:
```

#### &lt;12&gt;ljust {#ljust}

返回一个原字符串左对齐,并使用空格填充至长度 width 的新字符串

```
In [36]: name='hello world python'

In [39]: name.ljust(25)
Out[39]: 'hello world python       '

In [40]:
```

#### &lt;13&gt;rjust {#rjust}

返回一个原字符串右对齐,并使用空格填充至长度 width 的新字符串

```
In [36]: name='hello world python'


In [40]: name.rjust(25)
Out[40]: '       hello world python'

In [41]:
```

#### &lt;14&gt;center {#center}

返回一个原字符串居中,并使用空格填充至长度 width 的新字符串

```
In [36]: name='hello world python'


In [41]: name.center(25)
Out[41]: '    hello world python   '

In [42]:
```

#### &lt;16&gt;rstrip {#rstrip}

删除 mystr 字符串末尾的空白字符

```
In [44]: name='hello world python    '

In [45]: name.rstrip()
Out[45]: 'hello world python'
```

#### &lt;17&gt;strip {#strip}

删除mystr字符串两端的空白字符

```
In [46]: name='   hello world python   '

In [47]: name.strip()
Out[47]: 'hello world python'

In [48]:
```

### &lt;18&gt;rfind {#rfind}

类似于 find\(\)函数，不过是从右边开始查找.

```
mystr.rfind(str, start=0,end=len(mystr) )
```

### &lt;19&gt;rindex {#rindex}

类似于 index\(\)，不过是从右边开始.

```
mystr.rindex( str, start=0,end=len(mystr))
```

### &lt;20&gt;partition {#partition}

把mystr以str分割成三部分,str前，str和str后

```
In [52]: name='hello world python3.6 '

In [53]: name.partition('python')
Out[53]: ('hello world ', 'python', '3.6 ')

In [54]:
```

### &lt;21&gt;rpartition {#rpartition}

类似于 partition\(\)函数,不过是从右边开始.

```
mystr.rpartition(str)
```

### &lt;22&gt;splitlines {#splitlines}

按照行分隔，返回一个包含各行作为元素的列表

```
In [59]: myStr='hello \n world \n python3.6'

In [60]: myStr.splitlines()
Out[60]: ['hello ', ' world ', ' python3.6']
```

### &lt;23&gt;isalpha {#isalpha}

如果 mystr 所有字符都是字母 则返回 True,否则返回 False

```
In [59]: myStr='hello \n world \n python3.6'

In [61]: myStr.isalpha()
Out[61]: False
```

### &lt;24&gt;isdigit {#isdigit}

如果 mystr 只包含数字则返回 True 否则返回 False

```
In [63]: name='123456'

In [64]: name.isdigit()
Out[64]: True

In [65]: name='123456y'

In [66]: name.isdigit()
Out[66]: False

In [67]:
```

### &lt;25&gt;isalnum {#isalnum}

如果 mystr 所有字符都是字母或数字或（字母和数子组合）则返回 True,否则返回 False

```
In [68]: name='123456'

In [69]: name.isalnum()
Out[69]: True

In [70]: name='123abc'

In [71]: name.isalnum()
Out[71]: True

In [72]: name='abcdef'

In [73]: name.isalnum()
Out[73]: True

In [74]: name='123 abc' # 包含 ‘ ’空格  

In [75]: name.isalnum()
Out[75]: False
```

### &lt;26&gt;isspace {#isspace}

如果 mystr 中只包含空格，则返回 True，否则返回 False.

```
In [74]: name='123 abc'

In [76]: name.isspace()
Out[76]: False

In [77]: name='   '

In [78]: name.isspace()
Out[78]: True
```

### &lt;27&gt;join {#join}

mystr 中每个字符后面插入str,构造出一个新的字符串

```
In [83]: name='123abcDEF'

In [86]: '-'.join(name)
Out[86]: '1-2-3-a-b-c-D-E-F'
```



