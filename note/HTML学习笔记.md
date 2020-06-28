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
URL我们再熟悉不过，最常见就是网页地址<br>
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

