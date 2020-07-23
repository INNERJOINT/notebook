
### type|dtype|astype
```python
import numpy as np
a=[1,2,3]
print(type(a))
#>>><class 'list'>
b=np.array(a)
print(type(b))
#>>><class 'numpy.ndarray'>
print(b.dtype)
#>>>int64

e=np.linspace(1,5,20)#numpy.linspace(start, stop, num=50, endpoint=True, retstep=False, dtype=None)
#在指定的间隔内返回均匀间隔的数字。
print(e)
#>>>
'''
[1.         1.21052632 1.42105263 1.63157895 1.84210526 2.05263158
 2.26315789 2.47368421 2.68421053 2.89473684 3.10526316 3.31578947
 3.52631579 3.73684211 3.94736842 4.15789474 4.36842105 4.57894737
 4.78947368 5.        ]
'''
print(e.dtype)
#>>>float64

e=e.astype(int)
print(e)
#>>>[1 1 1 1 1 2 2 2 2 2 3 3 3 3 3 4 4 4 4 5]
print(e.dtype)
#>>>int64
```

### transpose
```python
x.transpose((0,1)) #original location
x.transpose((1,0)) #swap x and y aixs
```