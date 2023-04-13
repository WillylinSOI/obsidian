---
date : 2022-07-27
time : 18:16
aliases :
- 感光度
- ISO

Tags : 
---
# Metadata
Title :: <br>
Status :: #🌱 <br>
Note Type :: #📥/📰<br>
Source URL :: 
1. [数字成像系统概述|Camera](http://camera.geek-docs.com/camera-isp/digital-camera-system-intro.html)
2. [曝光三要素 (曝光三角)：光圈、快門、ISO | 給初學者的 5 分鐘指南 - Tim Ting Photography](https://timtingphotography.com/exposure-triangle/)<br>
Author :: 
1. 
2.  [[@Tim&Ting]]<br>
Topics :: {筆記跟什麼主題有關連，用`[Topic],[Topic]`格式}<br>
Cover ::

---
# Evergreen
Question :: 這篇文章主要是在說什麼?
Answer ::

---

# Summary
ISO 在傳統底片中所代表的是底片的感光能力，但是在數位相機中所代表的意義是sensor gain ，sensor gain 越大，成像就越亮,ISO有以下幾個特點:

- ISO 越高 : 圖片越亮
- ISO 越低 : 圖片越暗

- ISO 越高 : 噪點越多
- ISO 越低 : 噪點越少

---

# Note

感光度一詞是源自最早期的底片相機，由於不同種類的底片對光有不同的反應性，因此國際標準組織以 ISO Speed 來分類底片對光的靈敏度 (包括最早期的黑白底片標準 ISO-6、彩色底片標準的 ISO-5800)。**一般 ISO Speed (簡稱 ISO) 越高的底片代表感光能力越好**、ISO 越低的底片則是對光相較不敏感，而這概念也就一直沿用至今天的數位相機上。因此高 ISO 代表感光能力越高，相片越亮；反之亦然。

一般而言我們會以 ISO 50 , ISO 100 , ISO 200 , ISO 400 , ISO 800 , ISO 1600 , ISO 3200 , ISO 6400  來表示相機的感光度。

ISO 的概念也非常好理解，**數字高一倍代表感光度提高一倍**。舉例來說，ISO 100 的感光能力較 ISO 200 的還要低一倍，因此當所有參數和環境都一樣的狀況下，ISO 100 的照片會比 ISO 200 的照片暗一倍，如果要將它調整成和 ISO 200 一樣的曝光度，就需要將光圈增大一級、或是將快門速度延長一倍；同理，今天如果要透過調整感光度將 ISO 400 秒的相片亮度加倍，則可以將 ISO 上調一倍至 ISO 800，使得感光元件的受光能力提高一倍。

-   **<span style="background:#7a3f1f">ISO 越高 → 感光能力越高 → 照片越亮</span>** ^ghb4sm
-   **<span style="background:#7a3f1f">ISO 越低 → 感光能力越低 → 照片越暗</span>** ^vi5kgd


## ISO 的影響 - 相片品質 & 噪點

影响成像质量最核心的还是图像传感器（Sensor）， Image Sensor是一种将光学信号（影像）转换成电子信号的设备，广泛应用在数码相机和其他电子光学设备中。主要分为感光耦合元件（Charge-coupled device CCD）和互补式金属氧化物半导体有源像素传感器（CMOS Complementary Metal-Oxide-Semiconductor）两种。

CMOS Sensor上面排列着上千万的像素，

![CMOS Sensor](http://img.geek-docs.com/camera/basic/camera-flow-14.png "CMOS Sensor")

每个像素里面的光电二极管在遇到光时就会因为光电效应积累一定数量的电荷，将光信号转换为电信号。

![像素中的光电二极管](http://img.geek-docs.com/camera/basic/camera-flow-15.png "像素中的光电二极管")

由于光电二极管无法识别颜色，所以不同像素上还要覆盖红绿蓝三种滤光片。

![滤光片](http://img.geek-docs.com/camera/basic/camera-flow-16.png "滤光片")

通常红（R）绿（G）蓝（B）是按照1:2:1的比例设置，以模仿对绿光敏感的人眼，这种成为Bayer Filter。

![RGGB](http://img.geek-docs.com/camera/basic/camera-flow-17.png "RGGB")
## sensor曝光
![](https://pic4.zhimg.com/80/v2-4b48c5d1b26b1f66e139eec84f76514f_720w.jpg)

在曝光时照射到传感器上的光，可以用光子来描述。当每个光子到达传感器上的特定层时，光子就会产生一个电子。电子数量的单位是“e-”。一旦曝光时间结束，photosite电路中的ADC(模拟数字转换器)计算每个photosite中有多少电子，并将其转换为ADUs。在这种电子量化中，我们可以说，ADC使用转换因子“M”(来自乘法器)，以“ADU/e-”为单位，乘以电子数，得到相应的ADU值。在曝光开始前，所有的photosites将重置。“M”大小仅取决于相机的ISO设置。**当ISO值越高，“M”就会越高**，制造相同ADU需要的电子就会越少，光敏越高。

击中每个photosite的光子通量与光的强度成比例。拍摄场景中较暗的区域将对应于较低的电子数，从而导致较低的ADU值，而较亮的区域将对应于较高的ADU值。我们将在曝光时间结束时，用符号“EL”(电子)和单位e-表示每个照片中的电子数。到目前为止，我们的传感器模型是:

![](https://pic3.zhimg.com/80/v2-bde1eb28beb029e9353fa10fb283ea1e_720w.jpg)

## iso 對噪點的影響
感光度越高就对光线越敏感，照片也越亮。
![ISO](http://img.geek-docs.com/camera/basic/camera-flow-19.png "ISO")

但是通过拉高ISO，每个像素都会因为电路干扰产生固定的噪音信号，在高ISO下，噪音信号也会更大，出现噪点。

噪点问题可以通过增大像素面积来缓解，在有噪音信号的情况下，大像素可以收集更多有用的光信号，增加信噪比，从而减少噪点。


![](https://timtingphotography.com/wp-content/uploads/2021/10/05-13-Image-Noise.jpg "05-13 Image Noise")

[圖片來源]：[維基百科](https://zh.wikipedia.org/wiki/%E5%99%AA%E7%82%B9)

那麼 ISO 的高低對噪點和相片品質的影響有多大呢？大家可以參考以下 Tim & Ting 的教學示範圖 (為了讓差異明顯化，我們以非常極端的例子來做說明)：從無尾熊身上的毛髮清晰度，大家可以明顯比較出高低 ISO 的成像品質差異；而從圖片下方的桌子或後方的背景，則可以清楚感受到 ISO 高低如何影響噪點的多寡。

因此大家才會說 ISO 越高照片品質越糟、ISO 盡可能越低越好。但是也千萬記得，有些時候為了維持快門速度、避免手震而拍出模糊不清楚的畫面，適時的提高 ISO、犧牲一點相片品質是必須的，否則畫質再佳，只要是晃動不清的照片都不能算是合格的照片。

![](https://timtingphotography.com/wp-content/uploads/2021/10/05-14-ISO_vs_noise.jpg "05-14 ISO_vs_noise")

-   **ISO 越高 → 感光能力越高 → 噪點越多、照片品質越差**
-   **ISO 越低 → 感光能力越低 → 噪點越少、照片品質越好**

![[ISP/快門、光圈、ISO 是所謂的曝光三要素，其最根本的原理就是影響相片的亮度、連續程度以及噪點程度#ISO 感光度 曝光的交互關係]]