---
title: "日麻新手入门简易指南"
date: 2021-03-18T22:47:20+08:00
tags: ["Mahjong"]
series: ["Mahjong"]
related: true
mermaid: true
---

## 牌种一览

**{{< ruby "万子" "man zi" >}}**

{{< mahjong 123456789m >}}

**{{< ruby "索子" "suo zi" >}} / 条子**

{{< mahjong 123456789s >}}

**{{< ruby "饼子" "ping zi" >}} / 筒子**

{{< mahjong 123456789p >}}

**风牌**

{{< mahjong eswn >}}

**三元牌**

{{< mahjong bfc >}}

---

<div class="mermaid">
flowchart LR
  suit("日麻花色") ==>|"包括"| num("数字牌")
  suit ==>|"包括"| char("字牌")
  num ==>|"包括"| man_zi("万子 🀇🀈🀉🀊🀋🀌🀍🀎🀏")
  num ==>|"包括"| suo_zi("索子 / 条子 🀐🀑🀒🀓🀔🀕🀖🀗🀘")
  num ==>|"包括"| ping_zi("饼子 / 筒子 🀙🀚🀛🀜🀝🀞🀟🀠🀡")
  char ==>|"包括"| wind("风牌 🀀🀁🀂🀃")
  char ==>|"包括"| tri("三元牌 🀆🀅🀄")
</div>

## 怎么和牌

### 手牌

手牌由 13 张牌构成，比如：

{{< mahjong 3477m19p12456sbb >}}

### 顺子（同花顺的顺）

3 张 **同花色** 组成 **顺序数字** 的牌：

{{< mahjong 123m >}}

### 刻子（一个模子里刻出来的刻）

3 张（或 4 张） **相同** 的牌：

{{< mahjong 444p >}}

或杠（大明杠 / 暗杠 / 加杠）出来的

{{< mahjong 1111s >}}

> `顺子` 和 `刻子` 统称为 `面子`。

### 雀头

除开 4 组面子之外，剩余 2 张 **相同** 的牌。

### 和牌

<div class="mermaid">
flowchart LR
  mianzi("面子") ==>|"包括"| shunzi("顺子 🀜🀝🀞")
  mianzi ==>|"包括"| kezi("刻子 🀝🀝🀝")
  kezi ==>|"特殊情况（× 4）"| gangzi("杠子 🀝🀝🀝🀝")
</div>

通常，当手中的 13 张牌加上 **{{< ruby "自摸" "自己摸出" >}}** 或 **{{< ruby "放铳" "别人打出" >}}** 的 1 张牌可以组成——\
「4 组 **面子** + 1 对 **雀头**」时，即为 **和牌**。

只缺 1 张就完成 **和牌** 的状态叫做 **听牌**。\
一般情况：**听牌** 状态的手牌（13）再拿到自己听的那张（1）就完成 **和牌**（14）。

- 14 张 = {{< ruby "面子" "3" >}} + {{< ruby "面子" "3" >}} + {{< ruby "面子" "3" >}} + {{< ruby "面子" "3" >}} + {{< ruby "雀头" "2" >}}
- **杠** 可以额外多获得 1 张。\
   所以最多可以达到 18 张 = {{< ruby "杠子" "4" >}} + {{< ruby "杠子" "4" >}} + {{< ruby "杠子" "4" >}} + {{< ruby "杠子" "4" >}} + {{< ruby "雀头" "2" >}}（<a href="/game/mahjong-all/#%E5%9B%9B%E6%9D%A0%E5%AD%90" target="_blank">**四杠子**</a>）
- 也有特别特殊的牌型：14 = 2 + 2 + 2 + 2 + 2 + 2 + 2（<a href="/game/mahjong-all/#%E4%B8%83%E5%AF%B9%E5%AD%90%E9%97%A8%E5%89%8D%E6%B8%85%E9%99%90%E5%AE%9A" target="_blank">**七对子**</a>，川麻叫 **龙七对** / **暗七对**）

## 什么是役

<h4>立直麻将和牌</h4>
在立直麻将中，无役是不能和牌的，可以用来和牌的役种就是「役」。

> 在雀魂中，一共有 42 种役（或者说 _番型_）被采用。

当然，也不是说新手必须背下所有役种才能玩，不需要记住这么多。\
刚入门只需要知道 4 种简单好用的常见牌型就可以愉快玩耍了：**断幺九**、**平和**、**立直**、**役牌**。

## 断幺九

### 幺九牌

所有 **老头牌**（1 和 9 的 _数字牌_）和 _字牌_（**风牌**，**三元牌**）统称为 **幺九牌**：

{{< mahjong 19m19s19peswnbfc >}}

> 如果整副手牌都由不同的 **幺九牌** 组成（包含了全部 13 种幺九牌），就是大名鼎鼎的\
> **国士无双十三面** 了，此时可以和其中 **任何 1 张** 幺九牌。

### 断幺九

当手中的所有 _面子_ 和 _雀头_ 中都不含 **幺九牌** 的时候，就可以和牌：

{{< mahjong 234567m333p5688s 47s >}}

神役，虽然只有一番，但无比好和。

新人之友，天克做大牌。俗称「功夫再高，也怕断幺」，就是它了。

## 平和

除了 **断幺九** 之外还有一种稳定的牌型也适合新人去追求——**平和**。

{{< mahjong 123m1145678s789p 369s >}}

1. 手牌保持 **门前清** 状态（没有吃、碰、明杠过），即自己{{< ruby "面前" "门前" >}}{{< ruby "没有" "清" >}}抓来的别人打出的牌。
2. 所有面子都是顺子（456 形式）、没有刻子（444 形式）。
3. 不是单吊雀头（3 + 3 + 3 + 3 + {{< color-text "1" "red" bold >}}）而是两面听（3 + 3 + 3 + {{< color-text "2" "red" bold >}} + 2）。\
   注意必须是**两面听**（比如 2、3 听 1 / 4），听「{{< ruby "嵌张" "1、3 听 2" >}}」或「{{< ruby "边张" "1、2 听 3" >}}」都不行。

## 立直

### 鸣牌

<h4>吃（顺子）</h4>

**上家** （左手边）打出的牌如果可以和你手中的 2 张牌组成 **顺子**，就可以 **吃** 过来。\
并将该组 **顺子** 摊开放在面前（即公开并无法再改动）。

<h4>碰（刻子）</h4>

**别家** （任何对手）打出的牌如果可以和你手中的 2 张牌组成 **刻子**，就可以 **碰** 过来。\
并将该组 **刻子** 摊开放在面前（即公开并无法再改动）。

<h4>杠</h4>

**杠子**：4 张相同的牌（之前提过杠子也算作 1 个 **刻子**）。

- **大明杠**：自己手里本来有 3 张相同的牌（即 **刻子**），别家打出来一张，组成的杠子
- **加杠**：碰了别家的牌之后，自己再摸到第 4 张组成杠子
- **暗杠**：自己手中有 4 张相同的牌，（随时可以宣告然后）组成一个杠子

### 立直

没有吃、碰、大明杠的情况下（即门前清）进入 **听牌** 状态，此时可以宣告 **立直**。  
宣告 **立直** 之后摸到不能和的牌**必须**打出去，直到自摸或者荣和（别人放铳）。

## 役牌

役牌指的是三类特定的牌（场风牌、自风牌、三元牌）组成的 **刻子**。\
（注意一定得是 **{{< ruby "刻子" "3 张" >}}**，**{{< ruby "雀头" "2 张" >}}** 是不算数的。）\
当持有这三类牌的**刻子**（碰出来的也可以）就可以听牌，此时和的（役种）就是「役牌」。

### 场风牌

东风场的东、南风场的南、西风场的西、北风场的北就是场风牌。

### 自风牌

东家的东、南家的南、西家的西、北家的北就是自风牌。

> 如果是「东风场」的「东家」持有「东」的刻子，此时和的役种就是场风 + 自风。

### 三元牌

白、发、中三种牌就是三元牌。

## 振听

### 什么是振听

**振听** 就是你听的牌中，包含了你「曾经打出过」或者「别人放铳了但你没有和」的牌的状态。  
在 **振听** 状态下**只能自摸**，不能铳和不能铳和不能铳和（因为很重要所以说三遍）。

> 铳和就是 **荣和**。和别人打出的牌，你叫 **荣和**，他叫 **放铳**（俗称点炮）。

### 舍张振听

> 摸进来的牌留下，打别的牌出去。留下来的叫「进张」，打出去的叫「舍张」。

听牌中含有自己打过的牌（舍张）。比如这副：

{{< mahjong 34567m77789s456p 258m >}}

假如这副牌曾经打出过「二万 🀈」，那么「二五八万 🀈🀋🀎」三张牌都将形成 **舍张振听**。

注意：**没有**「~~舍张振听只振听其中 {{< ruby "1 张" "二万" >}}，不振听{{< ruby "其他 2 张" "五万、八万" >}}~~」的说法。

### 同巡振听

> 日麻中东、南、西、北四家，分别摸切（摸牌后打牌）一轮，称为「1 巡」。

没有振听的情况下听牌了，别家打出铳牌（你听的牌）你选择**不和** ，那么将会形成 **同巡振听**。\
同巡振听会在你**下一次摸切**（打出牌）之后**解除**。

这个规则主要是为了公平起见。比如同 1 巡中，你是北家：

1. 东家打红中。你**能和**，但你不和。
2. 南家一看「红中安全」「我也跟着打红中」。结果你和了。
3. 你让南家怎么想？几个意思？是不是想打架？
4. 所以这种情况索性规则上就不允许再和，大家凭本事打牌，以和为贵，不能搞刻意针对。

### 立直振听

没有振听的情况下立直了，别家打出铳牌（你听的牌）你选择**不和** ，那么将会形成 **立直振听**。  
立直振听**无法被解除**（因为不能换听牌了）。换言之，立直振听你就只能指望**自摸**了。\
这种情况在游戏里一般是手贱点错导致的，线下则是看错了。\
所以立直后反正又不用动脑了，要认真盯好啊。