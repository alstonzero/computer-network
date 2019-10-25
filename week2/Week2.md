# Week2

## 2-1 Physical Layer Overview

### Scope(范围) of the Pyhsical Layer

#### Concerns how signals are used to transfer message bits over a link

——Wires etc. carry analog signals(模拟信号)

——We want to send digital bits()



### Simple Link Model

We'll end with an abstarction of a physical channel

——Rate(or bandwidth(带宽),capacity(容量),speed(速度)) in bits/second(单位)

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





## 2-4  Moudlation(调制)

### Topic

#### We've talked about <u>signals representing bits</u>.How exactly?（具体如何用信号来表示bits）

——This is the topic of <u>modulation</u>

![](<https://raw.githubusercontent.com/alstonzero/computer-network/master/week2/pic/2-4_01.png>)

### A simple Modulation

#### Let a high vlotage(+V)(高电压) represent a 1,and low voltage(-V)(低电压) represent a 0

#### ——This is called NRZ(Non-Return to Zero，不归零编码)

![](<https://raw.githubusercontent.com/alstonzero/computer-network/master/week2/pic/2-4_02.png>)



### Many Other Schemes(方案)

#### Can use more signal levels,e.g.,4 levels is 2 bits per symbol

![](<https://raw.githubusercontent.com/alstonzero/computer-network/master/week2/pic/2-4-_02.png>)

#### Practical schemes(实用方案) are driven by engineering considerations

**——E.g, clock recovery**(时钟恢复)

### Clock Recovery(时钟恢复)

#### how many zeros was that?

——Receiver needs frequent signal transitions to decode bits.

接收器需要频繁的信号转换来解码bits

![](<https://raw.githubusercontent.com/alstonzero/computer-network/master/week2/pic/2-4_03.png>)

#### Several possible designs

**——E.g. Manchester coding（曼彻斯特编码） and scrambling(扰码)**

### Clock Recovery——4B/5B（编码）

#### Map every 4 data bits into 5 code bits without long runs of zeros

4B/5B的思想是在比特流中插入额外的比特以打破一连串的0或1。准确地讲，就是用5个比特来编码4个比特的数据，之后再传给接收方，因此称为4B/5B。

![](<https://raw.githubusercontent.com/alstonzero/computer-network/master/week2/pic/2-4_04.png>)

#### ——Has at most 3 zeros in a row （至多一行有三个0）

5比特代码是由以下方式选定的：每个代码最多有1个前导0，并且末端最多有两个0。因此，当连续传送时，在传输过程中任何一对5比特代码连续的0最多有3个。

#### ——Also invert signal level on a 1 to break up long runs of 1s(called NRZI)

然后，再将得到的5比特代码使用**NRZI编码传输**，这种方式说明了为什么仅需关心多个连续0的处理，因为NRZI已解决了多个连续1的问题。注意，4B/5B编码的效率为80%。

![](<https://www.2cto.com/uploadfile/2015/0612/20150612043953464.png>)



可用于表示线路空闲，00000表示线路不通，00100表示停止。在剩下的13个码中，7个是无效的（因为它们违反了1个前导、0或两个末尾0的规则），另外6个代表各种控制符号。在本章后面将会看到，某些组帧协议会使用这些控制符号。

#### Example:



![](https://raw.githubusercontent.com/alstonzero/computer-network/master/week2/pic/2-4_05（1）.png)





### Passband Modulation(带通调制（载波调制）)

把基带信号的频率范围搬移到较高的频段，并转换为模拟信号，经过载波调制后的信号为带通信号（仅在一段频率范围内能够通过信道），而使用载波调制的调制成为带通调制。
目的: 要传输的信号加载在载波信号上进行传输,因为载波信号传得远。

最基本的调制方法：
1.调幅（AM） 例如：0或1分别对应无载波或有载波输出。 2.调频（FM） 例如：0或1分别对应频率f1或f2。
3.调相（PM） 例如：0或1分别对应相位0度或180度。

#### What we have seen so far is <u>baseband</u> modulation for wires

——Signal is sent directly on a wire 信号直接通过线发送

#### These signals do not propagate well on fiber/wireless

——Need to send at higher frequencies

#### <u>Passband</u> modulation carries a signal by modulating a carrier (通过载波来承载信号)



#### Carrier is simply a signal oscillation(信号振荡) at a desired frequency: 载波是在所需频率下的信号振荡

#### We can modulate it by changing :

![](<https://raw.githubusercontent.com/alstonzero/computer-network/master/week2/pic/2-4_06.png>)

amplitude:振幅

frequency:频率

phase:相

#### Example:

![](<https://raw.githubusercontent.com/alstonzero/computer-network/master/week2/pic/2-4_07.png>)
