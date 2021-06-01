---
title: "手动制作乡镇地图的geojson"
date: 2021-05-31T17:21:12+08:00
---

## 一、准备阶段

在做乡镇级地图之前需要先知道几个网站并下载一个bigemap的软件，下面来分别介绍一下这些东西的用处

## 1. [DATAV.GeoAtlas](http://datav.aliyun.com/tools/atlas/#&lat=30.332329214580188&lng=106.72278672066881&zoom=3.5)

是阿里推出的一个用于获取全国、各省、各市以及个县级市详细地图信息的json文件

> http://datav.aliyun.com/tools/atlas/#&lat=30.332329214580188&lng=106.72278672066881&zoom=3.5

![在这里插入图片描述](https://img-blog.csdnimg.cn/20210414142112229.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NpbmF0XzQxOTA0NDEw,size_16,color_FFFFFF,t_70)

**上面截图左边部分，是获取json文件的API，在浏览器上打开该链接即可获取json文件，json API分两种：**

- 一种是不包含子区域（以郑州为例：只显示郑州的范围，不会详细的显示郑州内有哪些区，哪些县级市的地理范围）
- 一种是包含子区域（以郑州为例：既显示郑州的地理范围，也显示郑州下面区、县的地理范围，但是不会显示乡镇，以上图为例）

## 2.[bigemap](http://www.bigemap.com/reader/download/)

这是一个可以获取到街道、乡镇的软件。

> http://www.bigemap.com/reader/download/

打开链接地址，然后选择下载，并安装该软件
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210414142426305.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NpbmF0XzQxOTA0NDEw,size_16,color_FFFFFF,t_70)

安装完成后打开，输入要获取要获取地图的乡镇（以林州的横水镇为例）
然后点击导出边界按钮生成该乡镇的KML文件
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210414142454308.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NpbmF0XzQxOTA0NDEw,size_16,color_FFFFFF,t_70)

## 3.[geojson.io](http://geojson.io/#map=2/20.0/0.0)

可以在这个网站上生成我们的乡镇级地图json。

> http://geojson.io/#map=2/20.0/0.0

## 二、制作乡镇级地图json

制作步骤总共份三步：

1. 获取市地图（这一步可以不要，直接用镇级模块就拼成上级模块了）
2. 获取市下面乡镇的地图
3. 合并

第一步.在 DATAV.GeoAtlas上下载市的json信息，然后放到geojson.io中

第二步，在bigemap文件中输入依次选择市下面的乡镇并生成kml文件
![在这里插入图片描述](https://img-blog.csdnimg.cn/2021041414523438.png)

第三步、在geojson.io中分别导入这些kml文件

以包头市固阳县的镇级的各个镇，kml文件倒入为例，如下图所示

***（如果只是县的话就可以不用先导入县级地图了，直接导入各个镇级就可以，要不然会有两层地图）***
![在这里插入图片描述](https://img-blog.csdnimg.cn/20210414142920762.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NpbmF0XzQxOTA0NDEw,size_16,color_FFFFFF,t_70)

4.导入完成后，在geojson.io中把json文件复制下来即可，



