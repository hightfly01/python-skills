## hashlib模块

Python的hashlib提供了常见的摘要算法，如MD5，SHA1等等。

摘要算法又称哈希算法、散列算法。它通过一个函数，把任意长度的数据转换为一个长度固定的数据串（通常用16进制的字符串表示）。

我们以常见的摘要算法MD5为例，计算出一个字符串的MD5值：

```
import hashlib
m = hashlib.md5()   #创建hash对象，md5:(message-Digest Algorithm 5)消息摘要算法,得出一个128位的密文
print m             #<md5 HASH object>
m.update('how to use md5 in python hashlib?')  #更新哈希对象以字符串参数
print m.hexdigest() #返回十六进制数字字符串
```

计算结果：

```
d26a53750bc40b38b65a520292f69306
```

另一种常见的摘要算法是SHA1，调用SHA1和调用MD5完全类似：

```
import hashlib

sha1 = hashlib.sha1()
sha1.update('how to use sha1 in ')
sha1.update('python hashlib?')
print sha1.hexdigest()
```

SHA1的结果是160 bit字节，通常用一个40位的16进制字符串表示。

比SHA1更安全的算法是SHA256和SHA512，不过越安全的算法越慢，而且摘要长度更长。



#### 应用实例 {#应用实例}

用于注册、登录....



```
import hashlib
import datetime
KEY_VALUE = 'Itcast'
now = datetime.datetime.now()
m = hashlib.md5()
str = '%s%s' % (KEY_VALUE,now.strftime("%Y%m%d"))
m.update(str.encode('utf-8'))
value = m.hexdigest()
print(value)
```



