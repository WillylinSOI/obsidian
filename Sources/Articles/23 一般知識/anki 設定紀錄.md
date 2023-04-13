![500](Anki%20Algorithm%20v1.3.jpg)
# 卡片階段
共分為三階段
- learning step : 一開始新增卡片的學習階段
- review step : 在第一階段透過good 和easy後才能達到的階段
- relearning step : 在review階段透過again會來到的階段，在此階段中透過good 或是easy 就可以回到review階段

# anki setting 參數說明 
- daily limits
	- new card/day : 每天新卡片上限
	- maximum review : 每天review卡片上限
- new cards 
	- learning step : 25m 1d (代表good loop 的次數為2，2次後將會變為review card)
		- again : 25min，選again的時間
		- hard : (25min + 1d) /2 = 12hour，選hard的時間
		- good : 1d，選good的時間
	- graduating ivl : 3d ，再次選到good的時間
	- easy ivl : 4d ，選easy的時間
- lapses
	- relearning step :  30m 1d
		- again : 30min，選again的時間
		- hard : (30min + 1d) /2 = 12hour，選hard的時間
		- good : 1d，選good的時間
	- minimum interval : 卡片畢業後下次再看到卡片的最小間隔
	- leech threshoold : 卡片重複幾次後將會暫停
- advanced 
	- maximum interval : 下次看到卡片的最大間隔時間
	- starting ease : 在good後再次按下good時會承上的時間倍數，見[anki 設定紀錄](anki%20設定紀錄.md#會更改的easy%20percent)
	- easy bonus : 用在review card 階段，用於easy按鈕
	- interval modifier : 為所有卡片的參數起始倍數，此參數會影響到所有參數
	- hard interval : 用於relearning step 中的hard 
	- new interval : 用於relearning step 中的easy

# 卡片間隔
## 起始於review階段(learning card)
![](Pasted%20image%2020221125143544.png)
每張卡片在作答結束後都會顯示出選項，根據這些選項這張卡片會在以下間隔時間後再次出現，而這些時間都是可以設定的

![](Pasted%20image%2020221125145020.png)

當同一張卡片被連續按了兩次good的之後，下次卡片出現的時間將會被再次延長(圖片中為1天)，途中設定的參數如下，以下為選中後下次出現的時間:
- learning step : 25m 1d
	- again : 25min，選again的時間
	- hard : (25min + 1d) /2 = 12hour，選hard的時間
	- good : 1d，選good的時間
- graduating ivl : 3d ，再次選到good的時間
- easy ivl : 4d ，選easy的時間

## 起始於一個good之後接階段
承上圖，這次開始計算時間的中心點為按了一次good之後，如果在此階段選擇其他選項，那下次時間就會跟第一次選擇good的時間是一樣的

![](Pasted%20image%2020221125145145.png)

## 起始於第二次good之後(review card)
當連續按了兩次good後就會來到這階段

![](Pasted%20image%2020221125145708.png)
其中的參數有:
- hard percent : hard時間拉長比率，用於選擇hard時使用
- easy percent :  easy時間拉長比率，用於選擇good時使用
- easy bonus : easy額外時間拉長比率，用於選擇easy時使用

在這階段中如果按了:
- again : 會回到review階段中的again狀態
- hard : (hard percent) X (graduating ivl)
- good : (easy percent) X (graduating ivl)
- easy :  (easy percent) X (easy bonus) X(graduating ivl) 

### 會更改的easy percent
easy percent 會隨著你做的選擇做上升或是下降的調整

![](Pasted%20image%2020221125150754.png)

## relearnign step 
learning step 結束迴圈後將會進入relearning step 
![](Pasted%20image%2020221125155615.png)

# reference 
- [Deck options in a Mental Map - Scheduling - Anki Forums](https://forums.ankiweb.net/t/deck-options-in-a-mental-map/15757)
- [The BEST Anki Settings and Algorithm Explained (by an expert!) - YouTube](https://www.youtube.com/watch?v=Eo1HbXEiJxo)
- [Butler-Addon - AnkiWeb](https://ankiweb.net/shared/info/1439937507)