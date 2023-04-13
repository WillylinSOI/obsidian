---
date : 2022-07-28
time : 13:36
aliases :
- demonsaic

Tags : 
---
# Metadata
Title :: <br>
Status :: #🌱 <br>
Note Type :: #📥/📰<br>
Source URL :: [ISP图像处理之Demosaic算法及相关 - 知乎](https://zhuanlan.zhihu.com/p/170610956)<br>
Author :: [[@AomanHao]]<br>
Topics :: {筆記跟什麼主題有關連，用`[Topic],[Topic]`格式}<br>
Cover ::

---
# Evergreen
Question :: 這篇文章主要是在說什麼?
Answer ::解釋Demosaic

---

# Summary
由於現今sensor大多是用bayer式的CFA，這樣的排列方是會使輸出的圖片呈現馬賽克式的圖片，因為每個pixel都只有單色而以，所以需要ISP中的demosaic元件，根據演算法去模擬出單個pixel中的其他顏色

---

# Note

現在相機sensor主要是利用bayer 排列來接收顏色
![RGGB 色彩濾鏡](https://hojenjen.com/wp-content/uploads/20200217220314_26.jpg "[教攝影113] 什麼是 RGGB 色彩濾鏡 ? 認識 RGGB 色彩濾鏡，數位相機如何補捉色彩")

当光线通过 [[ISP/拜耳滤波器(bayer)主要的目的在於讓每個感光元件都只接收特定一種的顏色，這樣更接近人眼也可以降低成本|bayer]]型 CFA（Color Filter Arrays） 阵列之后， 单色光线打在传感器上，每个像素都为单色光，理想的Bayer 图是一个较为昏暗的马赛克图。（见感光元件成像示意图（2））。

根据sensor上感知的光线强度，再结合对应滤光片颜色排列就可以估计出 sensor输出的彩色图像（见bayer滤镜输出图像示意图（3））

首先需要说明的就是demosaiced并不是和字面的意思一样是为了去除电影中的一些打马赛克的图像，而是数字图像处理中用来从不完整的color samples插值生成完整的color samples的方法(因为bayer pattern看起来像一个个马赛克，因此称为去马赛克)。**在sensor端通常需要使用CFA滤镜来得到Bayer pattern，而在后面的处理中需要把bayer pattern变成完整的RGB444(真彩色)图像。**在ISP中需要有这么一个模块来做。

![](https://pic2.zhimg.com/80/v2-3bad04fd5de7f55583e3af9cd69feef5_720w.jpg)