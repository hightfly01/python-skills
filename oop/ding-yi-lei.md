# 类的概念

类：

```
将具有共同特征和行为的一组对象抽象定义。
具有相同属性和行为事物的统称
```

# 定义类

```
# 定义类
class Car(object):
    # 方法
    def getCarInfo(self):
        print('车轮子个数:%d, 颜色%s'%(self.wheelNum, self.color))

    def move(self):
        print("车正在移动...")
```

#### 说明： {#说明：}

* 定义类时有2种：新式类和经典类，上面的Car为经典类，如果是Car\(object\)则为新式类
* 类名 的命名规则按照"大驼峰"

# 对象概念

```
某一个具体事物的存在 ,在现实世界中可以是看得见摸得着的。
可以是直接使用的
```

# 对象创建

python中，可以根据已经定义的类去创建出一个个对象

创建对象的格式为:

```
对象名 = 类名()
```

```
# 定义类
class Car:
    # 移动
    def move(self):
        print('车在奔跑...')

    # 鸣笛
    def toot(self):
        print("车在鸣笛...嘟嘟..")

# 创建一个对象，并用变量BMW来保存它的引用
BMW = Car()
BMW.color = '黑色'
BMW.wheelNum = 4 #轮子数量
BMW.move()
BMW.toot()
print(BMW.color)
print(BMW.wheelNum)
```



