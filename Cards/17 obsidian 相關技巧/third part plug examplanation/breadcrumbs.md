# 在 Obsidian 中連結筆記的困難

我曾問過許多使用 Obsidian 筆記的朋友，他們的回答多是：「靠回憶吧…或是反向連結 (backlinks) 剛好有連結到，可以從面板中找到。」

然而這不是一個可靠的做法，人腦在記憶上不如電腦，不可能精準回想自己到底寫過哪些筆記。

舉例來說，當我在寫一則叫做「Kanban Methodology (看板方法)」的筆記時，最多只能想到跟「Agile (敏捷)」、「Scrum (敏捷合作框架)」…其他的筆記就算有寫過，但一時之間也很難想到！

![](https://miro.medium.com/max/1400/0*0Zm7tnueeHIcrfF3.png)

圖片來源：[Kanban Methodology — Kanban Method — Aktiasolutions](https://aktiasolutions.com/kanban-methodology-kanban-method/)

我們可以不斷在 Obsidian 中連結筆記，但如果想不到筆記名稱…根本沒有機會使用。

因此我們需要讓 Obsidian “提醒” 自己：「這則筆記可能和某些筆記有關聯唷！」再由我們自己判斷是否要將筆記做連結。

真的有可能嗎？ Obsidian 還會自動推薦可能有關連的筆記給我知道？

是的，只要我們使用 Breadcrumbs 這款插件就可以做到。

這篇文章先介紹 [Breadcrumbs](https://github.com/SkepticMystic/breadcrumbs) 的運作原理，下一篇文章再介紹個人應用方式。

# 三、Breadcrumbs 的運作原理

Breadcrumbs 的運作原理相當簡單，搭配下方圖解很容易理解。

我們想像一張族譜圖，中心點是「我」，上方有「父母」，同層有「兄弟」、「姐妹」，下方則是「小孩」。

![](https://miro.medium.com/max/1400/0*3K8aqC2YGqyyzpG1.png)

現在把人轉換成，中心點稱為「me note」，上層有一則「parent note」，同層有「sister note」與「brother note」，下方則有「child note」。

![](https://miro.medium.com/max/1400/0*6c8e9EQB-EWR85v_.png)

Breadcrumbs 會在我們點擊「me note」時，自動將「parent note」、「sister note」、「brother note」和「child note」推薦給我們，我們只要決定是否真的要將這些筆記寫在「me note」。

![](https://miro.medium.com/max/1400/0*GvXM-VedXJ_7LPKd.png)

厲害的是，Breadcrumbs 會自動依據筆記之間的連結結果，將推薦筆記分為「Real」跟「Implied」兩個欄位。「Real」的意思是在 me note 中有實際連結的筆記，「Implied」則是 Breadcrumbs 根據程式推算自動推薦給我們的連結筆記。

以上方的例子來說，在 Sibling 欄位顯示「Real」筆記為 sister note、「Implied」筆記為 brother note。這是因為「me note」中真的有 sister note 的連結筆記，但沒有 brother note 。

當我切換到 brother note 時，則可以看到 sibling 欄位顯示「Implied」筆記為 sister note 和 me note，這是因為這兩則筆記都沒有真實被 brother note 連結。

![](https://miro.medium.com/max/1400/0*ceZI4gArV7REgsHw.png)

這樣在寫筆記時，就可以參考 Breadcrumbs 推薦的筆記，方便的做筆記連結啦！

# 四、使用 Breadcrumbs 的前置作業

接下來我們來看如何在 Obsidian 中實作 Breadcrumbs 的功能。

## 1. 加入 Breadcrumbs 辨識欄位

核心步驟是：

> **_在 Metadata 區域加入 parent, sibling, child 辨識欄位。(欄位名字可自訂，等下會說明)_**

依據 [breadcrumbs Wiki · GitHub](https://github.com/SkepticMystic/breadcrumbs/wiki) 的說明，有 2 種加入欄位的方式。

**方法 1 — 在 YAML 區加入欄位**

YAML 區指的是用上下 `---` 包住一段文字，這段文字就稱為 YAML。而在 YAML 區中，我們會用 <欄位名稱> : <值> 來格式來定義欄位的值。

例如下方的 YAML 區域包含了 date 和 aliases (筆記別名)。

![](https://miro.medium.com/max/1400/0*FRbw8cYd6vLoZRdE.png)

我們可在 YAML 區加入 parent,sibling,child 的欄位，並在後方打上要連結的筆記。例如我在「me note」中分別加入下方欄位：

![](https://miro.medium.com/max/1206/0*FwSSkIls7OTIlM1i.png)

若有 1 則以上關聯的筆記，則可以用 `,` 區隔開來。例如下方我多加入了「brother note」：

![](https://miro.medium.com/max/1400/0*o4LPubabANsIOvt8.png)

**方法 2 — 使用 inline field**

Inline field 是 [Dataview](https://medium.com/pm%E7%9A%84%E7%94%9F%E7%94%A2%E5%8A%9B%E5%B7%A5%E5%85%B7%E7%AE%B1/obsidian-%E4%BD%BF%E7%94%A8%E6%95%99%E5%AD%B8-%E6%8F%92%E4%BB%B6%E7%AF%87-02-%E5%A6%82%E4%BD%95%E5%9C%A8-obsidian-%E4%B8%AD%E8%87%AA%E5%8B%95-%E5%BD%99%E6%95%B4%E7%AD%86%E8%A8%98-8d90b5e44f6a) 作者提出的 Obsidian 資料格式，格式為 `<欄位 :: 值>`，必須要寫在 YAML 區之外 (也就是 `---` 的外面)。

例如下方是將「me note」的 YAML 區欄位值改成 inline field：

![](https://miro.medium.com/max/1208/0*gOLdLS2oXfi34n0r.png)

這邊要特別注意的是，若想要使用 inline field 格式，必須先下載並開啟Dataview 插件。

我偏好使用 inline field 來建立 Breadcrumbs 所需要的欄位，理由有 3 個：

**1.比較沒有 Bug**

目前使用方法 1 — 在 YAML 加入欄位，有時候會出現 Breadcrumbs 無法正確顯示「Implied」欄位的筆記，但 inline field 沒有此問題。

**2.格式較正確**

在 YAML 區中合法欄位值是不能包含 `[[]]` 的 (雖然你硬要寫 obsidian 也不會報錯，但在程式世界中這樣定義 YAML 欄位是不正確的觀念)。

**3.可以跟 Dataview 共用欄位**

由於 `<欄位 :: 值>` 的格式本來就是 Dataview 支援的語法，使用 Dataview 時可共用欄位。

## 2. 更改辨識欄位的方法

如果你不喜歡 parent, sibling, child 當作辨識欄位，可以在 Breadcrumbs 的插件中修改。

![](https://miro.medium.com/max/1400/1*XSDdzu1uMFFSU2oEf7ssRg@2x.png)

若要特殊需求要同時指定多個欄位當作 parent, sibling 或 child，可用 `,` 隔開。(我會在下一篇介紹我使用多個欄位的筆記方法)

![](https://miro.medium.com/max/1400/1*shVqjnsBiGSIuR0UEEEM3g@2x.png)

接下來只要在每篇筆記中，都加入 parent, sibling, child 的欄位，並將你想得到的筆記連結放在該欄位後面，Breadcrumbs 就會自動判斷可能的相關筆記。

![](https://miro.medium.com/max/1400/0*gxEO5ssTlEQpLEXk.png)

# 五、Breadcumbs 的其他功能

打開 Breadcrumbs 插件選單，可以看到除了自動推薦功能之外 (Matrix/List View)，還有 Trail/Grid 和 Visualization Model 和 Create index 等功能。

我要特別介紹 Trail/Grid，其功能是顯示到最上層筆記到目前這則筆記的路徑。

以「parent note」→ 「me note」→「child note」為例，Breadcrumbs 顯示畫面如下：

![](https://miro.medium.com/max/1400/0*OMkT_EAynfRDYBLX.png)

1、2 則筆記感覺沒什麼，但當筆記數量增多時，此功能可以快速展示目前這則筆記的上層有哪些筆記，提供寫筆記時的脈絡。(All 是切換按鈕，可切換成顯示所有路徑)

![](https://miro.medium.com/max/1400/0*EIoChtLpn2YtbNiE.png)