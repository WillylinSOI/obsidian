---
date : 2022-07-27
time : 11:32
aliases : 
- 雙邊濾波器
Tags : 
---
# Metadata
Title :: <br>
Status :: #🌱 <br>
Note Type :: #📥/📰<br>
Source URL ::
1. [雙邊濾波器](https://cg2010studio.com/2012/10/14/%E9%9B%99%E9%82%8A%E6%BF%BE%E6%B3%A2%E5%99%A8-bilateral-filter/)
2. [Bilateral Filters（双边滤波算法）原理及实现_Naruto_Q的博客-CSDN博客_bilateral filter](https://blog.csdn.net/piaoxuezhong/article/details/78302920)<br>
Author :: [[@happyMan]]<br>
Topics :: {筆記跟什麼主題有關連，用`[Topic],[Topic]`格式}<br>
Cover ::

---
# Evergreen
Question :: 這篇文章主要是在說什麼?
Answer ::何謂雙邊濾波器

---

# Summary
![[Pasted image 20220727115450.png]]
雙邊濾波器主要目的為在平滑區將影像模糊化，同時也能保留邊緣區域的特徵，而雙邊濾波器是根據兩個特點去調整權重
- 像素與像素之間的距離
- 像素色差

---

# Note

## 目的

**<span style="background:#7a3f1f">在平滑區將影像模糊化，同時也能保留邊緣區域的特徵</span>**，屬於一個非線性的過濾器

## 算式

每一個像素的結果來自式子：

![[Pasted image 20220727113617.png]]

變量的含義如下：

-   p：目標像素
-   q：目標像素周圍的一個像素
-   Ip：目標像素的顏色
-   Iq：目標像素周圍的一個像素的顏色
-   S：目標像素周圍的像素群
-   Gs：與標準偏差的高斯濾波器（加權的像素根據**距離**）
-   Gr：與標準偏差的高斯濾波器（加權的像素根據**像素色差**）

式子看似複雜，但其實只有兩部份，前半部就是以**<span style="background:#7a3f1f">距離</span>**決定權重的[[高斯濾波(Gaussian)主要是用消除noise，而離中央 pixel 距離愈遠的 pixel 對濾波結果影響愈小|高斯濾波]]的式子，然後加上後半部以<span style="background:#7a3f1f">像素色差</span>決定權重的式子**。
![[Pasted image 20220727115258.png]]
濾波算法中，目標點上的像素值通常是由其所在位置上的周圍的一個小局部鄰居像素的值所決定。在2D高斯濾波中的具體實現就是對周圍的一定範圍內的像素值分別賦以不同的高斯權重值，並在加權平均後得到當前點的最終結果。而這裡的高斯權重因子是利用兩個像素之間的空間距離（在圖像中為2D）關係來生成。通過高斯分佈的曲線可以發現，離目標像素越近的點對最終結果的貢獻越大，反之則越小

## Bilateral與高斯分布區別

假設目標源影像為下述左右區域分明的帶有噪聲的影像（由程式自動生成），藍色框的中心即為目標像素所在的位置，那麼當前像素處所對應的高斯權重與雙邊權重因子3D可視化後的形狀如後邊兩圖所示：

[![](https://cg2010studio.files.wordpress.com/2012/10/bilateral-filter-1.png?w=540&h=160 "Bilateral Filter (1)")

左圖為原始的噪聲影像；中間為高斯採樣的權重；右圖為**Bilateral**採樣的權重。從圖中可以看出Bilateral加入了相似程度分部以後可以將源影像左側那些跟當前像素差值過大的點給過濾掉，這樣就很好地保持了邊緣。為了更加形像地觀察兩者間的區別，使用Matlab將該圖在兩種不同方式下的高度圖3D繪製出來，如下：

![](https://cg2010studio.files.wordpress.com/2012/10/bilateral-filter-2.png?w=540&h=149 "Bilateral Filter (2)")

上述三圖從左到右依次為：雙邊濾波、原始影像、高斯濾波。從高度圖中可以明顯看出**Bilateral**和Gaussian兩種方法的區別，前者較好地保持邊緣處的梯度，而在高斯濾波中，由於其在邊緣處的變化是線性的，因而就使用連累的梯度呈現出漸變的狀態，而這表現在影像中的話就是邊緣失真。