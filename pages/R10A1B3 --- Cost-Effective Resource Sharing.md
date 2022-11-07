- #+BEGIN_PINNED
  Peterson, L. L., & Davie, B. S. (2022). Computer networks: a systems approach (6th ed.). Morgan Kaufmann.c1.2.3
  #+END_PINNED
- 一个网络中的任意两个主机都可以通过一系列的链路(*link*)和节点(*node*)来传递信息。但我们想要的不仅仅是让两个host通信，而是网络里的所要主机都可以互相通信。那么这些host如何靠共享网络来通信呢？特别是它们想要同时通信的时候，或者更极端一点的，几个host如何依靠同一条链路同时进行通信呢？
- ## Multiplexing
	- 使用“多路复用”的技术可以让多个host进行link的共享。
		- ![../_images/f01-05-9780123850591.png](https://book.systemsapproach.org/_images/f01-05-9780123850591.png){:height 262, :width 461}
		- S1-S3的数据流通过Switch1 multiplexed到一条link上，并在Switch2 上 demultiplexed到3个目标数据流。
	- ### Synchronous time-division multiplexing(STDM)
		- 将时间分割成相等大小的quanta，并通过循环的方式给每个数据流在链路上发送数据的机会。
	- ### Frequency-division multiplexing(FDM)
		- 通过不同的频率在链路上发送数据，有点像电视台一句不同的频率通过电缆或者无线电波发送电视信号。
	- ### STDM和FDM的缺点
		- 如果其中又一个数据流没有数据可发，那它占用的资源就被闲置了。在STDM中表现为它占用的固定的一段时间，在FDM中表现为它占用的一个频率。
		- STDM和FDM都必须提前知道最多有多少数据流，因为在运行中STDM不能调整quantum的大小或者添加quanta，FDM不能添加新的频率。
- ## Statistial multiplexing
	-
-
	-