# Week2

## 2-1 Physical Layer Overview

### Scope(范围) of the Pyhsical Layer

#### Concerns how signals are used to transfer message bits over a link

——Wires etc. carry analog signals(模拟信号)

——We want to send digital bits()



### Simple Link Model

We'll end with an abstarction of a physical channel

——Rate(or bandwidth(带宽),capacity(容量),speed(速度)) in bits/second

——Delay(延迟) in seconds,related to length

![](https://raw.githubusercontent.com/alstonzero/computer-network/master/week2/pic/2-1_02.png)

#### Other important properties（属性）:

——Whether the channel is broadcast,and its error rate

### Message Latency(延迟时间)

![](https://raw.githubusercontent.com/alstonzero/computer-network/master/week2/pic/2-1_03.png)

transmission delay:传输延迟 把信息放到wire上所用时间

propagation delay:传播延迟 信息在wire上传播所用的时间

### Meteic Units

#### The main prefixes we use:

![](https://raw.githubusercontent.com/alstonzero/computer-network/master/week2/pic/2-1_04.png)

#### Use powers of 10 for rates,2 for storage

1 Mbps = 1,000,000bps, 1KB = 2^10 bytes



### Lantency Examples

![](https://raw.githubusercontent.com/alstonzero/computer-network/master/week2/pic/2-1_05.png)

### Bandwidth-Delay Product 带宽时延积

带宽时延乘积指的是一个数据链路的能力（每秒比特）与来回通信延迟（单位[秒](https://baike.baidu.com/item/秒)）的[乘积](https://baike.baidu.com/item/乘积)。

![](https://raw.githubusercontent.com/alstonzero/computer-network/master/week2/pic/2-1_06.png)

## 2-2 Media

### Types of Media

####　Media propagate(传播) signals that carry bits of information

#### We'll look at some common types:

——Wires （有线）

——Fiber (fiber optics cables 光纤)

——Wireless

### Wires----Twisted Pair（双绞线）

#### Very common;used in LANs and telephone lines

——Twists reduce radiated signal(传播信号)

![](https://raw.githubusercontent.com/alstonzero/computer-network/master/week2/pic/2-2_01.png)



### Wires----Coaxial Cable（同轴电缆）

#### Also common.Better shielding for better performance

![](https://raw.githubusercontent.com/alstonzero/computer-network/master/week2/pic/2-2_02.png)



#### Other kinds of wires too

### Fiber

#### Long,thin,pure strands of glass

----Enormous bandwidth(巨大的带宽)(high speed) over long distances

![](https://raw.githubusercontent.com/alstonzero/computer-network/master/week2/pic/2-2_03.png)



### Two varieties(两种):multi-mode(shorter links,cheaper) and single-mode(up to ~100km)

![](https://raw.githubusercontent.com/alstonzero/computer-network/master/week2/pic/2-2_04.png)

### Sender radiates（传播） signal over a region

——In many directions,unlike a wire,to potentially(潜在的) many receivers

——Nearby signals(same freq.)interfere at a receiver;need to coordinate use.

![](https://raw.githubusercontent.com/alstonzero/computer-network/master/week2/pic/2-2_05.png)

#### Microwave，3G，and unlicensed(ISM) frequencies,e.g.,WiFi,are widely used for computer networking



![](https://raw.githubusercontent.com/alstonzero/computer-network/master/week2/pic/2-2_06.png)