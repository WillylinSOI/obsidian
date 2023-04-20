---
date : 2022-07-28
time : 11:24
aliases :
- noise 
- read noise 
- prnu noise 
- shot noise 

Tags : 
---
# Metadata
Title :: <br>
Status :: #note_grow <br>
Note Type :: #type/📰<br>
Source URL :: 
1. [从0开始建立相机传感器的噪音模型-理论篇 - 知乎](https://zhuanlan.zhihu.com/p/363366030)
2. [暗光下拍攝應使用低 ISO 再後期提亮，還是高 ISO？ - GetIt01](https://www.getit01.com/p20190322131462389/)<br>
Author :: 
1. [[@BruceLIU]]<br>
Topics :: {筆記跟什麼主題有關連，用`[Topic],[Topic]`格式}<br>
Cover ::

---
# Evergreen
Question :: 這篇文章主要是在說什麼?
Answer :: 說明noise 的種類以及產生原理

---

# Summary
noise 大致上分三種，shot  noise、 PRNU noise 以及read noise
shot  noise : 因自然中光子的分佈不平均，導致的noise 
prun noise : 每個像素的感光程度不一所造成的noise 
read noise : 在adc轉換中所產生的noise 

---

# Note

图像噪声是在图片每个通道（RGB，RGGB，RYYB，YUV。。。）像素中亮度的随机变化，像素的期望本应该是均匀的或者是变化平缓的（如Total Variation的去噪原理）。在黑暗区域，当图像被放大仔细检查时，它更容易被注意到。噪声可以描述为由“亮度噪声”和“颜色噪声”组成，其中“亮度噪声”是保持整体色调基本一致的噪声，“色度噪声”中也有色调的变化。然而，由于噪声是随机变化的，其存在的原始图像总是涉及到这两种类型的噪声。请看下面的例子：

![](https://pic3.zhimg.com/80/v2-bc932233032234baee4958e55a8c797a_720w.jpg)
亮度加色度噪声

![](https://pic1.zhimg.com/80/v2-6eed153bb7d9227c3b78a7913be612f4_720w.jpg)
只有亮度噪声

noise 分為三種，shot  noise、 PRNU noise 以及read noise 

## shot noise 散粒雜訊
noise 來源自光子的分布不平均
![[ISO 在傳統底片中所代表的是底片的感光能力，但是在數位相機中所代表的意義是sensor gain#sensor曝光]]

它是由“EL”表示的电子数。**即使是在完全均匀的光照下，每个photosite的电子数也不一样**。光子数是一个随机变量而不是一个常量;图像表面上的这些不同的值就是所谓的光子散粒噪声。为了理解这一点，让我们想象许多相同的杯子放在相同的雨下，雨结束时没有杯子溢出

![](https://pic1.zhimg.com/80/v2-e656bd884ddc21aaf39103535513497c_720w.jpg)

如果在雨后，我们检查一下杯子，我们会发现每个杯子收集的雨水与其他杯子并没有太大的不同。但如果我们非常精确地测量，我们会发现每个杯子里的雨量是不同的。类似的情况也发生在光子撞击photosite的过程中。即使光子通量是常数,光子的数量,每个photosite生产的电子不是一个常数,而是一个随机变量遵循泊松分布。泊松过程被描述为“在固定的时间和/或空间内发生的离散事件的给定数量，这些事件以已知的平均速率发生，独立于自上一个事件以来的时间”。
![[Pasted image 20220728113846.png]]

## read noise 
模擬電路部分產生的讀出雜訊通常稱為前端讀出雜訊(Upstream Read Noise)，ADC轉換之後，數字部分產生的讀出雜訊稱為後端讀出雜訊(Downstream Read Noise)。

![](https://i1.wp.com/pic2.zhimg.com/50/v2-d5c0219737aaa3334dee5e38166753bb_hd.jpg)

在[APS (from Active Pixel Sensor)](https://zhuanlan.zhihu.com/p/363366030/h%3Cb%3Et%3C/b%3Etp://e%3Cb%3En%3C/b%3E.wiki%3Cb%3Ep%3C/b%3Eedia.org/wiki/Active_pixel_sensor)传感器中，每个photosite连接一个电路，将光子撞击产生的电子的电荷转换为电压，并将其作为输入到A/D转换器。由于这条处理线不是完美的，ADC的输出并不完全与光子发射的电子数量成比例。镜头盖上拍摄的照片，**从ADC出来的ADU总是有一个偏差或基线**（为了保留暗区信号，在ADC之前会有一个黑电平）。这种噪声称为read noise。
![[Pasted image 20220728114418.png]]
換句話說就是模擬信號（下圖上部分藍線）轉數字信號（下圖上部分紅線）時的Quantization noise。因為比特深度是不連續的，我們常見的12bit raw文件只有4096個亮度階段，那很多細節就淹沒了，尤其是暗部的，這其中產生的錯誤，就叫做quantization noise（下圖下部分藍線）
![[Pasted image 20220728115947.png]] 

 ## PRNU Noise

**并不是所有的photosites都是一样的，对光线的敏感度也不是完全一样的**。每个感光点上的微透镜（收集产生的电子的层）、A/D转换器和其他传感器电路元件在制造过程中并不是完全相同的。换句话说，在我们的模型中的“M”项，对于每个照片站点来说不是完全相同的值。相反，“M”是每个photosites的一个属性。这种情况称为像素响应不均匀性(PRNU)。

考虑到这一点，我们将因子“M”替换为“Mp”:我们将使用下标“p”来表示在每个给定的传感器位置“p”上，“M”随着每个photosites的变化而变化。

![](https://pic2.zhimg.com/80/v2-e0ff21db1482d8a8316d324bb4d50829_720w.jpg)

我们必须注意到，“Mp”的灵敏度变化并不是有意为之，它们是在不同像素点之间的随机变化。在这个意义上，Mp是一个关于传感器表面的随机变量。这个事实用上面公式的表示法表示——用粗体“Mp”表示。然而，我们将考虑到每一个像素，随着时间的推移，始终具有相同的“Mp”值。这意味着“Mp”，对于每一张照片，在保持相同的ISO速度(感光片的灵敏度随着ISO速度的变化而变化)的时间(在拍摄之间)是一个常数。