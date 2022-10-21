- #+BEGIN_PINNED
  Lippman, S. B., Lajoie, J., & Moo, B. E. (2013). C++ Primer 中文版 (王刚 & 杨巨峰, Trans.; 5th ed.). 电子工业出版社.p221-223
  #+END_PINNED
- 函数指针指向函数，它的类型由参数和返回值决定。
- ## 声明和赋值
	- ```C++
	  bool lengthCompare(const &string, const &string);
	  
	  bool (*pf) (const &string, const &string); 
	  
	  pf = lengthCompare; // 或者 pf = &lengthCompare
	  ```
	- 上例中，`pf`是指向参数列表为`(const &string, const &string)`，返回值为`bool`的指针。所以可以用`lengthCompare`对其赋值。
- ## 重载函数的指针
	- 如果指向的是重载函数，需要提供足够的上下文，来让编译器决定使用哪个函数。
	- ```C++
	  void ff(int);
	  void ff(unsigned int);
	  
	  void (*pf) (int) = ff;
	  void (*pf1) (unsigned int) = ff;
	  ```
- ## 函数指针形参
	- 和数组类似，不能直接将函数作为函数的参数，但可以将函数指针作为函数的参数使用。
	- 使用函数指针作为形参时虽然看起来像是一个函数，但其是自动转换成了函数指针。
		- ```C++
		  //第三个形参是函数类型，但它会自动转换成指针类型
		  void useBigger(const string &s1, const string &s2, 
		                bool pf(const string &, const string &));
		  
		  //等价声明
		  void useBigger(const string &s1, const string &s2, 
		                bool (*pf)(const string &, const string &));
		  
		  ```
	- 直接将函数作为实参使用，此时他会自动转换成指针。
		- ```C++
		  //自动将lengthCompare转换成该函数的指针
		  useBigger(s1, s2, lengthCompare);
		  ```
	- ### 使用typedef简化函数指针的使用
		- **简化**
			- ```C++
			  // Func和Func1是函数类型
			  typedef bool Func(const string&, const string&);
			  typedef decltype(lengthCompare) Func1;
			  
			  // FuncP和FuncP1是函数指针
			  typedef bool (*FuncP)(const string&, const string&);
			  typedef decltype(lengthCompare) *FuncP1;
			  ```
				- 注意到`decltype`推导出来的是函数类型，利用`typedef`的特性在要定义的名字前面加`*`来指定类型为指针类型。
		- **使用**
			- ```C++
			  //等价声明
			  void useBigger(const string&, const string&, Func);
			  void useBigger(const string&, const string&, FuncP);
			  ```
				- 注意到上明两个是等价声明，第一条声明里的`Func`虽然是函数类型，但自动转换成了函数指针。
- ## 返回指向函数的指针
	- 和数组类似，虽然不能直接返回函数，但可以返回指向函数的指针。
	- ### 简化
		- 使用`typedef`或`using`来简化要返回的类型
			- ```C++
			  using F = int(int*, int); 		//F是函数类型
			  using PF = int(*)(int*, int);	//PF是函数指针
			  ```
	- ### 使用
		- ```C++
		  PF f1(int);	//正确，返回函数指针
		  F f2(int);	//错误，不能直接返回函数
		  F *f3(int);	//正确，返回函数指针
		  ```
			- 注意到，若简化的是函数类型，需要添加`*`来让返回类型变成指针。
	- ### 若不简化？
		- 1. 考虑`int (*f1(int))(int *, int)`:
			- 从内到外分析，`f1`带参数列表，说明它是一个函数。前面带一个`*`，说明它返回的是一个指针。这个指针带参数列表和返回类型，说明这个指针是个函数指针。
		- 2. 使用尾置类型`auto f1(int) -> int (*)(int*, int)`
	-
-