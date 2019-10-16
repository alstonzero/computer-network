## 1-3 Network Componet



### Parts of a Network

![](https://raw.githubusercontent.com/alstonzero/computer-network/master/Week1/1-3_01.png)

node可以是 host，router

![](https://raw.githubusercontent.com/alstonzero/computer-network/master/Week1/1-3_02.png)

### Componet Names

![](https://raw.githubusercontent.com/alstonzero/computer-network/master/Week1/1-3_03.png)

end-system:终端系统 ；edge device:

intermeditae system:中介系统



### Types of Links

#### **Full-duplex** (全双工通信)

又称为双向同时通信，即通信的双方可以**同时**发送和接收信息的信息交互方式。

**Bidirectional（单纤双向）**：是指在一根光纤里可以同时传输收发两个方向的光信号，就象马路上由隔离带隔开的正反两个方向的车道，两边的车辆在各自的车道上行驶，互不干扰。

#### Half-duplex(半双工)--  BIdirectional

在通信过程的任意时刻，信息既可由A传到B，又能由B传A，但只能有一个方向上的传输存在。采用半双工方式时，通信系统每一端的发送器和接收器，通过收/发开关转接到通信线上，进行方向的切换，因此，会产生时间延迟。收/发开关实际上是由软件控制的电子开关。



#### Simplex（单工通信）--Unidirecitonal（单向的）

消息只能单方向传输的工作方式。例如遥控、遥测，就是单工通信方式



### Wireless Links

#### Message is broadcast

----Received by all nodes in range  (被网络范围内所有nodes接收)

----Not a good fit with our model 

#### Often show logical links

----Not all possible connectivity

![](https://raw.githubusercontent.com/alstonzero/computer-network/master/Week1/1-3_04.png)

### Network namse by scale

![](https://raw.githubusercontent.com/alstonzero/computer-network/master/Week1/1-3_05.png)

#### Network Boundaries

### What part is the "network"?

![](https://raw.githubusercontent.com/alstonzero/computer-network/master/Week1/1-3_06.png)

### What part represents an "ISP"?

![](https://raw.githubusercontent.com/alstonzero/computer-network/master/Week1/1-3_07.png)

The ISP typically dosen't include the host and applications and the age of the network.



### Key Interface

1、Network-application interfaces define how apps use the network

----Sockets are widely used in parctice

![](https://raw.githubusercontent.com/alstonzero/computer-network/master/Week1/1-3_08.png)

2、Network-network interfaces define how nodes works togeter

----Traceroute can peek in the network

![](https://github.com/alstonzero/computer-network/blob/master/Week1/1-3_09.png?raw=true)