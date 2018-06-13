# python2中的输入

### 1.1 raw\_input\(\) {#11-rawinput}

在Python中，获取键盘输入的数据的方法是采用 raw\_input 函数。如：

```
password = raw_input("请输入内容:")
print ("您输入的内容是：%s"%password)
```

**注意**:

* raw\_input\(\)的小括号中放入的是，提示信息，用来在获取数据之前给用户的一个简单提示
* raw\_input\(\)在从键盘获取了数据以后，会存放到等号右边的变量中
* raw\_input\(\)会把用户输入的任何值都作为字符串来对待

### 1.2 input\(\) {#12-input}

input\(\)函数与raw\_input\(\)类似，但其接受的输入必须是**表达式**。

如：

```
input('请输入表达式：')
请输入表达式：1+2
'1+2'
```

### 注意：

**input\(\)只接受表达式输入，并把表达式的结果赋值给等号左边的变量**

# python3中的输入

**没有raw\_input\(\)函数，只有input\(\)，并且 python3中的input与python2中的raw\_input\(\)功能一样**。

```
    userName = input('请输入用户名:')
    print("用户名为：%s"%userName)
```

**注意**：input获取的数据，都以**字符串的方式进行保存，即使输入的是数字，那么也是以字符串方式保存**

