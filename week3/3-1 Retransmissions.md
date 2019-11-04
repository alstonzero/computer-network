## 3-1 Retransmissions

### Two strategies to handle error:

#### 1.Detect error and retransmit frame

2.Correct error with an error correcting code(第二章)

**注：**

一个帧由4个字段组成：kind、seq、ack、info。

seq和ack分别用作序号和确认。

### ARQ 自动重复请求

发送方在前移到下一个数据之前必须等待一个肯定确认。

ARQ often used when errors are common or must be corrected.

——E.g.,WiFi,and TCP

Rules at sender and receiver:

——Receiver automatically acknowledges correct frames with an ACK

——Sender automatically resends after a timeout, until an ACK is received.

#### Normal operation（ no loss）

![](<https://raw.githubusercontent.com/alstonzero/computer-network/master/week3/pic/3-1_01.png>)

#### Loss and retransmission

![](<https://raw.githubusercontent.com/alstonzero/computer-network/master/week3/pic/3-1_02.png>)



### Tricky about ARQ

#### Two non-trivial issues:

#### 1.Timeout

**Timeout should be:**

——Not too big(link goes idle)

——Not too small (Spurious resend)

**Fairly easy on a LAN**

——Clear worst case,little variation

**Fairly difficult over the Internet**

——Much variation,no obvious bound

——We'll revisit this with TCP(later)

#### ACK is lost

![](https://raw.githubusercontent.com/alstonzero/computer-network/master/week3/pic/3-1_03.png)

#### Timeout early

![](https://raw.githubusercontent.com/alstonzero/computer-network/master/week3/pic/3-1_04.png)



对接收方来说，它需要有一种方法能够区分到达的帧是第一次发来的新帧，还是被重传的老帧。

### Sequence Number 序号

让发送方在它所发送的每个帧的头部放上一个序号。接收方根据这个序号判断是新帧还是应该被丢弃的重复帧。

#### Frame and ACks must both carry sequence numbers for correctness

To distinguish the current frame from the next one,a single bit(two numbers) is sufficient 

——Called <u>Stop-and-Wait</u> 

### Sotp-and-Wait

#### In the normal case:

![](https://raw.githubusercontent.com/alstonzero/computer-network/master/week3/pic/3-1_05.png)



#### With ACK loss:

![](https://raw.githubusercontent.com/alstonzero/computer-network/master/week3/pic/3-1_06.png)



#### With early timeout:

![](<https://raw.githubusercontent.com/alstonzero/computer-network/master/week3/pic/3-1_07.png>)

### Limitation of Stop-and-Wait

局限：数据帧只在一个方向上传输

It allows only a single frame to be outstanding from the sender:

——Good for LAN,not efficient for high BD（Bandwidth delay带宽时延乘积）



### Sliding Windows ——双向协议

#### Generalization of stop-and-wait

——Allows W frames to be outstanding

——Can send W frames per RTT（Round Trip Time往返时延）（=2D）

——

