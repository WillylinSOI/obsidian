# I. 每日金句
![tp.web.random_picture](https://images.unsplash.com/source-404?fit=crop&fm=jpg&h=800&q=60&w=1200) <br>
> He has no enemies, but is intensely disliked by his friends.
> — <cite>Oscar Wilde</cite>

>中文翻譯:
>他没有敌人，但他的朋友们非常不喜欢他。
---

# II. 回顧
```note-brown
開啟回顧，回想昨天以及去年的今天發生了什麼
```

## 明天
[[2022-09-13 daily note]]

## 一年前的今天
[[2021/09/2021-09-12 daily note]]

## 昨天
[[2022-09-11 daily note]] 


---
# III. 每日活動
今天是週一
```ActivityHistory
/

```

---
# IV. 每日感恩日記
## 早晨紀錄
### 精華
```note-brown
今天的人生精華是甚麼?
```
```note-red
要注意是否有精力完成
```
- 運動!!

### 目標確立
```note-brown
你想成為甚麼樣的人?
```
- 我想成為努力的人

### News 新聞
```note-brown
今天發生了什麼重大的事情、看到了甚麼新聞?有甚麼感想?
```
- 沒有看到新聞...

## 晚間紀錄
### 文章
```note-brown
每天至少閱讀1篇文章，並作筆記
```

```note-blue
生產力、知識型文章
```
- 沒有..

### 心靈
```note-brown
今天有哪 3 件值得感恩的事情?
```
- 感謝老闆給我好吃的晚餐
- 感謝[@humphrey](@humphrey.md)教導我如何coding得更好
- 感謝午餐店阿姨給我加肉!!

### 弱連結
```note-brown
今天是否「日行一善」，幫助了任何人?
```
- 我幫[[@Sophia]]開門，但是我幫忙的不夠快，每一天都要盡力幫忙別人

### 親密關係
```note-brown
今天要如何和另一半/家人/朋友表達關心、互動? 或是學習關於兩性之間的知識?
```
- 沒有

### 健康 (如何吃? 如何動? 如何靜?)
```note-brown
我做了哪些事情讓自己休息及放鬆? 做了甚麼運動?
```
- 拉筋
- 做腹肌訓練
- 明天開始要開始看運動相關書籍

### 財務
```note-brown
今天購買了哪些東西 ?
```
- 合力他命維他命650

### 生活產出
```note-brown
本日 AAR (After Action Review)
```

#### 1. 今天完成了什麼事情？ 
- 完成lec驗證
- 完成bilateral ftr 修改
- 看了至少半小的make file pdf

#### 2. 選一件讓我有感覺、有啟發的事情 
- 沒有

#### 3. 我從過程中學習到什麼事情 ? 
- 我在lec時發現我的code跑到一半會當掉，後還我發現是coding style的問題，但原因未知，以下為我在進行pipe line coding 時發現有些coding style 是會使lec當掉的，而有 些是可以通過的:
##### error coding
###### 1

```verilog
generate 
  for(conv_i=0;conv_i<KRN_HSZ;conv_i=conv_i+1) begin : data_convolution  //convolution need to wait 3T (pipe0 + pipe1)
assign data_conv_nxt[conv_i] = {12'h0,i_data_que[0][DATA_WD*(KRN_HSZ_SHIFT+2)-1:0+DATA_WD*(KRN_HSZ_SHIFT+1)]} * {12'h0,flt_weight[conv_i*KRN_VSZ + 0]} +  
                               {12'h0,i_data_que[1][DATA_WD*(KRN_HSZ_SHIFT+2)-1:0+DATA_WD*(KRN_HSZ_SHIFT+1)]} * {12'h0,flt_weight[conv_i*KRN_VSZ + 1]} + 
                               {12'h0,i_data_que[2][DATA_WD*(KRN_HSZ_SHIFT+2)-1:0+DATA_WD*(KRN_HSZ_SHIFT+1)]} * {12'h0,flt_weight[conv_i*KRN_VSZ + 2]} + 
                               ((conv_i==0) ? 20'd0 : data_conv[conv_i-1]);
  end 
endgenerate
```
###### 2
```verilog
assign data_conv_nxt[0] = i_data_que[0][DATA_WD*(KRN_HSZ_SHIFT+2)-1:0+DATA_WD*(KRN_HSZ_SHIFT+1)] * flt_weight[0] +  
                          i_data_que[1][DATA_WD*(KRN_HSZ_SHIFT+2)-1:0+DATA_WD*(KRN_HSZ_SHIFT+1)] * flt_weight[1] + 
                          i_data_que[2][DATA_WD*(KRN_HSZ_SHIFT+2)-1:0+DATA_WD*(KRN_HSZ_SHIFT+1)] * flt_weight[2];

assign data_conv_nxt[1] = (i_data_que[0][DATA_WD*(KRN_HSZ_SHIFT+2)-1:0+DATA_WD*(KRN_HSZ_SHIFT+1)] * flt_weight[3] +  
                          i_data_que[1][DATA_WD*(KRN_HSZ_SHIFT+2)-1:0+DATA_WD*(KRN_HSZ_SHIFT+1)] * flt_weight[4] + 
                          i_data_que[2][DATA_WD*(KRN_HSZ_SHIFT+2)-1:0+DATA_WD*(KRN_HSZ_SHIFT+1)] * flt_weight[5]) + 
                          data_conv[0]; //seperate 

assign data_conv_nxt[2] = (i_data_que[0][DATA_WD*(KRN_HSZ_SHIFT+2)-1:0+DATA_WD*(KRN_HSZ_SHIFT+1)] * flt_weight[2*KRN_VSZ + 0] +  
                          i_data_que[1][DATA_WD*(KRN_HSZ_SHIFT+2)-1:0+DATA_WD*(KRN_HSZ_SHIFT+1)] * flt_weight[2*KRN_VSZ + 1] + 
                          i_data_que[2][DATA_WD*(KRN_HSZ_SHIFT+2)-1:0+DATA_WD*(KRN_HSZ_SHIFT+1)] * flt_weight[2*KRN_VSZ + 2]) + 
                          data_conv[1];

assign data_conv_nxt[3] = (i_data_que[0][DATA_WD*(KRN_HSZ_SHIFT+2)-1:0+DATA_WD*(KRN_HSZ_SHIFT+1)] * flt_weight[3*KRN_VSZ + 0] +  
                          i_data_que[1][DATA_WD*(KRN_HSZ_SHIFT+2)-1:0+DATA_WD*(KRN_HSZ_SHIFT+1)] * flt_weight[3*KRN_VSZ + 1] + 
                          i_data_que[2][DATA_WD*(KRN_HSZ_SHIFT+2)-1:0+DATA_WD*(KRN_HSZ_SHIFT+1)] * flt_weight[3*KRN_VSZ + 2]) + 
                          data_conv[2];

assign data_conv_nxt[4] = (i_data_que[0][DATA_WD*(KRN_HSZ_SHIFT+2)-1:0+DATA_WD*(KRN_HSZ_SHIFT+1)] * flt_weight[4*KRN_VSZ + 0] +  
                          i_data_que[1][DATA_WD*(KRN_HSZ_SHIFT+2)-1:0+DATA_WD*(KRN_HSZ_SHIFT+1)] * flt_weight[4*KRN_VSZ + 1] + 
                          i_data_que[2][DATA_WD*(KRN_HSZ_SHIFT+2)-1:0+DATA_WD*(KRN_HSZ_SHIFT+1)] * flt_weight[4*KRN_VSZ + 2]) + 
                          data_conv[3];
```
###### 3
```verilog
generate 
  for(conv_i=0;conv_i<KRN_HSZ;conv_i=conv_i+1) begin : data_convolution  //convolution need to wait 3T (pipe0 + pipe1)
assign data_conv_nxt[conv_i] = {12'h0,i_data_que[0][DATA_WD*(KRN_HSZ_SHIFT+2)-1:0+DATA_WD*(KRN_HSZ_SHIFT+1)]} * {12'h0,flt_weight[conv_i*KRN_VSZ + 0]} +  
                               {12'h0,i_data_que[1][DATA_WD*(KRN_HSZ_SHIFT+2)-1:0+DATA_WD*(KRN_HSZ_SHIFT+1)]} * {12'h0,flt_weight[conv_i*KRN_VSZ + 1]} + 
                               {12'h0,i_data_que[2][DATA_WD*(KRN_HSZ_SHIFT+2)-1:0+DATA_WD*(KRN_HSZ_SHIFT+1)]} * {12'h0,flt_weight[conv_i*KRN_VSZ + 2]} ;
  end 
endgenerate

assign data_conv_add_nxt[0] = data_conv_nxt[0];
assign data_conv_add_nxt[1] = data_conv_add[0] + data_conv_nxt[1];
assign data_conv_add_nxt[2] = data_conv_add[1] + data_conv_nxt[2];
assign data_conv_add_nxt[3] = data_conv_add[2] + data_conv_nxt[3];
assign data_conv_add_nxt[4] = data_conv_add[3] + data_conv_nxt[4];
```

##### successful coding
###### 1
```verilog
generate 
  for(conv_i=0;conv_i<KRN_HSZ;conv_i=conv_i+1) begin : data_convolution  //convolution need to wait 3T (pipe0 + pipe1)
assign data_conv_nxt[conv_i] = {12'h0,i_data_que[0][DATA_WD*(KRN_HSZ_SHIFT+2)-1:0+DATA_WD*(KRN_HSZ_SHIFT+1)]} * {12'h0,flt_weight[conv_i*KRN_VSZ + 0]} +  
                               {12'h0,i_data_que[1][DATA_WD*(KRN_HSZ_SHIFT+2)-1:0+DATA_WD*(KRN_HSZ_SHIFT+1)]} * {12'h0,flt_weight[conv_i*KRN_VSZ + 1]} + 
                               {12'h0,i_data_que[2][DATA_WD*(KRN_HSZ_SHIFT+2)-1:0+DATA_WD*(KRN_HSZ_SHIFT+1)]} * {12'h0,flt_weight[conv_i*KRN_VSZ + 2]} ;
  end 
endgenerate

assign data_conv_add_nxt[0] = data_conv[0];
assign data_conv_add_nxt[1] = data_conv_add[0] + data_conv[1];
assign data_conv_add_nxt[2] = data_conv_add[1] + data_conv[2];
assign data_conv_add_nxt[3] = data_conv_add[2] + data_conv[3];
assign data_conv_add_nxt[4] = data_conv_add[3] + data_conv[4];
```
###### 2
```verilog
generate 
  for(conv_i=0;conv_i<KRN_HSZ;conv_i=conv_i+1) begin : data_convolution  //convolution need to wait 3T (pipe0 + pipe1)
assign data_conv_nxt[conv_i] = {12'h0,i_data_que[0][DATA_WD*(KRN_HSZ_SHIFT+2)-1:0+DATA_WD*(KRN_HSZ_SHIFT+1)]} * {12'h0,flt_weight[conv_i*KRN_VSZ + 0]} +  
                               {12'h0,i_data_que[1][DATA_WD*(KRN_HSZ_SHIFT+2)-1:0+DATA_WD*(KRN_HSZ_SHIFT+1)]} * {12'h0,flt_weight[conv_i*KRN_VSZ + 1]} + 
                               {12'h0,i_data_que[2][DATA_WD*(KRN_HSZ_SHIFT+2)-1:0+DATA_WD*(KRN_HSZ_SHIFT+1)]} * {12'h0,flt_weight[conv_i*KRN_VSZ + 2]} ;
  end 
endgenerate

assign data_conv_add_0_nxt = data_conv[0];
assign data_conv_add_1_nxt = data_conv_add_0 + data_conv[1];
assign data_conv_add_2_nxt = data_conv_add_1 + data_conv[2];
assign data_conv_add_3_nxt = data_conv_add_2 + data_conv[3];
assign data_conv_add_4_nxt = data_conv_add_3 + data_conv[4];
```

#### 4. 下次要如何做可以更好/有可以更好的地方嗎？
- 沒有

### 今天生活中發生的事或是感想
```note-brown
紀錄生活以及身邊發生的小事
```
- 開始將高效學習法做輸出，感覺這次輸出的還是蠻快的

### 發覺優點及缺點
```note-brown
紀錄生活中所見之人的優點及缺點
```
優點 : 
- 沒有

缺點 : 
- 沒有

### 改變(加入到notion人生原則中)
```note-brown
我可以做什麼改變讓自己變得更好?或是看到其他人有甚麼好或不好的行為可以學習的?
```
- [x] 早上因為太晚出門所以很急，進而導致我的情緒感覺很煩躁，下樓時故意把肉紙屑屑弄到地板上都是，這是很糟糕的行為和心態，下次時間要在抓的充裕一點，不然行為和心態都會受到影響 ✅ 2022-09-18
- [x] 衣服、襪子都不要用拉的，會壞掉 ✅ 2022-09-18

### 領悟(加入到notion人生原則中)
```note-brown
我從生活中得到的領悟?
```
- [x] 沒有 ✅ 2022-09-12

### 新學習
```note-brown
今天有沒有從生活中學到甚麼新的事物、技能?
```
- 沒有

### Ideas
```note-brown
把腦中靈感、想法都放在這個區域
```
- 我不知道為什麼我感覺我一直把[@humphrey](@humphrey.md)當作是我的敵人，他人明明對我那麼好，教導我許多知識，但我卻是對他有著這種心理，我應該要非常感謝他的
- 出門前要把耳機充電器給拔掉，不然很危險，我怕會燒起來

### 夢想
```note-brown
我為我的個人目標做了什麼?
```
- 沒有

### 每日檢查清單
- [x] 清除每日蒐集 ✅ 2022-09-12
- [x] 檢視待處理的事項 ✅ 2022-09-12
 
### 回顧紀錄

以上為空則不用建立任何項目


###  
```
 
```

###  
#### 
```

```
#### 
```

```

#### 

```
2022-09-12
```

