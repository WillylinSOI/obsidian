---
date : 2022-07-28
time : 10:12
aliases :
- lens-shading 
- LSC

Tags : 
---
# Metadata
Title :: <br>
Status :: #🌱 <br>
Note Type :: #📥/📰<br>
Source URL :: [ISP 对 Sensor 的 Lens-Shading 校正 - 大大通](https://www.wpgdadatong.com/tw/blog/detail?BID=B2168)<br>
Author :: [[@开局一个碗]]<br>
Topics :: {筆記跟什麼主題有關連，用`[Topic],[Topic]`格式}<br>
Cover ::

---
# Evergreen
Question :: 這篇文章主要是在說什麼?
Answer :: lens shading 是如何造成的

---

# Summary
Lens Shading Correction需要的原因在於光線透過[ICR](紅外線濾光片(IR%20cut)切換器可以阻擋紅光進入sensor.md)中的凸透鏡使得光線彎曲，會造成luma shading 或是color shading 兩種現象
- luma shading : 中間的光線比周圍的光線多，導致產生暗角的問題
- color shading : 光線經過透鏡後折射的角度不一樣，導致顏色偏差的問題

---

# Note

由于 lens 的光学特性，**镜头对于光学折射不均匀导致的镜头周围出现阴影的情况。shading可以细分为 luma shading 和 color shading**，镜头阴影校正（Lens Shading Correction）是为了解决由于 lens 的光学特性。

## luma shading  
由于 Lens 的光学特性，Sensor 影像区的边缘区域接收的光强比中心小，所造成的**中心和四角亮度不一致的现象**。镜头本身就是一个凸透镜，由于凸透镜原理，中心的感光必然比周边多。表现为四周的亮度相对于中心的亮度偏低,如图所示：

 ![](https://edit.wpgdadawant.com/uploads/news_file/blog/2020/2592/tinymce/1.png)

luma shading：会造成图像边角偏暗，就是所谓的暗角。
![](https://edit.wpgdadawant.com/uploads/news_file/blog/2020/2592/tinymce/3.png)  
 luma shading 引起的四周偏暗成像  
![](https://edit.wpgdadawant.com/uploads/news_file/blog/2020/2592/tinymce/4.png)

## chrom/color shading
由于各种颜色的波长不同，经过了透镜的折射，折射的角度也不一样，因此会造成 color shading 的现象，表现为**四周和中心颜色有偏差的问题**,这也是为什么太阳光经过三棱镜可以呈现彩虹的效果。  
  
![](https://edit.wpgdadawant.com/uploads/news_file/blog/2020/2592/tinymce/2.png)

color shading：中心和四周颜色不一致，体现出来一般为中心或者四周偏色。这种现象当然随着外界色温的变化 所表现出来的效果不同，如图所示：  
  
![](https://edit.wpgdadawant.com/uploads/news_file/blog/2020/2592/tinymce/5.png)

color shading 引起的成像中间偏红  
![](https://edit.wpgdadawant.com/uploads/news_file/blog/2020/2592/tinymce/6.png)