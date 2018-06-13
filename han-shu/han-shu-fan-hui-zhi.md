## &lt;1&gt;带有返回值的函数 {#带有返回值的函数}

想要在函数中把结果返回给调用者，需要在函数中使用return

```
    def add2num(a, b):
        return a+b
```

## &lt;2&gt;带有多个返回值的函数 {#带有返回值的函数}

```
>>> def divid(a, b):
...     shang = a//b
...     yushu = a%b 
...     return shang, yushu # 本质是利用了元组
...
>>> sh, yu = divid(5, 2) # 返回元组，并对元组拆包
>>> sh
5
>>> yu
1
```



