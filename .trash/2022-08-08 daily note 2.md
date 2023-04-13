# I. 每日金句
<% tp.web.random_picture("1920x1080") %> <br>
<% tp.web.daily_quote() %>

>中文翻譯:
>
---

# II. 回顧
```note-brown
開啟回顧，回想昨天以及去年的今天發生了什麼
```

## 明天
[[<% tp.date.now("YYYY-MM-DD",+1) %> daily note]]

## 一年前的今天
[[<% tp.date.now("YYYY/MM/YYYY-MM-DD", "P-1Y") %> daily note]]

## 昨天
[[<% tp.date.now("YYYY-MM-DD",-1) %> daily note]] 


---
# III. 每日活動
今天是<% tp.date.now("ddd") %>
```ActivityHistory
/

```

---
# IV. 每日感恩日記
## 心靈
```note-brown
今天有哪 3 件值得感恩的事情?
```
- 

## 弱連結
```note-brown
今天是否「日行一善」，幫助了任何人?
```
- 

## 親密關係
```note-brown
今天要如何和另一半/家人表達我愛妳? 或是學習關於兩性之間的知識?
```
- 

## 健康 (如何吃? 如何動? 如何靜?)
```note-brown
我做了哪些事情讓自己休息及放鬆? 做了甚麼運動?
```
- 

## News 新聞
```note-brown
今天發生了什麼重大的事情、看到了甚麼新聞?有甚麼感想?
```
```note-blue
早上8:20開始記錄
```

- 

## 文章
```note-brown
每天至少閱讀1篇文章，並作筆記
```
<%* if (tp.date.now("ddd") == "週一") { %>
- [ ] 生產力、知識型文章
- 
<%* if (tp.date.now("ddd") == "週二") { %>
- [ ] 兩性、感性類文章
- 
<%* if (tp.date.now("ddd") == "週三") { %>
- [ ] 生產力、知識型文章
- 
<%* if (tp.date.now("ddd") == "週四") { %>
- [ ] 兩性、感性類文章
- 
<%* if (tp.date.now("ddd") == "週五") { %>
- [ ] 生產力、知識型文章
- 
<%* if (tp.date.now("ddd") == "週六") { %>
- [ ] 任何文章
- 
<%* if (tp.date.now("ddd") == "週日") { %>
- [ ] 任何文章
- 

## 財務
```note-brown
今天購買了哪些東西 ?
```
- 

## 心智成長
```note-brown
今天在我最關注的領域 (溝通/個人成長/學習)，我有哪些進展 ?我閱讀了哪些書籍內容 ?
```
- 

## 工作
```note-brown
本日 AAR (After Action Review)
```

### 1. 今天完成了什麼事情？ 
- 

### 2. 選一件讓我有感覺、有啟發的事情 
- 

### 3. 我從過程中學習到什麼事情 ? 
- 

### 4. 下次要如何做可以更好/有可以更好的地方嗎？
- 

## 今天生活中發生的事或是感想
```note-brown
紀錄生活以及身邊發生的小事
```
- 

## 改變(加入到notion人生原則中)
```note-brown
我可以做什麼改變讓自己變得更好?或是看到其他人有甚麼好或不好的行為可以學習的?
```
- [ ] 

## 領悟(加入到notion人生原則中)
```note-brown
我從生活中得到的領悟?
```
- [ ] 

## 新學習
```note-brown
今天有沒有從生活中學到甚麼新的事物、技能?
```
- 


## 精華
```note-brown
今天的人生精華是甚麼?
```
```note-blue
早上8:20開始規劃
```
```note-red
要注意是否有精力完成
```
- 

## Ideas
```note-brown
把腦中靈感、想法都放在這個區域
```
- 

## 夢想
```note-brown
我為我的個人目標做了什麼?
```
- 

## 每日檢查清單
-  [ ] 清除每日蒐集
-  [ ] 檢視待處理的事項
 
## 回顧紀錄
<%* if (tp.date.now("ddd") == "週六") { %>
- [ ] 建立周回顧
<%* }if(tp.date.now("DD")== "30") { %>
- [ ] 建立月回顧
<%* }if(tp.date.now("MM-DD")== "2-28") { %>
- [ ] 建立月回顧
- [ ] 建立季回顧
<%* }if(tp.date.now("MM-DD")== "3-31") { %>
- [ ] 建立季回顧
<%* }if(tp.date.now("MM-DD")== "6-30") { %>
- [ ] 建立季回顧
<%* }if(tp.date.now("MM-DD")== "9-30") { %>
- [ ] 建立季回顧
<%* }if(tp.date.now("MM-DD")== "12-31") { %>
- [ ] 建立季回顧
- [ ] 建立年回顧
<%* } else { %>
以上為空則不用建立任何項目
<%* } %>

## 今月須完成OGSM
```tasks
path includes 001Project/個人OGSM
starts before tomorrow
has due date
not done
sort by due
```

## Other Tasks
### 特定日須執行
```tasks
priority is above none
sort by priority
```
### 假日需歸檔項目
```tasks
not done
no due date
path does not include Templates
path does not include 001Project
path does not include display note/待處理的事項.md
```

### Done Today

```tasks
done on <% tp.date.now("YYYY-MM-DD") %>
```

