---
title: Github与Gitee共存
date: 2020-01-06 09:42:24
tags:
- 软件
- 配置
categories:
- [安装]
---
# Github与Gitee共存 #

```
mkdir .ssh
cd .ssh
```

## 1.1、建立gitee秘钥 ##
ssh-keygen -t rsa -C "xxxxx@xxxxx.com"  
替换正确的邮箱，按enter  

```
Generating public/private rsa key pair.  
Enter file in which to save the key (/c/Users/FlyingHorse/.ssh/id_rsa): id_rsa_gitee   
```

## 1.2、建立github秘钥 ##
ssh-keygen -t rsa -C "xxxxx@xxxxx.com"  
替换正确的邮箱，按enter    

```
Generating public/private rsa key pair.  
Enter file in which to save the key (/c/Users/FlyingHorse/.ssh/id_rsa): id_rsa_github   
```

## 1.3、建立gitee工作秘钥 ##
ssh-keygen -t rsa -C "xxxxx@xxxxx.com"  
替换正确的邮箱，按enter    

```
Generating public/private rsa key pair.  
Enter file in which to save the key (/c/Users/FlyingHorse/.ssh/id_rsa): id_rsa_gitee_work   
```

## 2、public key复制到gitee或github ##

```
type id_rsa_gitee.pub
type id_rsa_github.pub  
type id_rsa_gitee_work.pub
```

## 3、创建配置解决ssh冲突 ##
在.ssh文件夹中创建config文件，添加以下内容以区分两个ssh key

```
# gitee
Host gitee.com
HostName gitee.com
PreferredAuthentications publickey
IdentityFile ~/.ssh/id_rsa_gitee

# github
Host github.com
HostName github.com
PreferredAuthentications publickey
IdentityFile ~/.ssh/id_rsa_github

# work
Host work
HostName gitee.com
PreferredAuthentications publickey
IdentityFile ~/.ssh/id_rsa_gitee_work
```

## 4、测试连接 ##
输入

```
ssh -T git@gitee.com
```

若返回如下图，则gitee则连接正常

```
Welcome to Gitee.com, yourname!
```

 输入

```
ssh -T git@github.com
```

若返回如下图，则github则连接正常

```
Hi yourname! You've successfully authenticated, but GitHub does not provide shell access.
```

## 5、工作账号使用 ##
1. 先修改下载地址 

```
将下载链接中的gitee.com替换为work
# 源连接
git@gitee.com:test/aaa.git
# 新连接
git@work:test/aaa.git
```

2. 程序下载
```
git clone git@work:test/aaa.git
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