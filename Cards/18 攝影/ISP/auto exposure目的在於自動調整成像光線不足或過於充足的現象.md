---
date : 2022-07-28
time : 10:54
aliases :
- 

Tags : 
---
# Metadata
Title :: <br>
Status :: #note_grow <br>
Note Type :: #type/📰<br>
Source URL :: [攝像頭自動曝光，自動對焦，自動白平衡，ISP，影象處理及色彩模型，色彩空間 - CodeBuug](https://www.codebuug.com/cs115324741/)<br>
Author :: [[]]<br>
Topics :: {筆記跟什麼主題有關連，用`[Topic],[Topic]`格式}<br>
Cover ::

---
# Evergreen
Question :: 這篇文章主要是在說什麼?
Answer ::甚麼是AE

---

# Summary
 自動調整成像光線不足或過於充足的現象
 
---

# Note

AE的基本概念：Auto Exposure即**自動曝光**，是**相機根據外界光線的強弱自動調整曝光量和增益，防止曝光過度或者不足的一種機制**。

![](https://i2.wp.com/img-blog.csdnimg.cn/20210330142808934.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2RqZmprajUy,size_16,color_FFFFFF,t_70)  
可見，AE的輸入為當前影像的亮度值Y，輸出為sensor的曝光時間和增益，isp增益和鏡頭光圈（如果鏡頭光圈可調）。當AE algorithm得到當前幀的亮度後，便會與target Y做比較，然後計算出下一次需要調整的引數，以便讓影像的亮度越來越接近target Y，如下所示(target並非一個固定值，而是一個range)。

![](https://i2.wp.com/img-blog.csdnimg.cn/20210330142822144.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L2RqZmprajUy,size_16,color_FFFFFF,t_70)