---
title: "[Virtual] SWERC 2021-2022"
description: "團練篇"
date: 2022-12-05T22:00:00+08:00
draft: false
tags: ["ICPC", "SWERC", "virtual"]
summary: "笨方塊耍笨 virtual SWERC 拖累隊友還被爆揍，燒雞"
---

## 前言
基本上就是 NPSC 團練第二場，其實還有第三場 NERC，NPSC 前確實沒機會檢討了吧  
（原本是想說除非我拋棄睡眠讓 NPSC 燒雞，不過實際上也是一樣啦）  

## Virtual
開場一樣高嘉泓從前面開始讀，我從後面開始讀，  
一開始高嘉泓先看到 A 好像是水題而且很多人做，我就直接開寫，  

> **pA**  
> 給你 $n$ 道問題，每題有難度美麗度 $b_i$ 跟難度 $d_i$，   
> 你要找出 10 道問題使得難度在 1 到 10 之間都恰好有一題，  
> 輸出最大美麗度或者不可能找到那 10 題。  
> $1 \leq t \leq 100,\\,1 \leq n \leq 100$  

水題，我能寫錯我就是智障。  

### 5 pA <green>+</green>
</br>

接下來我們看到很多人開 M 就直接讀他，  

> **pM**  
> 你要拿出 $n$ 瓶酒，每瓶可以是紅酒或白酒，  
> 有 $m$ 個評審，第 $i$ 個評審想找到一個連續區間使得其中剛好有 $r_i$ 瓶紅酒以及 $w_i$ 瓶白酒，   
> 構造一組解或者輸出不可能。  
> $1 \leq t \leq 100,\\,1 \leq n,\\,m \leq 100,\\,0 \leq r_i,\\,w_i \leq 100$  

把紅白分兩邊就好的水題。  

### 9 pM <green>+</green>
</br>

接下來高嘉泓看到 H 很多人開，發現開個 gcd 跟因數就好，上去寫  

> **pH**  
> 給一個 $w \times l$ 的網格，  
> 輸出所有 $a$ 滿足 $1 \times a$ 的磁磚可以鋪滿網格的邊框。  
> $1 \leq t \leq 100,\\,3 \leq w,\\,l \leq 10^9$，輸出的總數 $\leq 2 \cdot 10^5$  

高嘉泓寫了一小段時間然後就一發了，教我  

### 18 pH <green>+</green>
</br>

然後我看了 D 發現很多人寫，讀了一下就打算上去寫寫看  
> **pD**  
> 一個字串可以加入或刪除連續的 `AA`、`BB`、`CC`、`ABAB`、`BCBC`，  
> 給兩個只有 `ABC` 的字串 $u,\\,v$ 問可不可以經由操作把 $s$ 改成 $t$。  
> $1 \leq t \leq 100,\\,1 \leq |u|,\\,|v| \leq 200$  

一開始我以為是 DP，感覺 $\mathcal O(t|u||v|)$ 蠻合理的，寫一寫感覺對了就傳上去 

### 29 pD -1
</br>
 
我想說蛤什麼鬼，應該不是我 DP 寫錯吧，  
看了一下還真的寫錯了，改完之後測一測發現應該是好的就再傳了一次  

### 33 pD -2
</br>

感覺是正確性爛掉了，然後我就發現 `BAB` 可以變成 `AABAB` 再變成 `A`，  
我想說應該這個 case 判完就沒了吧，結果越想越不對，有超多東西會爆掉。  
沒記錯的話我應該就先讓高嘉泓上去寫 I 了，  

> **pI**  
> 一條數線上有 $n$ 區的人，第 $i$ 區在 $100(i-1)$ 的位置，有 $p_i$ 個人，  
> 另外有 $m$ 間冰淇淋店，第 $i$ 間在 $x_i$，  
> 你要開設一家冰淇淋店使得有最多的顧客距離你的店嚴格最近，輸出這個值。  
> $2 \leq n \leq 2 \cdot 10^5,\\,1 \leq m \leq 2\cdot 10^5,\\,1 \leq p_i \leq 10^9,\\,0 \leq x_i \leq 10^9,\\,x_i \neq x_j (i \neq j)$。  

高嘉泓他會做所以我就下來想 D，在弄他之前我發現 O 很多人過，所以就趁高嘉泓還在想小細節的時候寫了 O：

> **pO**  
> 有一個圓形的迷宮，裡面有 $n$ 道牆壁，  
> 有可能是直線，會蓋在半徑介於 $[r_1,\\,r_2]$，方向角是 $\theta$ 的地方，  
> 或是弧線，固定半徑是 $r$ 而方向角從 $[\theta_1,\\,\theta_2]$（可能會繞過 $0$）都有牆，  
> 輸出可不可能從無限遠的地方走到 $(0,\\,0)$。  
> $1 \leq t \leq 20,\\,1 \leq n \leq 5000$，沒有牆相交在正實數長度。  

想了之後其實就好好蓋圖做 DFS 就好，所以我就先上去把它寫出來，  

### 69 pO -1
</br>

我去一旁慢慢 debug，然後高嘉泓繼續去修他的 I，  
很快我就發現我似乎沒有處理好開閉區間的問題，再仔細看過一次確定沒問題我就上去改了一點點就再傳了一次，  

### 77 pO <green>+1</green>
</br>

下來之後電腦繼續交給高嘉泓的處理 I，我則是去把剛剛錯兩次的 D 給弄好，  
之後推了幾次發現了這些性質：  
 - `BA` <-> `AABABB` <-> `AB`  
 - `CB` <-> `BBCBCC` <-> `BC`  
  
也就是 `B` 可以自由移動，我只要判 `B` 的奇偶跟 `AC` 就好，變超簡單。  
所以我趁高嘉泓在燒實作的時候迅速寫完，傳上去  
「應該不會這麼梗吧，如果是這樣我真的會超氣」  

### 78 pD <green>+2</green>
</br>

做完我就一起幫高嘉泓看 I 應該要怎麼算合法區間，推了一小段時間我意識到我不太會數學，  
但好事是只剩這個部分，所以最後修修改改好像就好了，所以就傳上去，  

### 118 pI <green>+</green>
</br>

接下來我去開 L，  
> **pL**  
> 你一開始在數線上的 $0$，接下來有 $i$ 個目標，  
> 如果你在 $t_i$ 的時間點抵達 $a_i$ 就會獲得 $1$ 分，  
> 而你每秒能移動的最大速度就是 $v$，  
> 求出最高得分。  
> $1 \leq n \leq 2 \cdot 10^5,\\,1 \leq v \leq 10^6,\\,1 \leq t_i \leq 10^9,\\,-10^9 \leq a_i \leq 10^9$  

看幾眼畫個圖就發現是伸縮之後轉 45 度經典題，所以就轉完然後歸成 LIS 直接用 vector + 二分搜寫掉，  
一開始我還想用浮點數跟推轉 45 度轉很久，不過都算是小事，  
過程中突然發現要從 $0$ 當起點，所以就得反過來寫。  
寫完之後傳上去就吃了一個大大的 WA。  

### 134 pL -1
</br>

我想說我不可能連 LIS 都寫錯吧，結果測了一些小 case 發現是我忘記 $0$ 當起點的時候有人可能會超過，他們不能算，  
所以改完就穩穩地拿到了 AC。  

### 140 pL <green>+1</green>
</br>

下一個多的人開得是 F，  
> pF  
> 有 $n$ 座天線，第 $i$ 座的強度是 $p_i$，  
> 兩個天線 $i,\\,j$ 能花 $1$ 單位的時間傳遞訊息若且唯若 $\min(p_i,\\,p_j) \geq |i-j|$，  
> 輸出天線 $a$ 傳遞到 $b$ 需要多久。  
> $1 \leq t \leq 10^5,\\,1 \leq a,\\,b,\\,p_i \leq n,\\,\sum n \leq 2\cdot 10^5$  

接下來就進行睡覺環節了，我們對這題毫無頭緒，除了一個持久化線段樹優化建圖的怪東西，  

後來我是想到可以不用真的持久化，只要跑一個邊點都是 $\mathcal O(n \log n)$ 的 BFS 就能做完，  
所以我就開始寫了，實際上沒有很難，只是我一直對建邊出了一些小問題，  
修修改改總算過範測了，不過這題的問題是空間只有 256 MB，然後我們砸下去就是硬生生地吃了 MLE，  
我一邊不斷的壓然後高嘉泓一邊想其他解，  
最後他還是想不到，而這 MLE 的過程其實蠻痛苦的，就如實跟大家呈現記憶體爆掉的後果吧。  

### 245 pF -1
### 252 pF -2
### 254 pF -3
### 259 pF -4
### 260 pF -5
### 262 pF -6
### 267 pF -7
### 268 pF -8
### 278 pF -9
### 278 pF -10
</br>

## 檢討

其實 F 可以好好做，而且很快一個 $\log$，  
剩下的題目（包含 F）應該會開一個補題篇慢慢打，所以就敬請期待吧。  

主要的問題是我實作會有小偏差，整體被小地方卡的都是零碎時間，但積起來會很可怕，  
感覺是會多到影響題數的那種，可能要在全國賽前多練幾場讓自己的實作上軌道，  
還有就是應該要想到的得好好想到，  
還是出了不少問題，怎麼會這樣……  

我真的是不會 OI 也不會 ICPC 的笨蛋。  