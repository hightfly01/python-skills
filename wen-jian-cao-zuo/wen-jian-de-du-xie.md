## &lt;1&gt;写数据\(write\) {#写数据write}

使用write\(\)可以完成向文件写入数据

```
f = open('test.txt', 'w')
f.write('hello world, i am here!')
f.close()
```

注意：

* 如果文件不存在那么创建，如果存在那么就先清空，然后写入数据

## &lt;2&gt;读数据\(read\) {#读数据read}

使用read\(num\)可以从文件中读取数据，num表示要从文件中读取的数据的长度（单位是字节），如果没有传入num，那么就表示读取文件中所有的数据

```
f = open('test.txt', 'r')

content = f.read(5)

print(content)

print("-"*30)

content = f.read()

print(content)

f.close()
```

注意：

* 如果open是打开一个文件，那么可以不用写打开的模式，即只写
  `open('test.txt')`
* **如果使用读了多次，那么后面读取的数据是从上次读完后的位置开始的**

## &lt;3&gt;读数据（readlines） {#读数据（readlines）}

readlines可以按照行的方式把整个文件中的内容进行一次性读取，并且返回的是一个列表，其中每一行的数据为一个元素

```
f = open('test.txt', 'r')

content = f.readlines()

print(type(content))

i=1
for temp in content:
    print("%d:%s"%(i, temp))
    i+=1

f.close()
```

## &lt;4&gt;读数据（readline） {#读数据（readline）}

readline可以按照行的方式把文件中的内容按照行读取

```
f = open('test.txt', 'r')

content = f.readline()
print("1:%s"%content)

content = f.readline()
print("2:%s"%content)

f.close()
```

## &lt;5&gt;定位读写 {#读数据（readline）}

#### &lt;5-1&gt;获取当前读写的位置

在读写文件的过程中，如果想知道当前的位置，可以使用tell\(\)来获取

```
 # 打开一个已经存在的文件
    f = open("test.txt", "r")
    str = f.read(3)
    print "读取的数据是 : ", str

    # 查找当前位置
    position = f.tell()
    print "当前文件位置 : ", position

    str = f.read(3)
    print "读取的数据是 : ", str

    # 查找当前位置
    position = f.tell()
    print "当前文件位置 : ", position

    f.close()
```

#### &lt;5-2&gt;定位到某个位置

如果在读写文件的过程中，需要从另外一个位置进行操作的话，可以使用seek\(\)

seek\(offset, from\)有2个参数

* offset:偏移量
* from:方向
  * 0:表示文件开头
  * 1:表示当前位置
  * 2:表示文件末尾

demo:把位置设置为：从文件开头，偏移5个字节

```
 # 打开一个已经存在的文件
    f = open("test.txt", "r")
    str = f.read(30)
    print "读取的数据是 : ", str

    # 查找当前位置
    position = f.tell()
    print "当前文件位置 : ", position

    # 重新设置位置
    f.seek(5,0)

    # 查找当前位置
    position = f.tell()
    print "当前文件位置 : ", position

    f.close()
```



