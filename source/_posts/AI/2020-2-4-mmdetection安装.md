---
title: mmdetection安装
date: 2020-2-4 11:53:7
tags: 
- demo
categories:
- [AI,框架]
---
# mmdetection安装 #
```
# 环境安装 
conda create -n mmdetection python=3.7 -y
conda activate mmdetection
# pytorch安装 
conda install pytorch==1.2.0 torchvision==0.4.0 cudatoolkit=10.0 -c pytorch
# mmcv安装
git clone https://github.com/open-mmlab/mmcv
cd mmcv
pip install .
# pycoco安装
pip install "git+https://github.com/philferriere/cocoapi.git#egg=pycocotools&subdirectory=PythonAPI"
# Cython安装
pip install Cython==0.29.14
# mmdetection安装
git clone https://github.com/open-mmlab/mmdetection.git
cd mmdetection
pip install -r requirements.txt
python setup.py develop
```
- 检查
>pip list

包名 mmdet                     1.0+4ec5b80               dev_0    <develop>



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
