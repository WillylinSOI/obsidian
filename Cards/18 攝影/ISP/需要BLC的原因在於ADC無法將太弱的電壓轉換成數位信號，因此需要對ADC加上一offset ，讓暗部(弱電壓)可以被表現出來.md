---
date : 2022-07-28
time : 09:43
aliases :
- BLC

Tags : 
---
# Metadata
Title :: <br>
Status :: #note_grow <br>
Note Type :: #type/📰<br>
Source URL ::
1. [ISP-黑电平校正(BLC)洗脚水煮饺子的博客-CSDN博客_暗电流矫正](https://blog.csdn.net/xiaoyouck/article/details/72824534)
2. [ISP——BLC(Black Level Correction) - 知乎](https://zhuanlan.zhihu.com/p/386487708)<br>
Author ::
1. [[@洗脚水煮饺子]]
2. [[@猪猪爱吃鱼]]<br>
Topics :: {筆記跟什麼主題有關連，用`[Topic],[Topic]`格式}<br>
Cover ::

---
# Evergreen
Question :: 這篇文章主要是在說什麼?
Answer ::甚麼是BLC

---

# Summary
 需要BLC的原因在於ADC無法將太弱的電壓轉換成數位信號，因此需要對ADC加上一offset ，讓暗部(弱電壓)可以被表現出來
 
---

# Note

黑电平矯正（Black Level Correction）也就是黑色的最低点，以8bit数据来说，指在经过一定校准的显示装置上，没有一行光亮输出的视频信号电平。定义图像数据为0时对应的信号电平。

## 暗电流

暗电流（dark current），也称无照电流，指在没有光照射的状态下,在太阳电池、光敏二极管、光导电元件、光电管等的受光元件中流动的电流，一般由于载流子的扩散或者器件内部缺陷造成。目前常用的CMOS就是光电器件，所以也会有暗电流，导致光照为0的时候也有电压输出。

![](https://pic2.zhimg.com/80/v2-bb3450e48c26a9553cfcab978a75ccfd_720w.jpg)

如图是二极管的伏安特性曲线，从图中可以看出在反向截止区域电流并不是完全为0，而我们的COMS内部其实也是PN结构成的，所以符合该特性，并且光电二极管是工作在反向电压下，所以无光照是的这个微小电流就是暗电流。

## 原因
那么为什么要进行黑电平校正呢？原因如下：

1. CMOS传感器采集的信息经过一系列转换生成原始RAW格式数据。以8bit数据为例，单个pixel的有效值是0~255，但是**实际AD芯片（模数转换芯片）的精度可能无法将电压值很小的一部分转换出来**，因此，sensor厂家一般会在AD的输入之前加上一个固定的偏移量，使输出的pixel value在5（非固定）~255之间，**目的是为了让暗部的细节完全保留，当然同时也会损失一些亮部细节**，由于对于图像来说，我们的关注度更倾向于暗部区域，ISP后面会有很多增益模块（LSC、AWB、Gamma等），因此亮区的一点点损失是可以接受的。
   ![[Pasted image 20220728095239.png]]

2. sensor的电路本身会存在暗电流，导致在没有光线照射的时候，像素单位也有一定的输出电压，暗电流这个东西跟曝光时间和gain都有关系，不同的位置也是不一样的。因此在gain增大的时候，电路的增益增大，暗电流也会增强，因此很多ISP会选择在不同gain下减去不同的bl的值。
