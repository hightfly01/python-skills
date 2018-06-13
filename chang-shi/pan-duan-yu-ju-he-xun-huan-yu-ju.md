### if-elif-else 判断语句

```
 if 条件:
      执行语句
       ...
 elif 条件:
       执行语句
       ...
 else:
       执行语句
       ...
```

### while循环语句

如：

```
i = 1
sum = 0
while i<=100:
    if i%2 == 0:
        sum = sum + i
    i+=1

print("1~100的累积和为:%d"%sum)
```

### for循环

在Python中 for循环可以遍历任何序列的项目，如一个列表或者一个字符串等。

**for循环的格式**：

```
for 临时变量 in 列表或者字符串等:
        循环满足条件时执行的代码
else:
        循环不满足条件时执行的代码
```

```
    name = 'dongGe'
    for x in name:
        print(x)


-------------------------------------

    name = ''
    for x in name:
        print(x)
    else:
        print("没有数据")
```

### break和continue

break的作用：用来结束整个循环。如：

```
  name = 'dongGe'
  for x in name:
      print('----')
      if x == 'g': 
          break
      print(x)
```

continue的作用：用来结束本次循环，紧接着执行下一次的循环。如：

```
  i = 0
  while i<10:
      i = i+1
      print('----')
      if i==5:
          continue
      print(i)
```

### 注意点

* **break/continue只能用在循环中，除此以外不能单独使用**

* **break/continue在嵌套循环中，只对最近的一层循环起作用**



