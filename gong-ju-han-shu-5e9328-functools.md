functools函数工具库

```
import functools
dir(functools)
```

```
[
  'MappingProxyType',
  'RLock',
  'WRAPPER_ASSIGNMENTS',
  'WRAPPER_UPDATES',
  'WeakKeyDictionary',
  '_CacheInfo',
  '_HashedSeq',
  '__all__',
  '__builtins__',
  '__cached__',
  '__doc__',
  '__file__',
  '__loader__',
  '__name__',
  '__package__',
  '__spec__',
  '_c3_merge',
  '_c3_mro',
  '_compose_mro',
  '_convert',
  '_find_impl',
  '_ge_from_gt',
  '_ge_from_le',
  '_ge_from_lt',
  '_gt_from_ge',
  '_gt_from_le',
  '_gt_from_lt',
  '_le_from_ge',
  '_le_from_gt',
  '_le_from_lt',
  '_lru_cache_wrapper',
  '_lt_from_ge',
  '_lt_from_gt',
  '_lt_from_le',
  '_make_key',
  'cmp_to_key',
  'get_cache_token',
  'lru_cache',
  'namedtuple',
  'partial',
  'partialmethod',
  'recursive_repr',
  'reduce',
  'singledispatch',
  'total_ordering',
  'update_wrapper',
  'wraps'
]
```

python3中增加了更多工具函数，做业务开发时大多情况下用不到，此处介绍使用频率较高的2个函数。

#### partial函数\(偏函数\):冻结参数 {#partial函数偏函数}

基于一个函数创 建一个新的可调用对象，把原函数的某些参数固定。使用这个函数可以把接受一个或多个 参数的函数改编成需要回调的API，这样参数更少

```
import functools

def showarg(*args, **kw):
    print(args)
    print(kw)

p1=functools.partial(showarg, 1,2,3)
p1()
p1(4,5,6)
p1(a='python', b='partial')
```



