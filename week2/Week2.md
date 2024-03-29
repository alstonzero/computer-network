# Week2

## 2-1 Physical Layer Overview

### Scope(范围) of the Pyhsical Layer

#### Concerns how signals are used to transfer message bits over a link

——Wires etc. carry <u>analog signals</u>(模拟信号)

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

双绞线由两根相互绝缘的铜线组成，铜线的直径大约是一毫米。两根铜线以螺旋状的形式紧紧地绞在一起，就像一个DNA分子链。当两根线绞在一起后，不同电线产生的干扰波会相互抵消，从而能显著降低电线的辐射。<u>信号通常以两根电线的电压差来承载</u>，这样对外部噪声有更好的免疫力。因为噪声对两根电线的干扰是相同的，而它们的电压差却不会改变。

——Twists reduce <u>radiated signal</u>(传播信号)

![](https://raw.githubusercontent.com/alstonzero/computer-network/master/week2/pic/2-2_01.png)



### Wires----Coaxial Cable（同轴电缆）

#### Also common.Better shielding for better performance
它比非屏蔽的双绞线有更好的屏蔽特性和更大的带宽，所以它能以很高的速率传输相当长的距离。同轴电缆的结构和屏蔽性使得它既有很高的带宽，又拥有很好的抗噪性。带宽可能取决于电缆的质量和长度。

![](https://raw.githubusercontent.com/alstonzero/computer-network/master/week2/pic/2-2_02.png)



#### Other kinds of wires too

### Fiber(光纤)

#### Long,thin,pure strands of glass

#### 光纤传输系统由三个关键部件组成：光源，传输介质和探测器。
一个光脉冲表示比特1，没有光脉冲表示比特0。传输介质是超波玻璃纤维。光探测器探测光时产生一个电脉冲。在光纤两端分别接上光源和探测器，我们就有了单向数据传输系统。该系统接收电子信号，将其转换成光脉冲并传输出去，然后在另一端把光脉冲转换回电子信号输出给接收端。

----<u>Enormous bandwidth</u>(巨大的带宽)(high speed) over long distances

![](https://raw.githubusercontent.com/alstonzero/computer-network/master/week2/pic/2-2_03.png)



### Two varieties(两种):multi-mode(shorter links,cheaper) and single-mode(up to ~100km)

![](https://raw.githubusercontent.com/alstonzero/computer-network/master/week2/pic/2-2_04.png)
(a)单根光纤侧面图 (b)三根光纤的横截面视图

### Sender radiates（传播） signal over a region

——In many directions,unlike a wire,to potentially(潜在的) many receivers

——Nearby signals(same freq.)interfere at a receiver;need to coordinate use.

![](https://raw.githubusercontent.com/alstonzero/computer-network/master/week2/pic/2-2_05.png)

#### Microwave，3G，and unlicensed(ISM) frequencies,e.g.,WiFi,are widely used for computer networking



![](https://raw.githubusercontent.com/alstonzero/computer-network/master/week2/pic/2-2_06.png)


ISM:Industrial,Scientific,Medical 工业科学医学。
例如：车库门控制器、无绳电话、无线电遥控的玩具，无线鼠标等。


## 2-4  Moudlation(调制)

### Topic

#### We've talked about <u>signals representing bits</u>.How exactly?（具体如何用信号来表示bits）
有线和无线信道运载模拟信号，模拟信号可表示成诸如连续变化的电压、光照强度或声音强度。为了发送数字信息，我们必须设法用模拟信号来表示比特。
比特与代表它们的信号之间的转换过程成为 **数字调制（digital modulaton）**

——This is the topic of <u>modulation</u>

![](<https://raw.githubusercontent.com/alstonzero/computer-network/master/week2/pic/2-4_01.png>)
#### Baseband transmission(基带传输):有线介质普遍使用
即信号的传输占有传输介质上从<u>零到最大值</u>之间的全部频率，而最大频率则取决于信令速率。

#### Passband transmission(通带传输):无线和光纤普遍使用
即信号占据了以载波信号频率为中心的一段频带。在无线和光纤这样的传输介质中只能在给定的频带中传输信号。

### 1、基带传输 

#### A simple Modulation—— NRZ(Non-Return to Zero，不归零编码)

#### Let a high vlotage(+V)(高电压) represent a 1,and low voltage(-V)(低电压) represent a 0


![](<https://raw.githubusercontent.com/alstonzero/computer-network/master/week2/pic/2-4_02.png>)



### Many Other Schemes(方案)

#### Can use more signal levels,e.g.,4 levels is 2 bits per symbol

![](<https://raw.githubusercontent.com/alstonzero/computer-network/master/week2/pic/2-4-_02.png>)
利用有限带宽的一种更有有效的策略是**使用两个以上的信号级别**，例如采用4个电压级别，我们可以用单个符号(symbol)一次携带2个比特。


#### Practical schemes(实用方案) are driven by engineering considerations

**——E.g, clock recovery**(时钟恢复)

### Clock Recovery(时钟恢复)

#### how many zeros was that?
在NRZ编码方法中。符号简单地对应为电压等级，一长串的0或1使信号级别保持不变。经过一段时间以后，接收器很难区分出各个比特，比如15个0看起来像16个0，除非有一个非常准确的时钟。

——Receiver needs frequent signal transitions to decode bits.

接收器需要频繁的信号转换来解码bits

![](<https://raw.githubusercontent.com/alstonzero/computer-network/master/week2/pic/2-4_03.png>)

#### Several possible designs

**——E.g. Manchester coding（曼彻斯特编码） and scrambling(扰码)**

### Clock Recovery——4B/5B（编码）
目的：解决一长串的0。

#### Map every 4 data bits into 5 code bits without long runs of zeros

4B/5B的思想是在比特流中插入额外的比特以打破一连串的0或1。准确地讲，就是用5个比特来编码4个比特的数据，之后再传给接收方，因此称为4B/5B。

![](<https://raw.githubusercontent.com/alstonzero/computer-network/master/week2/pic/2-4_04.png>)

#### ——Has at most 3 zeros in a row （至多一行有三个0）

5比特代码是由以下方式选定的：每个代码最多有1个前导0，并且末端最多有两个0。因此，当连续传送时，在传输过程中任何一对5比特代码连续的0最多有3个。且永远不会出现连续三个0。

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

## 2-5
## Limits

### How rapidly can we send information over a link?

#### ——Nyquist limit （奈奎斯特定理/采样定理）
奎尼斯特公式：表示一个有限带宽的无声噪信道的最大传输率。


#### ——Shannon capacity （香农定理）

### Practiacal systems are devised to approach these limits

### Key Channel Properties

#### The bandwidth(B),signal strength(S),and noise strength(N)

——B limits the rate of transitions	B带宽限制了传输速率

——S and N limit how many signal levels we can distinguish	 

![](<https://raw.githubusercontent.com/alstonzero/computer-network/master/week2/pic/2-5_01.png>)

### Shannon Capacity香农定理

香农定理给出了信道信息传送速率的上限（比特每秒bit/s）和信道信噪比(S/N)及带宽(B)的关系。香农定理可以解释现代各种无线制式由于带宽不同，所支持的单载波最大吞吐量的不同。

#### How many levels we can distinguish depends on S/N（信噪比）

——Or **SNR**, the <u>Signal-to-Noise Ratio</u>	

（注：**信噪比**（英语：**Signal-to-noise ratio**，缩写为**SNR**或**S/N**），又称**訊噪比**，是科学和工程中所用的一种度量，用于比较所需[信号](https://zh.wikipedia.org/wiki/信号_(信息论))的强度与背景噪声的强度。其定义为信号功率与噪声功率的比率，以[分贝](https://zh.wikipedia.org/wiki/分貝)（dB）为单位表示。大于比率1:1（高于0分贝）表示信号多于噪声。信噪比通常用于描述电子信号，也可以应用在各种形式的信号，比如冰芯内的同位素量，或细胞间的生物化学信号。）

——Note noise is random, hence some errors(噪音是随机的，因此有错误)

#### SNR　given　on　a　log-scale（对数标尺）	in	deciBels（分贝）:	

通常情况下为了适应很大的范围，该比率表示成对数形式——SNR(dB) = 10log10(S/N)	
对数的取值单位为分贝(dB)。例如：10的信噪比是10分贝，100的信噪比是20分贝，1000的信噪比是30分贝。

![](<https://raw.githubusercontent.com/alstonzero/computer-network/master/week2/pic/2-5_02.png>)

#### Shannon limit is for capacity(C), the maximum information carrying rate of the channel:	
对于一条带宽为B Hz、噪声比是S/N的有噪声信道，其最大数据速率或者容量(capacity)是

![](<https://raw.githubusercontent.com/alstonzero/computer-network/master/week2/pic/2-5_03.png>)



### Wired/Wireless Perspective

#### Wires,and　Fiber（有线和光纤）

——Engineer link to have requisite SNR and B

——Can fix data rate	

#### Wireless（无线）

——Given	B,	but	SNR	varies	greatly,	e.g.,	up	to	60	dB!	

——Can’t	design	for	worst	case,	must	adapt	data	rate	

## 2 -6 Framing

### Topic

#### The Physical layer gives us a stream of bits.How do we interpret it as a sequence of frames?

对于数据链路层来说，通常的做法是将比特流拆分成多个离散的帧，为每个帧计算一个称为校验和的短令牌，并将该校验和放在帧中一起传输。

当帧达到目标机器时，要重新计算该帧的校验和。如果新算出来的校验和与该帧中包含的校验和不同，则数据链路层知道传输过程中产生了错误，它就会采取措施来处理错误。



### Framing Methods(成帧方法)

#### Byte count(motivation):字节计数法

#### Byte stuffing：字节填充的标志字节法

#### Bit stuffing:比特填充的标志字节法



#### IN practice,the physical layer often helps to identify frame boundaries

—E.g.,Ethernet,802.11

### Byte Count——字节计数法

#### First try:

#### ——Let's start each frame with a length field!

利用头部中的一个字段来标识该帧中的字符数。

![](https://raw.githubusercontent.com/alstonzero/computer-network/master/week2/pic/2-6_01.png)

#### 这个算法的问题在于计数值有可能因为一个传输错误而被弄混

#### Difficult to re-synchronize(重新同步) after framing error

![](https://raw.githubusercontent.com/alstonzero/computer-network/master/week2/pic/2-6_02.png)



### Byte Stuffing——字节填充法

#### Better idea：考虑到了出错之后的重新同步问题

#### —— Have a special flag byte value that means start/end of frame

每个帧用一些特殊的字节作为开始和结束。

#### ——Replace ("stuff")the flag inside the frame with an escape code

每个标志字节的前面插入一个特殊的转义字节(ESC)

#### ——Complication:have to escape the escape code too!

如果转义字节也在数据中，答案是同样的，即用一个转义字节来填充 

![](https://raw.githubusercontent.com/alstonzero/computer-network/master/week2/pic/2-6_03.png)

#### Rules:

#### ——Replace each FLAG in data with ESC FLAG

#### ——Replace each ESC in data with ESC ESC

![](https://raw.githubusercontent.com/alstonzero/computer-network/master/week2/pic/2-6_04.png)

### Bit Stuffing——比特填充法



![](https://raw.githubusercontent.com/alstonzero/computer-network/master/week2/pic/2-6_05.png)



### Link Example:PPP over SONET



#### PPP is Point-to-Point Protocol 点到点协议

#### Widely used for link framing

使用链路发送数据包

——E.g it is used to frame IP packets that are sent over SONET optical links

#### Think of SONET as a bit stream,and PPP as the framing that carries and IP packet over the link

SONET是物理层协议，它最常被用在广域网的光纤链路上。

为了在链路上承载数据包。运行在IP路由上的PPP提供了这个成帧机制。

![](https://raw.githubusercontent.com/alstonzero/computer-network/master/week2/pic/2-6_06.png)

#### Framing uses byte stuffing

#### ——FLAG is 0x7E and ESC is 0x7D

![](https://raw.githubusercontent.com/alstonzero/computer-network/master/week2/pic/2-6_07.png)

#### Byte stuffing method
#### ——To stuff(unstuff) a byte,add(remove) ESC(0x7D),and XOR byte with 0x20
#### ——Removes FLAG from the contenes of the frame.

所有的PPP帧都从标准的HDLC标志字节0x7E(01111110)开始。标志字节0x7E如果出现在Payload字段，则要用转义字节0x7D去填充；然后将紧跟在后面的那个字节与0x20进行XOR操作。
0x7E ————> 0x7D5E
0x7D ————> 0x7D5D
例如，0x7D 0x5E是标志字节0x7E的转义序列。这意味着只要简单扫描0x7E就能找出帧的开始和结束之处，因为这个字节不可能出现在其他地方。


### 2-7  Error Overview

#### Some bits will be received in error due to noise.

What can we do?

——Detect errors with codes

——Correct errors with codes

——Retransmit lost frames 

#### Reliablity is a concern that cuts across the layers-we'll see it again



### Approach——Add Redundancy

#### Error detection codes

—— Add <u>check bits</u> to the message bits to let some errors be detected

#### Error correction codes

——Add more <u>check bits</u> to let some errors be corrected



**Key issue is now to structure the code to detect many errors with few check bits and modest computation**

### Motiviating

#### A simple code to handle errors:

——Send two copies!Error if differnent.

#### How good is this code?

—— How many errors can it detect/correct?

—— How many errors will make it fail?



#### We want to handle more errors with less overhead

——Will look at better code;they are applied mathematics

——But,they can't handle all errors

——And they focus on accidental errors(wiil look at secure hashes later)



### Using Error Code

#### Codeword consits of D data plus R check bits(=systematic block code)



#### Sender:

——Compute R check bits based on the D data bits;send the codeword of D+R bits



### Receiver:

——Receive D+R bits with unknown errors

——Recompute R check bits based on the D data bits;error if R dosen't matvh R'



### Intuition for Error

#### For D data bits,R check bits:



#### Randomly chosen codeword is unlikely to be correct;overhead is low





### Hamming Distance

#### Distance is the number of bit flips needed to change D1 to D2



#### <u>Hamming distance</u> of a code is the minimum distance between any pair of codewords



#### Error detection:

——For a code of distance d+1,up to d errors will always be detected.





——For a code of distance 2d+1,up to d errors can always be corrected by mapping to the closest codeword.


## 2-8 Error Detection



### Simple Error Detection——Parity Bit（奇偶）

#### Take D data bits,add 1 check bit that is the sum of the D bits

把单个奇偶校验位附加到数据中。

#### ——Sum is modulo 2 or XOR



**How well does parity work?**

#### The distance of the code is 2.

具有单个校验位的编码具有码距2

#### Detect 1 error ，correct 0 error

奇偶码可以检测出1个错误，不能改正错误



### CheckSum 校验和

#### Idea:sum up data in N-bit words 

——widely used in,e.g,TCp/IP/UDP

校验和通常放在消息的末尾。通过对整个接收到的码字(包含了数据位和校验和)进行求和计算就能检测出错误



#### Stronger protection than parity 



#### Example——Internet Checksum

Internet 校验和，是按16位字计算得出的消息位总和。由于此方法针对字而不是像奇偶校验那样针对位进行操作，因此奇偶校验没能检出的错误此时仍然可以检出。

#### Sending : 发送方步骤

1.Arrange data in 16-bits words.

2.Put zero in checksum position,add 把0放到校验和的位置上，并相加

3.Add any carryover back to get 16bits  任何高序位溢出被放回到低序位上

4.Negate(complement)to get sum 

加图

#### Receiving 接收方步骤



#### The distance of the code is 2.

#### It can detect 1 error and correct 0.



### CRC   循环冗余校验码

也称作多项式编码。

#### 基本思想：将位串看成是系数为0或1的多项式。

一个k位帧(frame)看作是一个k-1次多项式的系数列表，该多项式共有k项，从x^k-1到x^0。

e.g 1、1、0、0、0、1，即 1x^5+1x^4+0x^3+0x^2+0x^1+1x^0

多项式算数运算以2为模完成，加法没有进位，减法没有退位。





## 2-9 Error Correction

### Use Hamming code to fix error

### 为了可靠检测d个错误，需要一个距离为d+1的编码方案

**Suppose we construct a code with a Hamming distance of at least3**

**——Need >=3 bit errors to change one valid codeword into another (需要大于3bits的错误才能把一个有效编码转换成另一个)**

**——Single bit errors will be closest to a unique valid codeword**

因为在这样的编码方案中，d个1位错误不可能将一个有效码字改变成另一个有效码字。

### 为了纠正d个错误，需要一个距离为2d+1的编码方案

**If we assume errors are only 1 bit,we can correct them by mapping an error to the closet valid codeword **

**——Works for d errors if HD >=2d+1**

因为在这样的编码方案中，合法码字之间的距离足够远，即使发生了d位变化，结果还是离它原来的码字最近。

### Hamming Code 海明方法

#### 2的幂次方的位是校验位，其余位是用来填充数据

Gives a method for constructing a code with a distance of 3

**——Uses n=2^k - k - 1,e.g n = 4,k=3**

——Put check bits in position p that are powers of 2,starting with position 1

——Check bit in position p is parity of positions with a p term in their values

#### Example:data=0101,3 check bits

—— 7 bit code,check bit positions 1,2,4

——Check 1 covers positions 1,3,5,7 

——Check 2 covers positions 2,3,6,7

——Check 4 covers positions 4,5,6,7

**校验码的具体计算方法如下：**

```
p1（第1个校验位，也是整个码字的第1位）的校验规则是：从当前位数起，校验1位，然后跳过1位，再校验1位，再跳过1位，……。这样就可得出p1校验码位可以校验的码字位包括：第1位（也就是p1本身）、第3位、第5位、第7位、第9位、第11位、第13位、第15位，……。然后根据所采用的是奇校验，还是偶校验，最终可以确定该校验位的值。

p2（第2个校验位，也是整个码字的第2位）的校验规则是：从当前位数起，连续校验2位，然后跳过2位，再连续校验2位，再跳过2位，……。这样就可得出p2校验码位可以校验的码字位包括：第2位（也就是p2本身）、第3位，第6位、第7位，第10位、第11位，第14位、第15位，……。同样根据所采用的是奇校验，还是偶校验，最终可以确定该校验位的值。

p3（第3个校验位，也是整个码字的第4位）的校验规则是：从当前位数起，连续校验4位，然后跳过4位，再连续校验4位，再跳过4位，……。这样就可得出p4校验码位可以校验的码字位包括：第4位（也就是p4本身）、第5位、第6位、第7位，第12位、第13位、第14位、第15位，第20位、第21位、第22位、第23位，……。同样根据所采用的是奇校验，还是偶校验，最终可以确定该校验位的值。
```

![](https://raw.githubusercontent.com/alstonzero/computer-network/master/week2/pic/2-9_01.png)



#### To decode:

接收方检查错误

1、没有错误的情况

![](https://raw.githubusercontent.com/alstonzero/computer-network/master/week2/pic/2-9_02.png)

2、有错误的情况

![](https://raw.githubusercontent.com/alstonzero/computer-network/master/week2/pic/2-9_03.png)

### Other Error Correction

#### Convolutional codes 卷积码

卷积码处理一个输入位序列，并生成一个输出序列

——Take a stream of data and output a mix of the recent input bits

——Makes each output bit less fragile

——Decode usinig Viterbi algorithm



#### Other Codes——LDPC 低密度奇偶校验码

——LDPC用一个 1 的密度很低的矩阵表示

——接收到的码字通过一个近似算法解码获得

——

**LDPC码比较适用于大块数据，具有出色的纠错能力，性能优越，迅速被新的协议所采用。**，

Heavily used in physical layer 



### Detection vs. Correction

在高度可靠的信道上（比如光纤）较为合理的做法是使用检错码，当偶尔发生错误时只需重传整个数据块。

然而在错误发生频繁的信道上（比如无线线路），更好的做法是在每一个数据块中加入足够的冗余信息，以便接收方能够计算出原始的数据块。



#### 1,Assume bit errors are random 偶尔出现的错误

——Message have 0 or maybe 1 error 孤立的单个比特错误

#### Error correction:

——Need ~10 check bits per message

——Overhead 10

#### Error detection

——Need ~10 check bits per message plus 1000 bit retransmission 1/10 of the time



#### 2,Assume errors come in bursts of 100

错误以100个bit的突发形式出现 

——Only 1or 2 messages in 1000 have errors

#### Error correction:

——Need >>100 check bits per message

—— Overhead ： 》100

#### Error detection

——More efficient when errors are not expected

——And when errors are large when they do occur



#### 检错码经常被用在链路层、网络层和传输层

#### 纠错码被用在链路层，也会出现在物理层
