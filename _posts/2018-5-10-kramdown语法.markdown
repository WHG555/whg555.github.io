---
layout: post  
title: kramdown语法  
date: 2018-5-9 23:57:31  
group:   
tags:   
---
测试一下
# 大标题  
## 小标题  
### 超小标题  
 超大标题   //等于号写于文字下方  
===  
 标题      //同超大标题  
---

2.行内代码
`这个符号在1的左边`
这个符号在1的左边
3. 引用
书写方式: >、> > + 空格 + 内容

A.单层引用

>第一行>开头+两个空格换行
第二行不必再写>
效果

第一行>开头+两个空格换行 
第二行不必再写>
B.叠层引用


> This is the first level of quoting.
>
> > This is nested blockquote.
>
> Back to the first level.
效果

This is the first level of quoting.

This is nested blockquote.
Back to the first level.
4. 列表
A.无序列表

书写方式 *、-、+ + 空格 + 内容

* Red
* Green
* Blue

- Red
- Green
- Blue

+ Red
+ Green
+ Blue
效果:(三种方式效果一样)

Red
Green
Blue
Red
Green
Blue
Red
Green
Blue
B.有序列表

书写方式 数字 + 空格 + 内容

 1. 这是第一个
 1. 这是第二个
 1. 这是第三个
效果:(会自动排序)

这是第一个
这是第二个
这是第三个
5. 分割线
书写方式: ***、---、\n +> + \n

* * *
***
*****
- - -
---
效果:

图片描述

6. 超链接
书写方式: [title](href)


[markdown-syntax](http://daringfireball.net/projects/markdown/syntax)
效果

markdown-syntax
以变量的方式定义超链接 
书写方式[var_name]: url "title"

[id]: http://example.com/  "Optional Title Here"
This is [an example][id] reference-style link.
效果:

This is an example reference-style link.
7. 强调(加粗，斜体)
书写方式: *内容*、**内容**、_内容_、__内容__,

*内容*
**内容**
_内容_
__内容__
效果:

内容 
内容 
内容 
内容
8. 图片引用
书写方式:![alt](图片路径)


![这是张图片](/path/to/im)
效果:
图片描述
这个跟超链一样都可以设置定义变量

[id]: url/to/image  "Optional title attribute"
![hahah][id]
效果

图片描述

9. 杂项
A.简单超链接

<http://example.com/>
效果:

http://example.com/
B.简单email地址

<xiazhichao75@126.com>
效果:

xiazhichao75@126.com
10. 代码块
书写方式:四个空格 or Tab

    四个空格
    一个tab
效果:

四个空格
一个tab
心得
因为之前看过SF的markdown解释器的语法规则，当时我想，这都是markdown，语法应该都一个样吧，结果照着SF的语法规则，行不通。下面我就来列一列他们之间的有哪些是不一样的

引用的换行
SF的换行规则是另起一行+`>`

GP的换行规则是在一行末尾+两空格`  `+回车不必+`>`
SF无法引用超大标题,为了让你们看到效果，我才截的图,当然这可能没什么卵用
分割线的使用方法，
SF是---,***中间不可加空格
GP是可以在中间插空格的
SF无法将<xiazhichao75@126.com>解释成email
新手驾到，如有不足之处，还请指点，大家共同进步。
##空格##
在中文输入法的情况下：shift＋空格键切换至全角模式，之后再按空格键，那么空格键就会生效。  
添加

	&#160;
或者  

	&nbsp;
注意：分号是英文状态下的！

***
参考链接 
http://kramdown.gettalong.org/converter/kramdown.html
http://daringfireball.net/projects/markdown/syntax
2016年03月05日发布
