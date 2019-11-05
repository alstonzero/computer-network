## 3-2 Multiplexing

网络链路可以分成两大类：点到点连接和广播信道。

广播信道：所有主机共享通信介质。

在任何一个广播网络中，关键的问题是当多方竞争信道使用权时如何确定谁可以使用信道。

用来确定多路访问信道的下一个使用者的协议属于数据链路层的一个子层，该层称为<u>介质访问控制(MAC)</u>



Multiplexing is the network word for the <u>sharing of a resource</u>

Classic scenario is sharing a link among different

### Time Dividion Multiplexing(TDM)

时分多路复用——频率相同，不同时间交替使用

#### User take turns on a fixed schedule

将时间划分为一段段等长的时分复用帧(TDM帧)。每一个时分复用的用户在每一个TDM帧中占用固定序号的时隙，所用用户轮流占用信道。

![](https://raw.githubusercontent.com/alstonzero/computer-network/master/week3/pic/3-2_01.png)



### Frequency Division Multiplexing(FDM)

频分多路复用——同一时间，分频使用

如果总共有N个用户，则整个带宽会被分成N等份，每个用户获得一份。由于每个用户都有各自专用的频段，所以用户间不会发生干扰。

#### put different users on different frequency bands

![](https://raw.githubusercontent.com/alstonzero/computer-network/master/week3/pic/3-2_02.png)



### TDM vs FDM

In TDM a user sends at a high rate a fraction of the time;in FDM,a user sends at a low rate all the time.

 ![](https://raw.githubusercontent.com/alstonzero/computer-network/master/week3/pic/3-2_03.png)



### TDM/FDM Usage

#### Statically divide a resource

——Suited for continuous traffic,fixed number of users

#### Widely used in telecommunications

——TV and radio stations(FDM)

——GSM(2G cellular)allocates calls using TDM within FDM

### Multiplexing Network Traffic

#### Network traffic is <u>bursty</u>

——ON/OFF sources

——Load varies greatly over time

——Inefficient to always allocate user their ON needs with TDM/FDM

![](https://raw.githubusercontent.com/alstonzero/computer-network/master/week3/pic/3-2_04.png)

#### <u>Multiple access</u> schemes multiplex users according to their demands ——for gains of statistical multiplexing

![](https://raw.githubusercontent.com/alstonzero/computer-network/master/week3/pic/3-2_05.png)



### Multiple Access

#### We will look at two kinds of multiple access protocols

**1.Randomized.Nodes randomize their resource access attempts**

——Good for low load situations

**2.Contention-free.Nodes order their resource access attempts**

——Good for high load or guaranteed quality of service situations



### 