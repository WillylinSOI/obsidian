---
date : 2022-07-19
time : 09:18
aliases :
- HSB
- HSL
- HSV
Tags : 
---
# Metadata
Title :: <br>
Status :: #note_grow <br>
Note Type :: #type/📰<br>
Source URL ::[HSL、HSV、HSB 有什么区别|酷客网](https://www.coolcou.com/color-space-and-color-model/diff-of-hsl-hsv-hsb.html)<br>
Author :: {作者名稱}<br>
Topics :: {筆記跟什麼主題有關連，用`[Topic],[Topic]`格式}<br>
Cover ::

---
# Evergreen
Question :: 這篇文章主要是在說什麼?
Answer :: 如何區分HSB、HSL、HSV

---

# Summary
## HSB
- 又稱為HSV
- H （Hue）: 色相
- S（Saturation） : 饱和度，即颜色的纯度，混入白色的量
- B（Brightness） : 明度，颜色的明亮程度，混入黑色的量
## HSL
- H （Hue）: 色相
- S（Saturation） : 饱和度，跟黑白沒有關係
-  L（Lightness）: 明度，混入黑白两种颜色

當兩者結合後就可以產生色錐模型

![HSL、HSV、HSB 有什么区别|left|1000](https://img.coolcou.com/colorspace/202108180815001.PNG "HSL、HSV、HSB 有什么区别")

---

# Note

HSL、HSV、HSB 有什么区别？ 首先， **HSB 和 HSV 是同一个东西，只是名称不同**，本文后面仅使用 `HSB`，当提到它的时候，也代表 `HSV`。

HSB 和 HSL 在字面意思上是一样的：

-   **H 指的是色相（Hue）**，就是颜色名称，例如“红色”、“蓝色”；
-   **S 指的是饱和度（Saturation），即颜色的纯度**；
-   **L（Lightness） 和 B（Brightness）是明度，颜色的明亮程度**

在原理和表现上，HSL 和 HSB 中的 H（色相） 完全一致，但二者的 S（饱和度）不一样， L 和 B （明度 ）也不一样：

-   **HSB 中的 S 控制纯色中混入白色的量**，值越大，白色越少，颜色越纯；
-   **HSB 中的 B 控制纯色中混入黑色的量**，值越大，黑色越少，明度越高
-   HSL 中的 S 和黑白没有关系，**饱和度**不控制颜色中混入黑白的多寡；
-   **HSL 中的 L 控制纯色中的混入的黑白两种颜色**。

## 顏色挑選器中比較
原理说完，结合实际应用场景看看。下面是 Photoshop 和 Affinity Designer 的拾色器

![HSL、HSV、HSB 有什么区别|left|1000](https://img.coolcou.com/colorspace/202108180815001.PNG "HSL、HSV、HSB 有什么区别")

两者分别使用了 HSB 和 HSL 颜色模型。两个拾色器都是 X 轴表示饱和度，越往右，饱和度越高；Y 轴表示明度，越往上明度越高。

先看 Photoshop 的 HSB 颜色模型拾色器，如下图所示，HSB 的 B（明度）控制纯色中混入黑色的量，越往上，值越大，黑色越少，颜色明度越高。

![HSL、HSV、HSB 有什么区别](https://img.coolcou.com/colorspace/202108180815002.PNG "HSL、HSV、HSB 有什么区别")

如下图所示，HSB 的 S（饱和度）控制纯色中混入白色的量，越往右，值越大，白色越少，颜色纯度越高。

![HSL、HSV、HSB 有什么区别](https://img.coolcou.com/colorspace/202108180815003.PNG "HSL、HSV、HSB 有什么区别")

接下来看 `Affinity Designer` 的 HSL 颜色模型拾色器。如下图所示，Y 轴明度轴，从下至上，混入的黑色逐渐减少，直到 50% 位置处完全没有黑色，也没有白色，纯度达到最高。继续往上走，纯色混入的白色逐渐增加，到达最高点变为纯白色，明度最高。

![HSL、HSV、HSB 有什么区别](https://img.coolcou.com/colorspace/202108180815004.PNG "HSL、HSV、HSB 有什么区别")

## 立體空間比較
![[Pasted image 20220719095025.png]]
![[Pasted image 20220719095041.png]]
HSL与HSB中的`HUE`（色相）涵义是相同的。但是SATURATION（饱和度）虽然用词一样，但是涵义（也就是算法）是截然不同的。另外需要注意的是HSL中L(Lightness亮度)与HSV/B中V（Value明度）/B（Brightness）是有区别的

## 明度與亮度對比
![[Pasted image 20220719095255.png]]

之后，由这二者会演变出来[[ISP/色錐模型是由HSL以及HSB混合產生的色彩模型|色錐模型]]
