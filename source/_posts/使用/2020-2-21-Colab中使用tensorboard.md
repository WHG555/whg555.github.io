---
title: Colab中使用tensorboard
date: 2020-2-21 11:50:45
tags: 
- Colab
- tensorboard
categories:
- [使用]
---
# 配置 #
- 文件下载
```
!wget https://bin.equinox.io/c/4VmDzA7iaHb/ngrok-stable-linux-amd64.zip
!unzip ngrok-stable-linux-amd64.zip
```
- 进行配置
```
# 设置log目录
LOG_DIR = '/content/drive/log'
get_ipython().system_raw('tensorboard --logdir {} --host 0.0.0.0 --port 6006 &'.format(LOG_DIR))
```
- 开启ngrok

```
#开启ngrok service，绑定port 6006(tensorboard)
get_ipython().system_raw('./ngrok http 6006 &')
```
- 启动服务
```
! curl -s http://localhost:4040/api/tunnels | python3 -c \
"import sys, json; print(json.load(sys.stdin)['tunnels'][0]['public_url'])"
```

# 挂载google硬盘 #
```
from google.colab import drive
drive.mount('/content/drive')
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
