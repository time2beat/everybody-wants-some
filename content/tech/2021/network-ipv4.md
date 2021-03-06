---
title: "计算机网络基础 IPv4"
date: 2021-03-25T12:56:52+08:00
tags: ["Internet", "IP"]
series: ["Network"]
related: true
---

## 格式
IPv4 是由「点分号 `.`」分隔开的 4 个「 8 位组」（占 8 位 `0 或 1 的无符号二进制数` 即 `bit`）。  

形如 `xxxx xxxx.xxxx xxxx.xxxx xxxx.xxxx xxxx`。  

举例 `1100 0000.1010 1000.0000 0000.0000 0001`。  
上面这个二进制表示的 IP 换算成十进制就是 `192.168.0.1`。  

显而易见：  
每个 8 位组最小为 `0000 0000`，换算成十进制为 `0`。  
每个 8 位组最大为 `1111 1111`，换算成十进制为 `255`。  

所以用十进制来表示的 IP，最大数字也就 255，十进制的 IP 取值范围为 0 - 255。  
以上，算是 IPv4 的基本「语法」。  

## 含义
而一个 IP（本文中默认指 IPv4，下同）地址是由两部分组成的：网络地址（Network Address）和主机地址（Host Address）。  

「网络地址」指某个网络空间，「主机地址」指该主机在某个网络空间中的位置。  
类似车牌号，`川 A` 指**成都**，那你 `粤 A` 也是成都吗？显然不是。  
虽然我们都是 A，但我这个 A 是广东（粤）的 A，この**广州**だ！  

在很早以前，第一个 8 位组（前 8 位）是网络地址，后三个 8 位组（后 24 位）是主机地址，是固定的。  
然后人们发现这种分配极度不合理，因为这意味着全网只有 256（0 - 255）个网络空间，而每个网络空间拥有 1600 万余（2^24 = 16,777,216）主机地址。  
这是因为互联网刚出现并不是国际性的，所以没有考虑那么多。然而，很快各个国家各个地区都发现了互联网的好处，于是大家国通网，都需要用到 IP 地址，256 个网络空间就不够分了。  
因此 IP 改革成了现在的样子，分为 A / B / C / D / E 五类。  

### A 类 IP 地址
> 用于设备寻址

以 `0` 开头。  
前一 8 位组（8 位）为网络地址，后三 8 位组（24 位）为主机地址。  
形如 `0nnn nnnn.hhhh hhhh.hhhh hhhh.hhhh hhhh`。  

> 此处用 `n` 表示网络地址（Network Address），`h` 表示主机地址（Host Address），下同。

换算成十进制为 `0.0.0.0` - `127.0.0.0`。  
默认的子网掩码为 `255.0.0.0`，CIDR（下面会讲）表示为 `/8`。

> 子网掩码和 IP 做与运算，得到就是公网 IP。  
> 我们平常说的「没有公网 IP」就是运营商分给你的 IP 与运算（&）子网掩码出去，跟你邻居的 IP 与了子网掩码出去，是同一个 IP。  

### B 类 IP 地址
> 用于设备寻址

以 `10` 开头。  
前二 8 位组（16 位）为网络地址，后二 8 位组（16 位）为主机地址。  
形如 `10nn nnnn.nnnn nnnn.hhhh hhhh.hhhh hhhh`。  
换算成十进制为 `128.0.0.0` - `191.255.0.0`。  
默认的子网掩码为 `255.255.0.0`，CIDR 表示为 `/16`。

### C 类 IP 地址
> 用于设备寻址

以 `110` 开头。  
前三 8 位组（24 位）为网络地址，后一 8 位组（8 位）为主机地址。  
形如 `110n nnnn.nnnn nnnn.nnnn nnnn.hhhh hhhh`。  
换算成十进制为 `192.0.0.0` - `223.255.255.0`。  
默认的子网掩码为 `255.255.255.0`，CIDR 表示为 `/24`。

### D 类 IP 地址
> 用于组播（Multicast）  

以 `1110` 开头。  
前三 8 位组为网络地址，后一 8 位组为主机地址。  
形如 `1110 xxxx.xxxx xxxx.xxxx xxxx.xxxx xxxx`。  
换算成十进制为 `224.0.0.0` - `239.255.255.255`。  

### E 类 IP 地址
> 保留，用于研究和开发用途  

以 `1111` 开头。  
前三 8 位组为网络地址，后一 8 位组为主机地址。  
形如 `1111 xxxx.xxxx xxxx.xxxx xxxx.xxxx xxxx`。  
换算成十进制为 `240.0.0.0` - `255.255.255.255`。  

## 无类别域间路由（CIDR，即 Classless Inter-Domain Routing）
通过设置子网掩码来将大型网络分解为小型网络，即子网划分。  

假如某 IDC 提供商拿到一个 B 类网络空间，假如为 `172.43.0.0/16`（那么这个网络空间内可以容纳 2^16 = 65536 个主机地址），他自己根本没有这么多服务器来吃下这个资源，怎么办？  

他就可以利用 CIDR 将自己用不完的 IP 资源二次分包出去（比如给另一家有资质但没有拿到网络空间的 IDC 提供商）。  

他手一划将原来的子网掩码（`255.255.0.0`）修改为 `255.255.240.0`（写成二进制就是 `1111 1111.1111 1111.1111 0000.0000 0000`），那么他就将原来的大型网络空间分成了 16 个： `172.43.0.0/20`、`172.43.16.0/20`、`127.43.32.0/20`、`172.43.48.0/20`……`127.43.240.0/20`。然后就可以自己用一半，分别人一半了。  

> 稍微提一下，虽然用得到这个知识的人肯定用不着我来提醒了。  
> 同一子网内的设备必须处于同一 IP 网段内，否则无法进行通信。  
> 如果同一子网内的设备被路由器隔开，那么即使处于同一 IP 网段，也无法进行通信。  

## 可变长子网掩码（VLSM，即 Variable Length Subnet Mask）
假如某公司拿到一个 B 类网络空间（抱歉，有钱真的可以为所欲为.gif），假如为 `172.114.0.0/16`（前略，65536 个主机地址），他反手用 CIDR 划了个 `255.255.255.0` 的子网掩码，于是他获得了 256 个网络空间，正好分配给他 200 多家分公司用。  

但将各个分公司的各个部门连接在一起的路由器之间组成的局域网（详情搜索 `网络拓扑`），它也是一种局域网，受到同主类别网络相同掩码的约束也必须使用 24 位掩码，而实际上它根本用不了这么多（如果这个网络空间只需要用 8 个主机地址，那么就浪费了 248 个原本可用的主机地址。暂时这样认为，具体详见下一节网段可用 IP），怎么办？  

他就可以利用 VLSM 再进一步划分网络空间，比如把子网掩码改成 `255.255.255.248`，那么就获得了一个仅 4 个主机地址的小网络空间「比方说 `172.114.112.0/30`、`172.114.112.4/30`、`172.114.112.8/30`、`172.114.112.12/30`」，专供路由器使用。  

不仅限于三级子网，VLSM 甚至可以继续再分。比如集团下有多分公司，分公司下有多部门，部门下有多分部，分部下有多团队，团队下有多项目组……只要 IP 够，使用 VLSM 技术可以无限再分 ~~跟左派一样~~。  

## 网段可用 IP
不是网络空间有多少主机地址就能分配多少主机地址出去。  
每个网段第一个 IP **一定**是网络 IP。  
每个网段最后一个 IP **一定**是广播 IP。  
因此一个网段可用 IP 数量应该是该网段拥有的 IP 数量 - 2。  

## 特殊 IP
整个 IPv4 的网络 IP `0.0.0.0`，它意味着 IPv4 中的全体（或者说任何，它不是 someone，它是 anyone）IP。  

特殊的广播 IP：`255.255.255.255`，它是所有设备通用的广播 IP，它不在乎你是什么时间什么地址发送了什么消息，它唯一的作用是作为「网关」。  
比如当你的手机连进一个新的无线网，如果你的手机支持，如果你留意显示的过程，它会显示先成功连接到当前 Wi-Fi，然后显示「正在获取可用 IP」。  
中间的过程就是设备（你的手机）加入局域网之后，并不知道「我是谁我在哪」，于是它发送了一条广播到（默认）网关 `255.255.255.255` 问「我是谁这是哪」，网关告诉它「你个小必宰治又来蹭网了，但跟我这个无情的 DHCP 机器又有什么关系呢」然后分配了一个 IP。于是设备就在这个局域网中确定了自己的位置，并通过路由器连接到外部广域网（或者说公网 / 外网 / 互联网）。  

## IP 分配
我们知道全球通用且唯一的 IP 地址是上级分发的，那这一块到底是谁在管理呢？  

所有 IP 都由 IANA（Internet Assigned Numbers Authority，互联网号码分配局）管理，他们将大量 IP 地址分配给世界各地的 RIR（Regional Internet Registry，区域性互联网注册管理机构）。不同地区的 RIR 有不同的名字，比如我们的是 APNIC（Asia-Pacific Network Information Centre，即亚太地址网络信息中心）。  

IANA 管不过来全世界，那 RIR 就管得过来这么辽阔一块地区了吗，也不能，所以 RIR 除了给一些大客户提供服务之外，继续把 IP 分配给自己区域内各地的 ISP（Internet Service Provider，互联网服务提供商）。  

ISP 拿到 IP 资源再分配给小客户。  

## 公共 IP 和私有 IP
由于 IPv4 的资源实在有限，近年来更是形式严峻，濒临耗尽。  

> 如果我没记错的话，我国 17 年就大力推行 IPv6，强制关乎民生的网络服务（堪称互联网基础设施）的几家互联网企业兼容 IPv6，因此腾讯阿里系的 APP 如果你注意观察启动页，下面都会有一行小字「支持 IPv6 网络」。  
> 不过话说回来都 2021 年了，我调下光猫挂 DDNS 都能用 PC 跑个 IPv6 网站，支持 IPv6 实在算不上什么新鲜事了。  

1990 年 IANA 就预测到了这一点，结合实际需求，提出了名为 RFC1918 的标准，这个标准中保留了一些 IP 资源供私人使用：  
* A 类：`10.0.0.0/8` 即 `10.0.0.0` \~ `10.255.255.255`  
* B 类：`172.16.0.0/12` 即 `172.16.0.0` \~ `172.31.255.255`  
* C 类：`192.168.0.0/16` 即 `192.168.0.0` \~ `192.168.255.255`  

这些 IP 被本地或者私有内部局域网使用。  
除此之外的 IP 都是公共 IP。  
