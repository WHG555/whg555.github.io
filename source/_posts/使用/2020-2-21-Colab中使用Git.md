---
title: colab使用git
date: 2020-2-15 16:26:52
tags: 
- demo
categories:
- [使用]
---
# colab使用git #
## 配置用户与密码 ##
```
!git config --global user.name whghcyx
!git config --global user.email whghcyx@outlook.com
```
## 下载代码 ##
```
!git clone https://gitee.com/whghcyx/Pytorch-RetinaNet.git
```

## 上传代码 ##
```
!git remote set-url origin git@github.com:whghcyx/Pytorch-RetinaNet.git
!git add . --all
!git commit -m "test colab222768"
# 注意 passwd 的位置为自己的密码
!git push https://whghcyx:passwd@gitee.com/whghcyx/Pytorch-RetinaNet.git --all
```



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
