---
title: "[Virtual] BOI 2020"
date: 2021-07-14T14:04:24+08:00
draft: false
tags: ["virtual", "BOI", "OI"]
summary: "笨方塊耍笨 vir BOI 2020 被爆揍，燒雞"
---

拖稿 QwQ  
以下有雷，還沒 vir 但想 vir 的不要忍不住往下滑，  
我都有好好把防雷空行弄好了，希望沒有爆雷到 QwQ  

## 賽前

被 shaun 推題的時候先發現他是 OI 制的 Online Mirror，  
在還沒被爆雷題目內容前就發現他是 BOI 2020 了，  
想說只有 vir 過 APIO 2021 一場而已，就來試試看。  
</br></br></br></br></br></br></br></br>

## Day 1

### 題目
- pA color  
**\[互動題\]**  
有一個值 $C$，當上次跟這次查詢差距超過 $C$ 會回傳 `1`，否則回傳 `0`，  
你可以查詢 1 到 $N$ 最多各一次，總共不超過 64 次，求出 $C$。  
$N \leq 10^{18}$。

- pB mixture  
有一個完美比例（三個數字的連比），以及其他混和物的比例，  
每次會增加或刪除一個混和物，  
輸出從目前的庫存中，最少可以選擇多少混和物以任意比例湊出這個完美比例。  
操作次數 $N \leq 10^5$。

-  pC joker  
有一張圖，每個點跟邊有編號，  
$Q$ 次查詢把一個區間 $[l,\\,r]$ 的邊拔掉還有沒有奇環。  
$N,\\,M,\\,Q \leq 2 \times 10^5$


### 00:22 
**Score: 9/0/0**  

color 應該是某種二分搜/分治，  
mixture 完全沒有想法，DP 想不到，greedy 也沒有策略，  
joker 應該就是圖論題，  

花了好久把 9 分拿到，查詢的時候不小心打錯符號，被自己蠢死 = =  

### 00:52
**Score: 9/0/14**  

joker 感覺就是判二分圖，    
就砸下去 DFS $\mathcal O(NQ)$ 拿到暴力 14 分，  
C++ 17 不能用全域變數 `visit`，燒雞。  

### 01:14
**Score: 9/0/39**  

突然想到二分圖可以用 DSU 啟發式合併下去，   
然後又發現只要對於給定的 $l$，會有一個右界 $f_l$ 分隔 `YES`, `NO` 兩種答案。  
所以寫了一個 $\mathcal O(N \log N)$ 去做 $l = 1$ 的子題。  

### 01:33
**Score: 9/0/39**  

還是想不到 joker 之後的做法，回去想 color，  
一直找不到好的策略去二分搜，每次都會卡在兩邊答案在 $[L,\\,L+1]$ 沒辦法決定，  
然後就去看一下 mixture，突然發現可以當成向量和，才知道這是計算幾何題，  
把它當成三維的之後發現答案不超過 3，就開始推式子看看可不可以拿到一個子題。  

### 02:27
**Score: 9/0/39**  

推式子燒雞，有些 case 處理不了，  
決定去做掉 color 簡單的子題 2：查中間再暴搜就可以了。  

### 03:37
**Score: 22/0/39**  

color 拿到了，joker 的子題四被卡，沒辦法單純做 200 次，  
有點忘記是不是這個時候想到 $f_l$ 是單調的，  
但是我沒辦法把 DSU 改成 Queue-like，所以就先放掉了，  
繼續去推 mixture 的式子，然後傳上去吃了 WA。  

### Until End
**Score: 22/0/39**  

color 仍舊沒想法，因為每種數字只能查一次的限制卡住了，  
joker 一樣沒有進度，  
至於 mixture 發現到它必須是正的線性組合，而且原本的平面計算是爛的，  
修好之後傳上去還是 WA，就乾燒到結束了。

### 結果  
pA color: <green>9</green> / <green>13</green> / 21 / 24 / 33  
pB mixture: 13 / 17 / 30 / 40  
pC joker: <green>6</green> / <green>8</green> / <green>25</green> / 10 / 22 / 29  
Total: 61  

### 賽後 
mixture 的解只是答案為 3 忘記檢查向量是否彼此平行，不然可以拿到 13 分，   
然後 joker 差一步：只要做分治就可以了，分數虧超多 ;w;

</br></br>

## Day 2

### 題目
- pA graph  
給一張無向圖，有兩種顏色（紅、黑）的邊，
對每個點都填上實數，滿足：  
黑色邊兩側要是 1，紅色邊兩側相加要是 2，  
問點權總和最小的其中一個方案。  
$N \leq 10^5$，$M \leq 2\times 10^5$。

- pB1 village(minimum)
給定一棵樹，每個點的人都要移動到非自己的那個點，  
問**最小**移動距離。  
$N \leq 10^5$

- pB2 village(maximum)
給定一棵樹，每個點的人都要移動到非自己的那個點，  
問**最大**移動距離。  
$N \leq 10^5$

- pC virus
對於一個字串，每次這個字串都可以選擇任意一個不是 `0` 或 `1` 的字元取代成替換表裡的其中一種可能，  
另外給定一群字串（稱為抗體），問對於所有可能取代完的途徑中，沒辦法被其中一個抗體匹配到子字串的最小長度是多少。  
對於字串是 $2$ 到 $G$ 分別回答。  
有點難懂，建議看原本的題目。  

### 01:11
**Score: 100/0/0**

先開了 graph，發現連浮點數都沒辦法處理，  
就想想看我手動解的情形，  
然後就發現了可以直接假設初始點是 $x$，用 DFS Tree 然後回邊當條件，  
吃了幾次 WA，像是沒判連通塊之類的，然後 AC 了。

### 02:12
**Score: 100/56/0**

看了 pB1，就是樹上最大匹配，  
寫了之後傳上去 WA，  
想說先把兩個爆搜拿到 12 分，再來 debug。  
結果是發現是恰兩個子樹的 case 沒判好，改完就 AC 了。

### 02:51
**Score: 100/100/0**

用爆搜跑範測確定了 pB2 幾組解，然後發現一件事：  
每條邊的貢獻等於大小較小那一側的節點 $\times 2$，  
不確定是不是每個都這樣，所以就稍微證了一下，  
假設某條邊左右兩棵子樹大小是 $L,\\,R$，且 $L < R$，  
此時一定有 $L \leq \dfrac N 2$，  
所以考慮左邊那個點的所有子樹，  
如果其中有一個大小 $> \dfrac N 2$，就討論這個子樹上面這條邊，  
否則，一定可以辦法互換使得所有邊都有最大貢獻，  
（根據絕對眾數的證法）  
所以直接用 `prioriry_queue` 對重心所有子樹做事，就 AC 了。

### Until End
只剩 virus，燒雞，  
暴搜丟上去沒過，然後又de不出bug ;w;

### 結果  
pA graph: <green>5</green> / <green>12</green> / <green>17</green> / <green>24</green> / <green>42</green>  
pB village: <green>6</green> / <green>19</green> / <green>25</green> // <green>6</green> / <green>19</green> / <green>25</green>  
pC virus: 11 / 14 / 25 / 32 / 18  
Total: 200

### 賽後 
還沒戳題解跟補題，會連下一場一起補（如果我看得懂題解的話 ;w;）。


## Result

總分: 261  
Rank: 金牌中間  

</br></br></br></br></br>

## 心得

Day 1 燒太慘了，看完官解發現 pB 其實 2D 就解完了，不需要用到 3D，  
Day 2 的 pC virus 看 BOI 的板發現不是簡單題，整體來說還可以，只是暴搜沒拿到有點可惜，  

看起來所需要的知識跟科技我都有，只是想不出來，  
之後要多加強這塊，回顧 TOI 入營考、模考、之前 virtual 的 APIO 2021 跟這場，  
大部分都是沒有想出來，  

另外我覺得我實作的好慢，  
而且中間會出一堆 bug，如果這些都沒有抓出來，分數可能會比預期的差，  
可能要再找一些題目練實作，不然改天燒雞就來不及了。   
