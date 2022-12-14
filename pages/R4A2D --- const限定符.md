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
- ## const的引用
	- 可以把引用绑定到`const`对象上，叫作**对常量的引用**，简称为**常量引用**。与普通引用不同的是不能用它修改它所绑定的对象。
	- ### 初始化和const的引用
		- 引用类型必须与被引用的对象类型相同，但有两个例外，其中一个例外就是`const`引用可以用任意表达式初始化，只要该表达式的类型可以转换成引用的类型，尤其，允许为一个常量引用绑定非常量的对象，字面值，甚至是个一般表达式。
		- #### 发生了什么？
			- 编译器在看到这种情况时，会自动添加一个临时量，将引用绑定到这个临时量上。
			- ```C++
			  double dval = 3.14
			  const int& i = dval;
			  
			  int temp = dval;
			  const int &i = temp;
			  ```
		- #+BEGIN_NOTE
		  必须认识到，常量引用仅对引用克参与的操作做出了限定，对引用的对象本身是不是一个常量未作限定。
		  #+END_NOTE
- ## 指针和const
	- 指针可以指向常量或者非常量。指向常量的指针不能用于改变所指对象的值。存放常量的地址只能使用指向常量的指针。
	- 指针的类型必须与其所指对象的类型一致，但有两个例外。第一个例外就是允许一个指向常量的指针指向一个非常量对象。
	- #+BEGIN_NOTE
	  指向常量的指针最主要的目的就是为了不能通过这个指针改变所指对象。
	  #+END_NOTE
	- ## const指针
		- 指针是对象，所以它也可以被定义为常量。常量指针必须初始化，而且一旦初始化完成，则它的值就不能再改变了。
			- 把`*`放在`const`关键字之前以说明指针是一个常量。
			- ```C++
			  int *const pa = &a;
			  ```
- ## 顶层const
	- 顶层`const`表示指针本身是一个常量，而底层`const`表示指针所指的对象是一个常量。更一般的，顶层`const`表示指针本身是个常量，底层`const`则与指针和引用等复合类型的基本类型部分有关。
	- 当执行对象的拷贝操作时，顶层`const`不受什么影响，底层`const`却会产生限制，拷入和拷出的对象必须具有相同的底层`const`资格，或者两个对象的数据类型必须能够转换。
	- ```C++
	  const int t = 10;
	  const int *pa = &t;
	  
	  int *pb = &a;    // 错误:底层const要求类型一致
	  ```
- ## constexpr和常量表达式
	- **常量表达式**是指值不会改变并且在编译过程中就能得到计算结果的表达式。
		- 一个对象(或表达式)是不是常量表达式由它的数据类型和初始值共同决定。
	- ### constexpr变量
		- 判断一个初始值是不是常量表达式是困难的，可以通过将变量声明为`constexpr`类型以便由编译器验证变量是否是一个常量表达式。
	- ### 字面值类型
		- 因为常量表达式的值在编译时就要得到计算，所以初始化它的值的类型必须有所限制，它们一般比较简单，值也显而易见，所以被称为“字面值类型”。
		- 指针和引用也可以被定义成`constexpr`，但它们的初始值却收到严格的限制。一个`constexpr`指针的初始值必须是==nullptr==或者==0==，或者是==存储于某个固定地址中的对象==。
			- 函数体内定义的变量一般来说并非存放在固定地址中，因此`constexpr`指针不能指向这样的变量。
			- 定义于所有函数体之外的对象其地址固定不变，能用来初始化`constexpr`指针。
	- ### 指针和constexpr
		- 在`constexpr`声明中如果定义了一个指针，限定符`constexpr`仅对指针有效，与指针所指的对象无关。
		-
	-