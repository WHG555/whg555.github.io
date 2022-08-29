---
title: hexo安装与使用教程
date: 2019-12-30 15:10:18
tags:

categories:
- [使用]
---



# 软件安装 #
- Node.js   
[https://nodejs.org/dist/v12.14.0/node-v12.14.0-x64.msi](https://nodejs.org/dist/v12.14.0/node-v12.14.0-x64.msi)    
- Git  
[enter image description here](https://git-scm.com) 
[Git-2.24.1.2-64-bit.exe](https://github.com/git-for-windows/git/releases/download/v2.24.1.windows.2/Git-2.24.1.2-64-bit.exe)
- nexo
npm install -g hexo-cli

# 软件配置 #

参数|	描述|	默认值
:-|:-|:-
layout	|布局	
title	|标题	文章的文件名
date	|建立日期	文件建立日期
updated	|更新日期	文件更新日期
comments	|开启文章的评论功能	|true
tags	|标签（不适用于分页）	
categories	|分类（不适用于分页）	
permalink	|覆盖文章网址	
keywords	|仅用于 meta 标签和 Open Graph 的关键词（不推荐使用）	
top |将文章置顶 | false

# 软件使用 #



# 简单使用 #
hexo init hexo
cd hexo
npm install --save hexo-deployer-git
hexo g
hexo server
## 文章首部信息说明 ##
```
categories:
- Diary
tags:
- PS3
- Games

categories:
- [Diary, PlayStation]
- [Diary, Games]
- [Life]
```

文章不被处理

```
---
layout: false  # 更改这里
title: OpenCV编译  
date: 2019-10-8 
tags: 
- Opencv 编译
categories:
- []
---
```

# 文章编译 #
1. 添加草稿
>hexo new draft demo

2. 添加笔记
>hexo new post demo

3. 发布文章
>hexo publish post demo

# 引用 #
{% codeblock %}
code snippet
{% endcodeblock %}

{% codeblock lang:objc %}
[rectangle setX: 10 y: 10 width: 20 height: 20];
{% endcodeblock %}

{% blockquote Seth Godin http://sethgodin.typepad.com/seths_blog/2009/07/welcome-to-island-marketing.html Welcome to Island Marketing %}
Every interaction is both precious and an opportunity to delight.
{% endblockquote %}

# 帮助文档  #
[https://hexo.io/zh-cn/docs/](https://hexo.io/zh-cn/docs/)

---
<center>
<table>
    <tr>
        <td >
            <center>
                <img src="https://i.loli.net/2020/01/08/CJz85Sbal6M7EOV.png" width="200"/>
            </center>
            <center style="font-weight:900">
                微信：宏沉一笑
            </center>
        </td>
        <td >
            <center>
                <img src="https://i.loli.net/2020/01/08/veq2DSphHME9KPV.jpg" width="200"/>
            </center>
            <center style="font-weight:900">
                公众号：漫步之行
            </center>
        </td>
    </tr>
</table>
</center>


**签名：Smile every day**    
**名字：宏沉一笑**   
**邮箱：whghcyx@outlook.com**  
**个人网站：https://whg555.github.io**  
---