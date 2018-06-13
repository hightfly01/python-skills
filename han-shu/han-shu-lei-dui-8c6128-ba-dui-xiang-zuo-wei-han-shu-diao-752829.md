## 用户定义的可调用类型

不仅Python函数是真正的对象，任何Python对象都可以表现得像函数。为此，只需实现实例方法\_\_call\_\_。

```
import random
class BingoCage:
     def __init__(self, items): 
          self._items = list(items) ➊ 
          random.shuffle(self._items) ➋

     def pick(self): ➌ 
          try:
              return self._items.pop()
          except IndexError:
               raise LookupError('pick from empty BingoCage') ➍ 

     def __call__(self): ➎
          return self.pick()
```

➊\_\_init\_\_接受任何可迭代对象;在本地构建一个副本，防止列表参数的意外副作用。

➋shuffle定能完成工作，因为self.\_items是列表。  
➌起主要作用的方法。  
➍如果self.\_items为空，抛出异常，并设定错误消息。

➎bingo.pick\(\)的快捷方式是bingo\(\)。

* > 注意，bingo实例可以作为函数调用，因为类中实现\_\_call\_\_方法



