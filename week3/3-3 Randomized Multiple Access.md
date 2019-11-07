## 3-3 Randomized Multiple Access

### MAC(multiple access control ) protocols

—— This is the basis for classic Ethernet

——Remeber:data traffic is bursty(突发性)



### ALOHA  Network 不听就说

#### 纯ALOHA

**Simple idea**

——Node just sends when iit has traffic

当用户有数据需要发送时就传输。

——If there was a collision(no ACK received)then wait a random time and resend.

如果产生了冲突，冲突的帧将被损坏。如果帧损坏了，则发送方要等待一段随机时间，然后再次发送该帧。等待的时间必须是随机的，否则同样的帧会一次又一次地冲突。

图

**Simple，decentralized protocol that works well under <u>low load</u>!**

**Not efficient under <u>high load</u>**

——Analysis shows at most 18% efficiency

#### 分槽ALOHA

将时间分成离散的间隔，这种时间间隔称为时间槽，每个时间槽对应于一帧。

——Improvement:divide time into slots时间槽 and efficiency goes up to 36%

与纯ALOHA不同的是，在分槽ALOHA中，站不允许用户立即发送帧，必须等到下一个时槽的开始时刻。



### CSMA（Carrier Sense Multiple Access）先听再说

坚持载波检测多路访问。

当有一个数据要发送时，它首先侦听信道，确定当时是否有其他站正在传输数据；如果信道空闲，它就发送数据。否则，如果信道忙，则等待直到信道变成空闲。

#### Improve ALOHA by listening for activity before we send

——Can do easily with wires,not wireless

#### CSMA is a good defense against collisions only when BD is small

在某个站开始发送后，另一个站也刚好做好发送的准备并侦听信道。如果第一个站的信号没能到达第二个站，后者侦听到信道是空闲的，因而开始发送，由此导致双方的冲突。

这个机会取决于信道上合适的帧数，或者信道的带宽延迟积

图



### CSMA/CD(with Collision Detection碰撞检测)先听再说，边听边说

#### **带冲突检测的CSMA**

每个站快速检测到发生冲突后立即停止传输帧(而不是继续完成传输)，因为这些帧已经无可挽回的成为了乱码。这种策略可以节省时间和带宽。

Can reduce the cost  of collision by detecting them and aborting(Jam) the rest of the frame time

——Again，we can do this with wires



图

#### 传播时延对载波监听的影响 

最迟多久才能知道自己发送的数据没和别人碰撞？

Want everyone who collides（碰撞）to know that it happened

——Time window in which a node may hear of a collision is **2D seconds**

**最多是两倍的总线端到端(往返)的传播时延**

Impose a minimum frame size that lasts for 2D seconds

#### 如何确定碰撞后的重传时机？——截断二进制指数规避算法

**Binary Exponential Backoff(BEB)**

Cleverly estimates the probability

——1 st collision,wait 0 or 1 frame times

——2 nd collision,wait from 0 to 3 times

——3rd collison,wait from 0 to 7 times

定义参数k，它等于重传次数，但k不超过10，即k=min[重传次数，10]。当重传次数不超过10时，k等于重传次数：当重传次数大于10时，k就不再增大而一直等于10。

从离散的整数集合[0,1,...,2^k-1]中随机取出一个数r，重传所需要退避的时间就是r倍的基本退避时间

BEB doubles interval for each successive collision

——Quickly gets large enough to work

——Very efficient in pratice

#### Classic Ethernet,or IEEE 802.3

Most popilar LAN of the 1980s,1990s

——10 Mbps over shared coaxial cable,with baseband signals

——Multiple access with "<u>1-persisten CSMA/CD</u> with BEB"



#### 最小帧长 

A站发了一个很小的帧，但发生了碰撞，不过帧在发送完毕后才检测到碰撞，没法停止发送，因为发完了。所以要规定一个最小帧长。

帧的传输时延至少要两倍于信号在总线中的传播时延。

——So node can't finish before collision

——Ethernet minimum frame is 64 bytes

### CSMA"Persistence"

What should a node do if another node is sending?



Idea:Wait until it is done,and send



Problem is that multiple waiting nodes will queue up then collide

——More load,more of a proble,





Intuition for a better solution

——If there are N queued senders,we want each to send next with probability 1/N

图

###  Ethernet Frame Format

**Has addresses to identify the sender and receiver**