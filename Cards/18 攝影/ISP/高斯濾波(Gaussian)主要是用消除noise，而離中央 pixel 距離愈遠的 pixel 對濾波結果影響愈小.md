---
date : 2022-07-27
time : 11:27
aliases :
- 高斯濾波
Tags : 
---
# Metadata
Title :: <br>
Status :: #🌱 <br>
Note Type :: #📥/📰<br>
Source URL ::
[高斯濾波及高斯卷積核C++實作 - 天天看點]([Fetching Title#2r5n](https://ithelp.ithome.com.tw/m/articles/10273833)
[iT 邦幫忙::一起幫忙解決難題，拯救 IT 人的一天](https://ithelp.ithome.com.tw/m/articles/10273833)
Author :: [[@林酷妹]]<br>
Topics :: {筆記跟什麼主題有關連，用`[Topic],[Topic]`格式}<br>
Cover ::

---
# Evergreen
Question :: 這篇文章主要是在說什麼?
Answer :: 何謂高斯分布

---

# Summary

![](https://img.marsnews.work/img/__Qf2AjLwojIjJCLyojI0JCLi0zaHRGcWdUYuVzVa9GczoVdG1mWfVGc5RHLwkzX39GZhh2csATMflHLwEzX4xSZz91ZsADMx8FdsYkRGZkRG9lcvx2bjxSa2EWNhJTW1AlUxEFeVRUUfRHelRHL2EzXlpXazxyayFWbyVGdhd3LcV2Zh1Wa9M3clN2byBXLzN3btg3PnVGcq5iNzQGO1MGN0ITMkhTY2EjY3UGO3M2NxYTZmZGNxgDZx8CX0AzLchDMxIDMy8CXn9Gbi9CXzV2Zh1WavwVbvNmLvR3YxUjL0M3Lc9CX6MHc0RHaiojIsJye.webp) ![right|500](https://img.marsnews.work/img/__Qf2AjLwojIjJCLyojI0JCLi0zaHRGcWdUYuVzVa9GczoVdG1mWfVGc5RHLwkzX39GZhh2csATMflHLwEzX4xSZz91ZsADMx8FdsYkRGZkRG9lcvx2bjxSa2EWNhJTW1AlUxEFeVRUUfRHelRHL2EzXlpXazxyayFWbyVGdhd3LcV2Zh1Wa9M3clN2byBXLzN3btg3PnVGcq5SNwEDMlVTY1YDMkFWM0MjMkVWZxcTN0MmNwAjYwYmMw8CX0AzLchDMxIDMy8CXn9Gbi9CXzV2Zh1WavwVbvNmLvR3YxUjL5M3Lc9CX6MHc0RHaiojIsJye.webp)
高斯濾波主要是用消除noise，高斯filter 具有以下幾個特點:
- 離中央 pixel 距離愈遠的 pixel 對濾波結果影響愈小
- σ越大，曲線分布越寬，模糊效果越差，反之亦然
- 捲積的尺寸越大表示模糊效果越好

---

# Note

## 目的
**高斯濾波是一種線性平滑濾波，<span style="background:#7a3f1f">适用于消除高斯噪聲</span>**，在圖像處理的降噪、平滑中應用較多，特别是對抑制或消除服從正态分布的噪聲非常有效。

高斯濾波的過程其實就是對整幅圖像進行權重平均操作的過程。濾波後圖像上每一個像素的灰階值大小，由其本身和鄰域内的其他像素共同決定。具體實作是：用一個大小為（2xN+1）的模板（或稱卷積核、掩模）依次掃描圖像中的每一個像素，用模闆确定的鄰域内像素的權重平均灰階替代模闆中心像素點的灰階值。

## 高斯分布及計算

### 一維、二維高斯分布

一維高斯函數表述為：

![](https://img.marsnews.work/img/9ZDMuAjOiMmIsIjOiQnIsISPrdEZwZ1Rh5WNXp1bwNjW1ZUba9VZwlHdsATOfd3bkFGazxCMx8VesATMfhHLlN3XnxCMwEzX0xiRGZkRGZ0Xy9GbvNGLpZTY1EmMZVDUSFTU4VFRR9Fd4VGdsYTMfVmepNHLrJXYtJXZ0F2dvwVZnFWbp1zczV2YvJHctM3cv1Ce-cmbw5SM1QjNiJTNwIzMykjNzUGN5cjM1gDOjF2NwI2YxMGZx8CX0AzLchDMxIDMy8CXn9Gbi9CXzV2Zh1WavwVbvNmLvR3YxUjL4M3Lc9CX6MHc0RHaiojIsJye.webp)

對應圖形：

![](https://img.marsnews.work/img/9ZDMuAjOiMmIsIjOiQnIsISPrdEZwZ1Rh5WNXp1bwNjW1ZUba9VZwlHdsATOfd3bkFGazxCMx8VesATMfhHLlN3XnxCMwEzX0xiRGZkRGZ0Xy9GbvNGLpZTY1EmMZVDUSFTU4VFRR9Fd4VGdsYTMfVmepNHLrJXYtJXZ0F2dvwVZnFWbp1zczV2YvJHctM3cv1Ce-cmbw5SOxczM0ATNhJTO5gTY5gDOiRzYklzY1UGMlZGMiJDZm9CX0AzLchDMxIDMy8CXn9Gbi9CXzV2Zh1WavwVbvNmLvR3YxUjL0M3Lc9CX6MHc0RHaiojIsJye.webp)

二維高斯函數表述為：

![](https://img.marsnews.work/img/__Qf2AjLwojIjJCLyojI0JCLi0zaHRGcWdUYuVzVa9GczoVdG1mWfVGc5RHLwkzX39GZhh2csATMflHLwEzX4xSZz91ZsADMx8FdsYkRGZkRG9lcvx2bjxSa2EWNhJTW1AlUxEFeVRUUfRHelRHL2EzXlpXazxyayFWbyVGdhd3LcV2Zh1Wa9M3clN2byBXLzN3btg3PnVGcq5SNwEDMlVTY1YDMkFWM0MjMkVWZxcTN0MmNwAjYwYmMw8CX0AzLchDMxIDMy8CXn9Gbi9CXzV2Zh1WavwVbvNmLvR3YxUjL5M3Lc9CX6MHc0RHaiojIsJye.webp)

![](https://img.marsnews.work/img/__Qf2AjLwojIjJCLyojI0JCLi0zaHRGcWdUYuVzVa9GczoVdG1mWfVGc5RHLwkzX39GZhh2csATMflHLwEzX4xSZz91ZsADMx8FdsYkRGZkRG9lcvx2bjxSa2EWNhJTW1AlUxEFeVRUUfRHelRHL2EzXlpXazxyayFWbyVGdhd3LcV2Zh1Wa9M3clN2byBXLzN3btg3PnVGcq5iNzQGO1MGN0ITMkhTY2EjY3UGO3M2NxYTZmZGNxgDZx8CX0AzLchDMxIDMy8CXn9Gbi9CXzV2Zh1WavwVbvNmLvR3YxUjL0M3Lc9CX6MHc0RHaiojIsJye.webp)

### 高斯計算
**Sigma 值越大，權重值向外下降幅度越平滑。**  
（越接近中心，取值越大 ; 越遠離中心，取值越小。）

計算平均值的時候，我們只需要將 "中心點" 作為原點，其他點按照其在高斯分佈曲線上的位置**分配權重**，就可以得到他的加權平均值。

![](https://i.imgur.com/oULORDL.png)

經過Gaussian filter ![](https://i.imgur.com/1Hews6M.png)

> **高斯濾波器越靠中心的權重值越高，且 filter 內的權重值由中心向外平滑下降 → <span style="background:#7a3f1f">離中央 pixel 距離愈遠的 pixel 對濾波結果影響愈小</span>**。

影像輸出：  
![](https://i.imgur.com/xM8m375.png)

將每個點乘以自己的權重值，再將這9個值加起來，就是中心點的高斯模糊的值了！

## 一些重要特性說明：

1. 一維二維高斯函數中μ是服從正态分布的随機變量的均值，稱為期望或均值影響正态分布的位置，實際的圖像處理應用中一般取μ=0；σ是标準差，σ^2是随機變量的方差，σ定義了正态分布資料的離散程度，σ越大，資料分布越分散，σ越小，資料分布越集中。在圖形或濾波效果上表現為：**<span style="background:#7a3f1f">σ越大，曲線越扁平，高斯濾波器的頻帶就越寬，平滑程度就越好，σ越小，曲線越瘦高，高斯濾波的頻帶就越窄，平滑程度也越弱</span>**；

2. 二維高斯函數具有旋轉對稱性，即濾波器在各個方向上的平滑程度是相同的．一般來說，一幅圖像的邊緣方向是事先不知道的，是以，在濾波前是無法确定一個方向上比另一方向上需要更多的平滑．旋轉對稱性意味着**高斯平滑濾波器在後續邊緣檢測中不會偏向任一方向**；

3. 高斯函數是單值函數。這表明，高斯濾波器用像素鄰域的權重均值來代替該點的像素值，而每一鄰域像素點權值是随該點與中心點的距離單調增減的。這一性質是很重要的，因為邊緣是一種圖像局部特征，如果平滑運算對離算子中心很遠的像素點仍然有很大作用，則平滑運算會使圖像失真，換言之就是**高斯濾波器越靠中心的權重值越高，且 filter 內的權重值由中心向外平滑下降 → 離中央 pixel 距離愈遠的 pixel 對濾波結果影響愈小**

4. 相同條件下，**<span style="background:#7a3f1f">高斯卷積核的尺寸越大，圖像的平滑效果越好，表現為圖像越模糊，同時圖像細節丢失的越多；尺寸越小，平滑效果越弱，圖像細節丢失越少</span>**
