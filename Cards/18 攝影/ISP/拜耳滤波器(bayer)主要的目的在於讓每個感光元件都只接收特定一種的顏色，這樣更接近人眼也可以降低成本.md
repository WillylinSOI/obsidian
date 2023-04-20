---
date : 2022-07-28
time : 13:19
aliases :
- 拜耳滤波器
- bayer
- CFA

Tags : 
---
# Metadata
Title :: <br>
Status :: #note_grow <br>
Note Type :: #type/📰<br>
Source URL :: [ISP图像处理之Demosaic算法及相关 - 知乎](https://zhuanlan.zhihu.com/p/170610956)<br>
Author :: [[@AomanHao]]<br>
Topics :: {筆記跟什麼主題有關連，用`[Topic],[Topic]`格式}<br>
Cover ::

---
# Evergreen
Question :: 這篇文章主要是在說什麼?
Answer ::說明拜耳滤波器(bayer)

---

# Summary
拜耳滤波器(bayer)主要的目的在於讓每個感光元件都只接收特定一種的顏色，這樣更接近人眼也可以降低成本

---

# Note

![RGGB 色彩濾鏡](https://hojenjen.com/wp-content/uploads/20200217220314_26.jpg "[教攝影113] 什麼是 RGGB 色彩濾鏡 ? 認識 RGGB 色彩濾鏡，數位相機如何補捉色彩")

感光元件功用，只是在記錄「光線明暗強弱」資訊，並不包含色彩資訊，所以需要在感光元件上鋪上一層帶有顏色的濾色片，如上圖所示，上方有藍、綠、紅相間的濾色片，**這個濾色片結構，我們稱為 RGGB 拜爾濾色片**也稱為彩色滤波阵列（Color Filter Arrays，CFA）。

目前最常用的滤镜阵列是棋盘格式的， 已经有很多种类的， 其中绝大多数的摄像产品采用的是原色贝尔模板彩色滤波阵列（Bayer Pattern CFA）。R、G、B 分别表示透红色、透绿色和透蓝色的滤镜阵列单元。由于人的视觉对绿色最为敏感，所以在 Bayer CFA 中G分量是 R和B 的二倍，在每个像素点上只能获取一种色彩分量的信息，然后根据该色彩分量的信息通过插值算法得到全色彩图像。
![[Pasted image 20220728133426.png]]

而這拜爾濾色片，包含了 **25% 的藍、25% 的紅，以及 50% 的綠**所組成矩陣結構，所以稱為 RGGB 濾色片。

![[Pasted image 20220728131941.png]]

不同顏色的濾色片，能吸收對應的光線顏色，最後將光線資訊記錄在感光元件上的像素上，使得每一個感光像素，除了記錄光線強弱資訊外，同時也記錄一種顏色資訊。