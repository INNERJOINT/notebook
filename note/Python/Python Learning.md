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

### format
* "hello {0}{1:}"使用{}:代替以前的%
* 
|输入|格式化|输出|说明|
|---|----|---|---|
|3.1415926|	{:.2f}|	3.14|	保留小数点后两位|
|3.1415926|	{:+.2f}	|+3.14|	带符号保留小数点后两位
-1	|{:+.2f}	|-1.00	|带符号保留小数点后两位
2.71828|	{:.0f}|	3	|不带小数
5	|{:0>2d}|	05|	数字补零 (填充左边, 宽度为2)
5	|{:x<4d}	|5xxx	|数字补x (填充右边, 宽度为4)
10	|{:x<4d}|	10xx	|数字补x (填充右边, 宽度为4)
1000000|	{:,}|	1,000,000|	以逗号分隔的数字格式
0.25	|{:.2%}|	25.00%|	百分比格式
1000000000	|{:.2e}|	1.00e+09|	指数记法
13	|{:>10d}|	        13|	右对齐 (默认, 宽度为10)
13	|{:<10d}	|13	|左对齐 (宽度为10)
13	|{:^10d}|	    13|	中间对齐 (宽度为10)
11|	'{:b}'.format(11)|1011|二进制
11|'{:d}'.format(11)|11|十进制
11|'{```:o```}'.format(11)|13|八进制
11|'{:x}'.format(11)|b|十六进制
11|'{:#x}'.format(11)|0xb|十六进制带0x
11|'{:#X}'.format(11)	|0XB|十六进制带0X

### tunple
* 定义空tuple：t = ()
* 定义只有1的tuple: t = (1,)#不加，会把t当作1
* 可变tuple: t = (1,2,['A','B'])#t[2]为list，可变化

### dict
* 判断key是否存在两种方法：‘XXX' in dict； dict.get('XXX')
* dict内部存放的顺序和key放入的顺序是没有关系的
#### dict与list对比
和list比较，dict有以下几个特点：

查找和插入的速度极快，不会随着key的增加而变慢；
需要占用大量的内存，内存浪费多。
而list相反：

查找和插入的时间随着元素的增加而增加；
占用空间小，浪费内存很少。
所以，dict是用空间来换取时间的一种方法。

### set
无重复key集合
```
>>> s = set([1, 2, 3])
>>> s
{1, 2, 3}
>>> s = set([1, 1, 2, 2, 3, 3])
>>> s
{1, 2, 3}
```

### 切片
```python
#前11-20位数
>>> L[10:20]
[10, 11, 12, 13, 14, 15, 16, 17, 18, 19]
#每5个数取一次
>>> L[::5]
#前10个数，每2个数取一次
>>> L[:10:2]
```

### 列表生成器
```python
>>> [m + n for m in 'ABC' for n in 'XYZ']
['AX', 'AY', 'AZ', 'BX', 'BY', 'BZ', 'CX', 'CY', 'CZ']
>>> [x for x in range(1, 11) if x % 2 == 0]
[2, 4, 6, 8, 10]
>>> [x if x % 2 == 0 else -x for x in range(1, 11)]
[-1, 2, -3, 4, -5, 6, -7, 8, -9, 10]
```

### 生成器
产生生成器的两种方法：
* 把列表生成器的[]改为()
```python
>>> L = [x * x for x in range(10)]
>>> L
[0, 1, 4, 9, 16, 25, 36, 49, 64, 81]
>>> g = (x * x for x in range(10))
>>> g
<generator object <genexpr> at 0x1022ef630>
```
* 使用yield代替return将函数变成生成器

调用生成器的方法：
* 使用next（）
* 使用for循环

### 迭代器
凡是可作用于for循环的对象都是Iterable类型；

凡是可作用于next()函数的对象都是Iterator类型，它们表示一个惰性计算的序列；

集合数据类型如list、dict、str等是Iterable但不是Iterator，不过可以通过iter()函数获得一个Iterator对象。

###  高阶函数
函数名也是变量名，不但可以指定新的函数名如x=abs,也可以把函数名当成参数传给新的函数如def add(x,y,f):return f(x)+f(y)
* map()函数,第一个参数f是函数本身，第二个参数是一个Iterator
```python
>>> def f(x):
...     return x * x
...
>>> r = map(f, [1, 2, 3, 4, 5, 6, 7, 8, 9])
>>> list(r)
[1, 4, 9, 16, 25, 36, 49, 64, 81]
```
* reduce()函数，把一个函数作用在一个序列上，该函数必须接受两个参数
```python
>>> from functools import reduce
>>> def fn(x, y):
...     return x * 10 + y
...
>>> reduce(fn, [1, 3, 5, 7, 9])
13579
```
将两者结合起来可以整理成一个str2int函数
```python
from functools import reduce

DIGITS = {'0': 0, '1': 1, '2': 2, '3': 3, '4': 4, '5': 5, '6': 6, '7': 7, '8': 8, '9': 9}

def str2int(s):
    def fn(x, y):
        return x * 10 + y
    def char2num(s):
        return DIGITS[s]
    return reduce(fn, map(char2num, s))
```
* filter()函数，接受一个函数和序列
```python
def is_odd(n):
    return n % 2 == 1

list(filter(is_odd, [1, 2, 4, 5, 6, 9, 10, 15]))
```
**filter和map一样，返回的是一个Iterator，是一个惰性序列，要强迫完成计算结果，可以使用list（）获取所有结果**

* sorted(),第一个参数排序的序列，第二个key为排序函数，reverse为逆向排序
```python
L = [('Bob', 75), ('Adam', 92), ('Bart', 66), ('Lisa', 88)]
def by_name(t):
    return t[0]

L2 = sorted(L, key=by_name)
print(L2)
```
### 匿名函数lambda
只能有一个表达式的函数

### 装饰器

### 偏函数
一种用于固定一些函数的参数值的方法，导入functool包，使用如下：
```python
>>> import functools
>>> int2 = functools.partial(int, base=2)
>>> int2('1000000')
64
>>> int2('1010101')
85
```