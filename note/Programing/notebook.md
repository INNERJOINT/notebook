## 强弱类型和动态静态语言
* 强类型语言指强制类型定义，即不经过强制类型转换不能变换。强类型语言包括：C++，Java，Python等
弱类型例子：
```VB
var A=5;
var B="5"
sumA=A+B;‘sumA=55,A自动转化为string类型
sumB=A-B;’sumB=0,B自动转化为int类型
```
* 动态语言指的是变量本身类型不固定的语言，是在运行期间才去做数据类型检查。定义变量时不需要指定变量类型。如Python和Java的对比。
##### 强类型和弱类型对比，强类型速度上可能稍逊于弱类型，但严谨性高
##### 动态语言和静态语言对比，区别在于是在编译期间还是运行期间做变量类型检查