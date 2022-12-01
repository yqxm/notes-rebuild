- #+BEGIN_PINNED
  Lippman, S. B., Lajoie, J., & Moo, B. E. (2013). C++ Primer 中文版 (王刚 & 杨巨峰, Trans.; 5th ed.). 电子工业出版社. c2.4
  #+END_PINNED
- 使用`const`来定义不变量。任何对不变量的修改都会发生错误。
- 因为`const`对象一旦初始化之后就不会发生改变，所以必须对`const`对象进行初始化。
- `const`的特性只有当它被修改时才会发挥作用，只要是不改变其内容的操作都可以执行，包括使用const对象对其他对象初始化，初始化后的值与const对象没有关系。
- ==默认情况下，`const`对象仅在文件内有效==
	- 要想让`const`对象跨文件可用，不管是声明还是定义都使用`extern`。
	- ```C++
	  // file1.cc 定义并初始化了一个常量，该常量能被其他文件访问。
	  extern const int buffsize = fcn();
	  // file1.h
	  extern const int bufsize; 			//与file1.cc中的bufsize是同一个
	  ```