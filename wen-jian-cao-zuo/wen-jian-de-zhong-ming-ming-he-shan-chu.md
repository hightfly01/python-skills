# 文件的重命名、删除 {#文件的重命名、删除}

有些时候，需要对文件进行重命名、删除等一些操作，python的os模块中都有这么功能

## &lt;1&gt;文件重命名 {#文件重命名}

os模块中的rename\(\)可以完成对文件的重命名操作

rename\(需要修改的文件名, 新的文件名\)

```
    import os
    os.rename("aa.txt", "aa-update.txt")
```

## &lt;2&gt;删除文件 {#删除文件}

os模块中的remove\(\)可以完成对文件的删除操作

remove\(待删除的文件名\)

```
    import os
    os.remove("aa.txt")
```



