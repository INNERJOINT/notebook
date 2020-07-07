---
layout:     post                    # 使用的布局（不需要改）
title:      HTML学习笔记               # 标题 
subtitle:   Hello World, Hello Blog #副标题
date:       2020-06-19              # 时间
author:     INNERJOINT                      # 作者
header-img: img/post-bg-2015.jpg    #这篇文章标题背景图片
catalog: true                       # 是否归档
tags:                               #标签
    - HTML
---

## URI(Uniform Resourece Identifier)统一资源标识符号
URI可以指URL，URN或者同时是两者
#### URL(Uniform Resource Locator)统一资源定位符

URL我们再熟悉不过，最常见就是网页地址
**URL在额外参数后面可以跟上#SomewhereInTheDocument标示资源本身一部分的锚点，例如视频播放到的位置，锚点部分是不会发送给服务器的！**
例如：https://zh.wikipedia.org/wiki/%E7%BB%9F%E4%B8%80%E8%B5%84%E6%BA%90%E5%AE%9A%E4%BD%8D%E7%AC%A6

#### URN(Uniform Resource Name)统一资源名称

不同于URL类似地图导航的方式，将你从根域名一步步引导你到子目录内寻找资源的方式，URN类似一个人的身份证。<br>
栗子：<br>
* urn:isbn:0554564646
* urn:uuid:6e8bc430-9c3a-11d9-9669-0800200c9a66
URN是在命名空间内寻找资源如ISBN图书编码，UUID统一唯一识别码。。。

---
## HTML中的空格
>HTML提供了5种空格实体（space entity），它们拥有不同的宽度，非断行空格（```&nbsp```）是常规空格的宽度，可运行于所有主流浏览器。其他几种空格（```&ensp; &emsp; &thinsp; &zwnj; &zwj```）在不同浏览器中宽度各异。
>> * ```&nbsp```**Unicode编码U+00A0** [ref1](https://www.fileformat.info/info/unicode/char/00a0/index.htm)    [ref2](https://www.unicode.org/charts/PDF/U0080.pdf)
半角不换行空格，全称No-Break Space，**用途是禁止自动换行**，它是最常见和我们使用最多的空格，大多数的人可能只接触了```&nbsp```，它是按下space键产生的空格。在HTML中，如果你用空格键产生此空格，空格是不会累加的（只算1个）。要使用html实体表示才可累加，该空格占据宽度受字体影响明显而强烈。
>> * ```&ensp```**Unicode编码U+2002**[ref1](https://www.fileformat.info/info/unicode/char/2002/index.htm) 
它叫“半角空格”，全称是En Space，en是字体排印学的计量单位，为em宽度的一半。根据定义，它等同于字体度的一半（如16px字体中就是8px）。名义上是小写字母n的宽度。此空格传承空格家族一贯的特性：透明的，此空格有个相当稳健的特性，就是其占据的宽度正好是1/2个中文宽度，而且基本上不受字体影响。
>>* ```&emsp```**Unicode编码U+2003**[ref1](https://www.fileformat.info/info/unicode/char/2003/index.htm) 
它叫“全角空格”，全称是Em Space，em是字体排印学的计量单位，相当于当前指定的点数。例如，1 em在16px的字体中就是16px。此空格也传承空格家族一贯的特性：透明的，此空格也有个相当稳健的特性，就是其占据的宽度正好是1个中文宽度，而且基本上不受字体影响。

---
## DOCTYPE
用于标示该HTML文档使用了哪个HTML标准<br>
在HTML4.01中又分为Transitional、Strict、Frameset。<br>
对于不同的标准，支持的元素不同，例如，```<aside>```元素只在HTML5中支持。
H5之前，需要引用DTD（Document Type Definition)
>DTD用于定义合法的XML文档构建模块,如下为一电视台的某一实例
```
<!DOCTYPE TVSCHEDULE [
<!ELEMENT TVSCHEDULE (CHANNEL+)>
<!ELEMENT CHANNEL (BANNER,DAY+)>
<!ELEMENT BANNER (#PCDATA)>
<!ELEMENT DAY (DATE,(HOLIDAY|PROGRAMSLOT+)+)>
<!ELEMENT HOLIDAY (#PCDATA)>
<!ELEMENT DATE (#PCDATA)>
<!ELEMENT PROGRAMSLOT (TIME,TITLE,DESCRIPTION?)>
<!ELEMENT TIME (#PCDATA)>
<!ELEMENT TITLE (#PCDATA)> 
<!ELEMENT DESCRIPTION (#PCDATA)>

<!ATTLIST TVSCHEDULE NAME CDATA #REQUIRED>
<!ATTLIST CHANNEL CHAN CDATA #REQUIRED>
<!ATTLIST PROGRAMSLOT VTR CDATA #IMPLIED>
<!ATTLIST TITLE RATING CDATA #IMPLIED>
<!ATTLIST TITLE LANGUAGE CDATA #IMPLIED>
]>
```
现在DTD基本上由XML Schema（XSD）替代
>在构建DTD过程中：<br>
PCDATA(parsed character data)会被解析的字符数据
CDATA(character data)不会被解析的字符数据
---

## HTML空元素
标准HTML元素中，某些元素是没有内容的，称为空元素，如``<br>``

## Test
```
5.在下列的 HTML 中，哪个可以添加背景颜色？
您的回答：<background>yellow</background>

正确答案：<body bgcolor="yellow">

6.请选择产生粗体字的 HTML 标签：
您的回答：<bold>

正确答案：<b>

7.请选择产生斜体字的 HTML 标签：
您的回答：<italics>

正确答案：<i>

9.如何制作电子邮件链接？
您的回答：<mail href="xxx@yyy">

正确答案：<a href="mailto:xxx@yyy">

10.如何在新窗口打开链接？
您的回答：<a href="url" target="new">

正确答案：<a href="url" target="_blank">


12.请选择可以使单元格中的内容进行左对齐的正确 HTML 标签：
您的回答：<td align="left">

13.如何产生带有数字列表符号的列表？
您的回答：<ol>

14.如何产生带有圆点列表符号的列表？
您的回答：<dl>

正确答案：<ul>

15.在下列的 HTML 中，哪个可以产生复选框？
您的回答：<input type="check">

正确答案：<input type="checkbox">

16.在下列的 HTML 中，哪个可以产生文本框？
您的回答：<input type="text">

17.在下列的 HTML 中，哪个可以产生下拉列表？
您的回答：<input type="dropdown">

正确答案：<select>

18.在下列的 HTML 中，哪个可以产生文本区（textarea）？
您的回答：<input type="textarea">

正确答案：<textarea>

19.在下列的 HTML 中，哪个可以插入图像？
您的回答：<image src="image.gif">

正确答案：<img src="image.gif">

20.在下列的 HTML 中，哪个可以插入背景图像？
您的回答：<background img="background.gif">

正确答案：<body background="background.gif">```