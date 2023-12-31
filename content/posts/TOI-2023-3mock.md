---
title: "TOI 2023 三模（+ 二階心得亂寫）"
date: 2023-04-23T14:30:00+08:00
draft: false
tags: ["TOI", "OI"]
summary: "笨方塊在三模被 Output Only 揍爛，燒雞"
---

之後四模的部分可能會先打我有印象的，然後要是之後有辦法補詳細再更新 ><  

## 三模
### A 最便宜的茶葉蛋 (Eggs)
[Batch, 4s/2 GB]  

有 $n$ 間商店排成一排，第 $i$ 座商店的顏色是 $c_i$，總共有 $m$ 種顏色，而第 $j$ 種顏色的商店賣茶葉蛋的價格是 $p_j$，你需要支援 $q$ 筆詢問，每筆分別是這三種其中一個：

1. 單點修改顏色
2. 單點修改某個顏色的價格
3. 區間詢問最低價格

 - $1 \leq n, m, q \leq 300\,000$
 - $0 \leq c_i < m$
 - $1 \leq p_j \leq 10^9$

|分數|額外輸入限制|
|:-:|:-|
|$7$|$n, m, q \leq 5000$
|$36$|$n, m \leq 20\,000$
|$40$|$n \leq 100\,000$
|$17$|無額外限制

### B 巴斯達三角形 (Pasta)
[Batch, 1s/2 GB]  

有一張地圖，地圖可以分成 $n$ 行，第 $x$ 行（0-based）有 $x + 1$ 個六邊形，  
依序編號為 $(x, 0), (x, 1), \cdots, (x, x)$，其中 $(x, y)$ 跟下一行的 $(x + 1, y), (x + 1, y + 1)$ 相鄰。

這個地圖有些地方不能通行，對 $0 \leq x < n$，而言，$(x, 0), (x, x)$ 都是可以通行的，  
而對於 $0 \leq x < n, 1 \leq y < i$，這個格子 $(x, y)$ 能通行若且唯若 $(x - 1, y - 1), (x - 1, y)$ 恰有一格可以通行。

詳細可以參考[題本](./#附件)上有 $n = 7$ 的一個例子。

你每一步可以往六邊形的六個方向走，給定 $q$ 筆 $(x, y), (z, w)$，輸出兩點間的最短路。保證兩點皆是可以通行的。

 - $2 \leq n \leq 10^{15}$
 - $1 \leq q \leq 10^5$

|分數|額外輸入限制|
|:-:|:-|
|$9$|$n, q \leq 100$
|$15$|$n \leq 10^5, q \leq 100$
|$33$|$n \leq 10^5$
|$43$|無額外限制

### C 最穩定的薪水 (Salary)
[Batch, 3s/2 GB]

有一棵樹，第 $i$ 個節點可能有兩種狀況：**已開發**或**發展中**，對**已開發**的城市，平均薪資固定為 $x_i$，而對於**發展中**的城市，平均薪資起始為 $x_i = 0$，而這些城市會不斷的（同時或不同時）調漲員工薪水，對這些城市而言，定義 $N(i)$ 是該點的鄰居集合而 $c_i$ 為加碼的常數，那這次薪水的調漲將會是

$$x_i \leftarrow \max\left\\{x_i, c_i + \frac 1 {|N(i)|}\sum_{j\in N(i)}x_j\right\\}$$

也就是鄰居的薪資平均加上加碼常數 $c_i$ 與當下的薪資取最大值。

已知在任意順序下經過無限多次的調整之後所有城市的薪資都會達到一個固定的數值，對所有**發展中**的城市輸出這個最終固定的 $x_i$。輸出的絕對或相對誤差在 $10^{-6}$ 以內都視為正確。

 - $1 \leq n \leq 10^6$
 - $0 \leq$ 初始的 $x_i,c_i \leq 10^6$

|分數|額外輸入限制|
|:-:|:-|
|$17$|$n \leq 50$
|$9$|$\|N(i)\| \leq 2$
|$22$|$c_i = 0$
|$19$|$n \leq 5000$
|$33$|無額外限制

### D 眾口鑠金 (Majority)
**[Output Only]**  

有 $n$ 個布林值 $b_i\,(0 \leq i < n)$，總共有 $d$ 天，除了最後一天以外，你可以舉辦很多場投票；而在最後一天，你只能恰舉辦一場投票，而這場投票將會是最後的總決策。

每一場投票恰由 $k$ 個人參與（$k$ 是奇數），每個代理人會做出贊成（$1$）或反對（$0$）的意見，而投票的結果將會是這些意見較多的那種。對一場發生在第 $i$ 天的投票，每個人有三種代表意見的可能：
1. 代表某個 $b_i$
2. 代表在第 $i$ 天以前發生某場投票的結果
3. 永遠是贊成或反對

注意可以有複數個代表人代表相同來源的意見。

你的目標是對於給定的 $f : [0, 2^n-1] \rightarrow \\{0, 1\\}$，你想要構造一種投票的過程滿足最後一天唯一一場投票的結果為 $f(\sum 2^ib_i)$。

 - $2 \leq n \leq 12$
 - $3 \leq k \leq 11$ 且為奇數
 - $1 \leq d \leq 8$
 - 保證 $f(0) = 0, f(2^n - 1) = 1$
 - 保證輸入存在一種沒有 3. 這種代表人的合法會議過程
 - 總會議數量 $\leq 10000$

對每一組測試資料，若輸出合法，則你的分數是  
$$\frac S {1 + 0.3 \log_2(Q_a + Q_b + 1)}$$

其中 $S$ 是該筆測試資料的得分比重，而 $Q_a$ 是 3. 的代表人總數量，$Q_b$ 是「無論 $b$ 是如何都做出相同意見的代表人」數量。

|測試資料|檔案名稱|分數比重 $S$|說明
|:-:|:-:|:-:|:-|
|1|[input_01.txt](./../TOI-2023-3/input_01.txt)|$10$|$n = 5, k = 5, d = 8$
|2|[input_02.txt](./../TOI-2023-3/input_02.txt)|$10$|$n = 7, k = 11, d = 8$
|3|[input_03.txt](./../TOI-2023-3/input_03.txt)|$10$|$n = 12, k = 9, d = 8$
|4|[input_04.txt](./../TOI-2023-3/input_04.txt)|$10$|$n = 12, k = 7, d = 8$
|5|[input_05.txt](./../TOI-2023-3/input_05.txt)|$10$|$n = 9, k = 3, d = 5$
|6|[input_06.txt](./../TOI-2023-3/input_06.txt)|$10$|$n = 11, k = 3, d = 5$
|7|[input_07.txt](./../TOI-2023-3/input_07.txt)|$10$|$n = 12, k = 3, d = 5$
|8|[input_08.txt](./../TOI-2023-3/input_08.txt)|$10$|$n = 7, k = 5, d = 2$
|9|[input_09.txt](./../TOI-2023-3/input_09.txt)|$10$|$n = 9, k = 7, d = 2$
|10|[input_10.txt](./../TOI-2023-3/input_10.txt)|$10$|$n = 11, k = 9, d = 2$

### 比賽

比賽延了一個小時而且還在 C209（也就是我們上課的地方），超怪但如果維持階梯教室的話施工的噪音跟味道可能對大家都是不小的 debuff 吧，而且在 C209 其實蠻舒服的，只是想題目會有想去白板上畫畫的衝動（  

開場先看到 D 是詭譎 Output Only，讀題的時候花了很多時間在理解題目上，尤其是 D 到底是什麼超怪的題目阿，  
A 顯然是一題資料結構題，然後我以為他要強制在線，因為之前寫 CEOI potion 的時候有遇過這種用 grader 強制你在線，  
B 感覺是奇怪數學題，尤其 $n$ 很大然後子題又切得很垃圾，  
C 感覺也是奇怪數學題，  
D 可以先不要碰它，  

A 先想想怎麼樣都糟透了所以就先去碰 C，  
C 的取 $\max$ 根本就在騙人，因為你要不是一樣的話，每個人都是遞增的所以你也只能遞增，  
假設有穩定態的話，那就可以把穩定態的方程式寫出來解，但樸素的高斯消不僅要 $\mathcal O(n^3)$ 甚至會面臨精度爆掉的問題，  
所以我就開始想簡單的 case，先從範測跑跑看，但因為我把兩個類型的輸入看反了所以想超久為什麼範測答案長這樣，  
推了一下想到固定的已開發節點可以切開，然後未開發的那些人的葉子好像很簡單就能算了，  
所以延續上個想法用拔葉子的話每個人只要想辦法不用自己小孩的 $x_i$ 表示就好了，  
然後我就發現等式根本只剩下 $a x_i + b x_{p_i} = c'_i$，然後就能快樂樹 DP 了。  

推完我覺得超神奇的，寫一寫範測就 WA 了，但因為範測一是對稱的但算出來的答案不一樣就一定是我 DP 爛了，  
結果發現是我打錯負號了，怎麼會這樣...  

改完上傳就很順利的拿到 <green>AC</green> 了 ><  

#### 0:45 C <green>100</green>
</br>

回頭想 A 的方法都大爆炸，我第一個想法是分大顏色跟小顏色但這樣的話複雜度應該是 $\mathcal O(Q\sqrt N \log N)$，  
而且這時候的我還以為要強制再線，所以要用類似操作分塊之類的，想說先看看 B 再決定要不要先去寫看看，  

B 認真看一次就發現他是巴斯卡三角形 $\mod 2$，所以很自然地就往碎形去想了，  
上次寫這個東西好像是 ARC Prefix XORs，那時候我是想到分治的做法（因為我根本不會數學），  
這時候就直接用之前做完的結論，看到它是碎形之後又發現到每個 $2$ 的冪次的時候，中間會出現一個大的不能走的倒三角形把版面切開，  
很自然地想到要是詢問跨兩個不同塊的話，它旁邊的三個邊必須要走，然後就破梗完了，  
下一步就是快速地算一個點到三邊的距離，然後又因為它是倒三角形不會擋路所以就只是從三個方向看過去的深度，  
在題本上推推數學之後就直接開寫了，  

快樂小明寫寫之後範測就過了，多測幾個 case 之後也都對就傳了，然後就快樂吃 WA 了，  

#### 1:29 B 0
</br>

大概是數學式出錯了吧，我仔細想想的時候以為三個方向的距離我推錯了，重推一次發現根本就是同樣的結論，  
確定座標沒問題之後再傳了一次

#### 1:40 B 0
</br>

蛤，怎麼會這樣...  
下個 submission 我就忘記我又找出什麼 bug 或只是我在亂傳，反正應該是一些無關緊要的東西吧，不然我應該會記得 XD  

#### 1:51 B 0
</br>

這時候我想說時間很多，而且這題應該是我該拿下的，所以我就毫不猶豫地寫了對拍器。  
先把暴力的弄過，  

#### 1:56 B 9
</br>

拍拍拍就發現我有一個 case 數學是打錯了，那時候回去看那條我真的不知道我在寫甚麼了w，改完測測應該是對的就傳上去，  

#### 2:07 B 57
</br>

大概是 overflow 了吧，但我怎麼記得我都有開 `long long`，打一筆滿的測資就看到 `fsanitize` 噴錯了，原來是我取 `__lg` 之後的那個位移忘記開 `1LL` 了，改完就順利又拿到一題 <green>AC</green> 了 ><  

#### 2:09 B <green>100</green>
</br>

這時候當然是先把 A 喇好才能沒有後顧之憂的玩 D 阿，所以我重看一次 A 才發現完全沒有強制在線這回事，  
那它帶 grader 要幹嘛，模仿 IOI 嗎 🤔  

後來想到的解是正常的分塊，然後應該是只有一邊有帶 $\log$ 所以我可以把 $\log$ 壓進去根號裡面，  
不過實際上是我實作出包忘記壓某一邊的 $\log$ 了，我猜我可能是最近寫根號都要壓記憶體所以忘記可以直接暴力開吧，  
這樣做完之後傳上去吃了兩個 WA，  

我記得好像是我打錯字了，不過我真的沒有記很清楚（但應該真的是打錯字啦，我有記得其中一個是 $n, m$ 打反），  

#### 2:47 A 0
#### 2:49 A 0
#### 2:52 A 43
</br>

我原本想拿 83 的，但我過了 43 至少正確性是好的，所以我就來瘋狂壓常跟亂調塊大小了，  
這邊有很多 submission（賽中應該沒有被我卡到 judge 吧 🥶），  

所以呢，我來講講細節跟做法吧，下面有看到 A 的 submission 全部都只有 43，原因都大同小異，就是我漏壓某一邊的 $\log$ 所以沒過，看到的話就滑掉就好了，或是也可以看看然後笑一下「喔小方塊怎麼這麼笨不會資料結構」就好，  

對陣列分塊，以及維護一個 `multiset` 以及各個顏色出現次數的陣列，每種顏色在那一塊中只能有一個分身，  
修改顏色的時候，修改那個陣列，然後根據有沒有影響修改 `multiset`，  
修改價格的時候，對每一塊都看有沒有需要改，有的話再改，  
查詢的時候，每一塊可以直接用 `multiset` 的最小值，然後碎塊可以暴力，  

再壓常數的方法是在只需要支援知道第一個人（最大或最小）的話，那其實可以用兩個 `priority_queue` 來模擬 `multiset`，  
做法是讓一個存加入操作，另一個存刪除操作，然後查詢的時候要是兩個 `priority_queue` 的頂端可以抵消，就一直兩個都 pop 直到完全抵消，  
雖然有兩個 `priority_queue` 但因為 heap 超級快但 BBST 通常都很慢，所以速度會快非常多。  

#### 2:54 A 43
#### 2:55 A 43
#### 3:03 A 43
#### 3:04 A 43
#### 3:16 A 43
#### 3:31 A 43
#### 4:02 A 43
#### 4:05 A 43
#### 4:06 A 43
#### 4:08 A 43
</br>

壓不過了，決定來做 D，  
看看測資連最小的都不會構造，所以我就在想要怎麼至少構出合法的解，  

一個觀察是所有測資（我比賽中應該是有寫爛，所以我以為 03 跟 07 沒有這個性質），要是 $f(mask)$ 是 $0$，那所有 $submask \subset mask$ 都滿足 $f(submask) = 0$，  

所以其實可以把最小的 $mask$ 都測出來然後算就好，因為沒打算滿分的話可以用常數 0 跟常數 1，這兩個可以把分別做出 $\frac{k+1}{2}$-AND 跟 -OR，所以就能直接構造了，  

構出來其實有夠爛的，不過有分數總比沒分數好，就傳上去了，  

#### 4:24 D 3.17
#### 4:28 D 3.88
#### 4:35 D 5.88
</br>

3.88 跟 2 分別是 01 跟 02 的分數，因為常數一直用會在分母多貢獻 $0.3$，所以其實 01 多一層可以用，把常數換成某場會議的結果會更好，
這時候我應該是有跑出 04 的解，但因為檔案太大了傳不上去，所以我趕快發了一個 Question，但 TOI 都一直不回，  

所以我就先想說放著然後去壓 A，想笑的可以繼續笑笨方塊為什麼那麼不會壓 $\log$，  

#### 4:44 A 43
#### 4:47 A 43
#### 4:47 A 43
#### 4:47 A 43
#### 4:48 A 43
</br>

傳錯檔案了，怎麼會這樣...   

#### 4:49 D 5.88
</br>

#### 4:52 A 43
#### 4:52 A 43
#### 4:52 A 43
#### 4:52 A 43
#### 4:53 A 43
#### 4:54 A 43
#### 4:55 A 43
</br>

這時候發了 Announcement 說系統會調整參數，然後重開並延 15 分鐘，  
我那時候想說好欸我可以在 D 多拿 1. 多分了 XD   
小插曲是大家都以為結束了，不過還好沒有人像 IOICamp 一樣直接講跟題目有關的內容，  

實際重新啟動之後還是不能傳，所以我先回去壓 A  

#### 5:05 A 43
</br>

這時候可以傳了，我趕緊把 output_04.txt 傳上去，結果

#### 5:07 D 5.88
</br>

Output isn't correct  

然後我就發現我構解的 code 有 bug @@  
怎麼會這樣，我一看我根本就來不及修了，所以最後 8 分鐘我也是沒有進展，就這樣三模就結束了。  


### 賽後

Result:
|A|B|C|D|
|:-:|:-:|:-:|:-:|
|43|<green>100</green>|<green>100</green>|5.88|

我發現我忘記壓 $\log$ 真的很蠢，賽後壓壓就拿到 100 了 qwq，  
或許我需要好好練資料結構題，感覺已經有一段時間沒遇到這類的了，  

還有芒果跟 PixelCat 到底是什麼神，為什麼可以在 D 拿到 >= 10 分啊，  
最近 virtual 某場 IOI 的時候我 Output Only 也是裡面打最爛的，  
我一定要好好學習如何做 Output Only。  

還有為什麼會有人在 C 做了 5 次 DFS，芒果是神。  

## 二階

跟一階一樣這邊大概是一些亂記之類的東西 ><  

### Day 1

中午的時候一起去吃了阿宗麵線，
然後報到的時候拿到課表就發現我專題的教授竟然在 Day 8 會來上課 @@  
怎麼會這樣，我在選訓不想做專題啊  

### Day 2

清大教授的 DP 課，內容好像大部分都會了，只是這個教授很喜歡 reject 太複雜的想法 XD  
這天我在 virtual APIO 2019，然後我真的大燒雞大中風，到底是誰可以比我笨，  
我再也不要 virtual APIO 了。  

### Day 3

蔡孟宗教授的課，今天的內容是一堆詭譎的 DP 跟 greedy，然後我人生中第一次用 MCMF 做出教授以為是很難的題目，好耶，  
只是中間有個題目我到現在還是不會，好難

### Day 4

國手課被調走了，所以我在 virtual IOI 2019 Day 1，  
內容可能之後有機會再補，因為我也沒有很認真記錄所有結果，  

### Day 5

謝旻錚教授來上課，內容是各種詭譎幾何，還有很多 ICPC 問題，  
教授承認 2D 是他出的 idea，不過根據他的說法，全國賽跟 TOI 都是教授出主意，然後會有另外的 problem preparer 去負責改題目跟把測資、解答之類的生出來，然後才會有這些比賽，據說 TOI 裡面也很辛苦所以 TOI 模考品質不太好可能要多體諒他們，但我是覺得抄 IMO 20p3 還有歐拉與 TOT 有點太扯了就是，  
突然發現平面圖的各種東西之類的要是給平面鑲嵌其實 IOI 好像都能考，  

這天晚上我好像在 virtual IOI 2019 Day 2，結果是銀牌，不過我好像也大概把我的精神分都拿到了吧。  

### Day 6

模考前一天 ><  
也是謝旻錚教授來上課，內容是更多詭譎幾何，還有更多 ICPC 問題，  
另外有四題從 2015 長春 Regional 拿出來組的題目，judge 是 vjudge -> HDU，所以我那時候也發現 HDU 竟然復活了，  
（但上面的題目我應該是不會常寫啦）  
我做掉了一題給凸多邊形問所有子凸多邊形的平均面積的題目，我覺得這個真的只有 Codeforces 1700 ~ 1900 而已但大家都說他是 2100 ~ 2300，好怪喔  

### Day 7

三模 ><  

### Day 8

~~被專題教授嗆時間~~，其實教授好像就講了很多關於 chromatic number 的性質，不過我想很多可能目前都用不到吧 XD  
下午是奇怪的輔導課，但至少很好玩  

### Day 9

不知道為什麼又有被專題教授嗆時間，然後下午又是奇怪的輔導課，  

### Day 10

蔡孟宗教授的 matroid 跟 PIE 課，雖然沒有講 matroid intersection 但其實收穫了不少，也是有很多跟 matroid 沒有很大關係的題目，但都很難而且好酷，  

這裡有一個題目是還沒有人想出來的，內容是給一個表格，保證每行每列 sum 都是 0，但有些格子是不能知道的，需要藏起來，  
問你要最少再多藏多少格子，才能保證給定的格子不可能有任何一個被知道答案。  

### Day 11

國手課，內容是 8w 來讓一個人講一題模考題，  
基本上除了 3D 以外都有解了（3D 官方也沒有給 output），  
但很酷的事情是 1D 跟 3A 如果拿官方的解去丟的話，會過不了，  
所以我其實在一模就打贏 TOI 了（X  

下午是各種詭譎遞迴式，但我都不會數學，  

### Day 12

王炳豐教授的課，簡單來講就是各種 $\langle\mathcal O(n), \mathcal O(1)\rangle$ 的東西，好像有更懂他在幹嘛了，  
剛好是模考前一天所以也沒事要做 ><  

有趣的事是我趁邱翊均睡著的時候幫他畫了一個名牌但是他的名字被改成數學家，所以現在邱翊均不只是國手還是數學家了，  

### Day 13

四模，詳細跟選訓總心得應該會之後一起附上，這裡就先不放了（或許只是因為我在偷懶）  


## 附件
題本跟範例互動程式： 

[3A.pdf](./../TOI-2023-3/3A_zh_tw.pdf)
[3A_sample.cpp](./../TOI-2023-3/3A_sample.cpp)
[3A_sample_grader.cpp](./../TOI-2023-3/3A_sample_grader.cpp)  
[3B.pdf](./../TOI-2023-3/3B_zh_tw.pdf)  
[3C.pdf](./../TOI-2023-3/3C_zh_tw.pdf)  
[3D.pdf](./../TOI-2023-3/3D_zh_tw.pdf) 
[testdata.zip](./../TOI-2023-3/testdata.zip)（
[input_01.txt](./../TOI-2023-3/input_01.txt)
[input_02.txt](./../TOI-2023-3/input_02.txt)
[input_03.txt](./../TOI-2023-3/input_03.txt)
[input_04.txt](./../TOI-2023-3/input_04.txt)
[input_05.txt](./../TOI-2023-3/input_05.txt)
[input_06.txt](./../TOI-2023-3/input_06.txt)
[input_07.txt](./../TOI-2023-3/input_07.txt)
[input_08.txt](./../TOI-2023-3/input_08.txt)
[input_09.txt](./../TOI-2023-3/input_09.txt)
[input_10.txt](./../TOI-2023-3/input_10.txt)）