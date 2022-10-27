- #+BEGIN_PINNED
  Bryant, R. E., & O’Hallaron, D. R. (2016). 深入理解计算机系统 (龚奕利 & 贺莲, Trans.; Third Edition). 机械工业出版社.p29-34
  #+END_PINNED
- 对一个多字节的程序对象，在大多数计算机上它的存储都是连续的。要使用它需要关注的主要是两个方面:
	- **对象的位置**
		- 对象的位置在它所使用的字节中最小的那个地址
	- **对象如何排列**
		- [[R1A1A1 --- Big Endian]]大端法
		- [[R1A1A2 --- Little Endian]]小端法
		- [[R1A1A3 --- show_bytes.c]] 查看对象在系统中的排列
		- [[R1A1A4 --- 字符串的表示]]
-