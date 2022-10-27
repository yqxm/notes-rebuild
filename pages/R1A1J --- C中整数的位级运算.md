- #+BEGIN_PINNED
  Bryant, Randal E., and David R. O’Hallaron. 深入理解计算机系统. Translated by 龚奕利 and 贺莲. Third Edition. Beijing: 机械工业出版社, 2016.p37-41
  #+END_PINNED
- ## 位级运算
	- C支持按位布尔运算，运算符`|`对应“或”、`&`对应“且”、 `~` 对应“非”、`^`对应“异或”。
	- 位级运算的一个应用就是**掩码运算**，从一个字中选出你想要的位。比如将一个字和掩码`0xFF`进行`&`运算就可以获得这个字的最低8位。
	- [[R1A1J1 --- 练习 2-10]]
- ## 逻辑运算
	-