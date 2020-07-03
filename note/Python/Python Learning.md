### zip函数
>>>a = [1,2,3]
>>> b = [4,5,6]
>>> c = [4,5,6,7,8]
>>> zipped = zip(a,b)     # 打包为元组的列表
[(1, 4), (2, 5), (3, 6)]
>>> zip(a,c)              # 元素个数与最短的列表一致
[(1, 4), (2, 5), (3, 6)]
>>> zip(*zipped)          # 与 zip 相反，*zipped 可理解为解压，返回二维矩阵式
[(1, 2, 3), (4, 5, 6)]

### pickle
pickle与cPickle；两者的关系：“cPickle – A faster pickle”
* dump()函数接受一个文件句柄和一个数据对象作为参数，把数据对象以特定的格式保存到给定的文件中。
```
cPickle.dump(data,open("test\\data.pkl","wb")) 
```
* 使用load()函数从文件中取出已保存的对象时，pickle知道如何恢复这些对象到它们本来的格式。
```
data = cPickle.load(open("test\\data.pkl","rb"))
```
* dumps：将python对象序列化保存到一个字符串变量中
```
data_string = cPickle.dumps(data)
```
* 从字符串变量中载入python对象
```
data = cPickle.loads(data_string)
```

### with(```__enter__和__exit__```)
```python
class Sample:
    def __enter__(self):
        return self

    def __exit__(self, type, value, trace):
        print "type:", type
        print "value:", value
        print "trace:", trace
        
    def do_something(self):
        bar = 1/0
        return bar + 10

with Sample() as sample:
    sample.do_something()

>>>
type: <type 'exceptions.ZeroDivisionError'>
value: integer division or modulo by zero
trace: <traceback object at 0x1004a8128>
Traceback (most recent call last):
  File "./with_example02.py", line 19, in <module>
    sample.do_somet hing()
  File "./with_example02.py", line 15, in do_something
    bar = 1/0
ZeroDivisionError: integer division or modulo by zero
```

### open


### 字符串
字符串内默认不转义在前面加r``print(r'\\\t\\\\')``
多行打印使用‘’‘...’‘’

### 除法
* / 结果是浮点数
* // 地板除 结果是取浮点数部分的整数部分