### 使用生成器打印杨辉三角\(即帕斯卡三角形\)

打印效果

```
[1]
[1, 1]
[1, 2, 1]
[1, 3, 3, 1]
[1, 4, 6, 4, 1]
[1, 5, 10, 10, 5, 1]
[1, 6, 15, 20, 15, 6, 1]
[1, 7, 21, 35, 35, 21, 7, 1]
[1, 8, 28, 56, 70, 56, 28, 8, 1]
```

代码实现：

```
def triangles():
    ret = [1] # 第一次调用时，第一元素为1
    while True:
        yield ret
        #for循环中，计算每一个行第一元素和最后一个元素之间的元素
        #通过图形观察：每个的第一元素和最后一个元素都是1.只需要计算中间的元素即可。
        #每一行中间元素的算法机制：
            #ret变量：当前行计算之后的数组
            #pre变量：记录上一行保存的数据
            #计算当前行的中间每个元素规则：
            # 根据pre变量保存的数据，来计算。
            #  比如：
            # pre = [1,2,1]
            # ret =  [1,3,3,1]
            # ret的第2个元素 3 : pre中的第2元素(1) + 第1个元素(2)
            # ret的第3个元素 3 :  pre中的第3个元素 (1) + 第2个元素(2)
            # 以此类推....
        for i in range(1, len(ret)):
            ret[i] = pre[i] + pre[i - 1]
        ret.append(1) # 每一行添加最后一个元素为1
        pre = ret[:]

t = triangles()

print(next(t)) 
print(next(t)) 
print(next(t)) 
print(next(t)) 
print(next(t)) 
print(next(t)) 
print(next(t)) 
print(next(t)) 
print(next(t))

```


