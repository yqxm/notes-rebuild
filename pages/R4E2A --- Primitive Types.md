- #+BEGIN_PINNED
  Rothwell, T., & Youngman, J. (2016). The GNU C Reference Manual (0.2.5). Free Software Foundation, Inc. c2.1
  #+END_PINNED
- ==关键词==: Integer Types、Real Number Types、Complex Number Types
-
- **Integer Types**
	- 注意下面的范围是标准要求的要达到的最小范围，实际由机器决定，范围可能更大一些。
	- `signed char`: -128~127，8-bits。
	- `unsigned char`: 0~255, 8-bit。
	- `char`: `char`的类型有机器决定，它的范围或者和`signed char`一样，或者和`unsigned char`一样
	- `short int`: -32768~32767，16-bit。
	- `unsigned short int`: 0~65535, 16-bit。
	- `int`: -2147483648~2147483647, 32-bit。
	- `unsigned int`: 0~4294967295, 32-bit。
	- `long int`: -2147483648~2147483647, 32-bit。实际情况可能是64-bit，具体由机器决定。
	- `unsigned long int`: 0~4294967295, 32-bit。实际情况可能是64-bit，具体由机器决定。
	- `long long int`: -9,223,372,036,854,775,808 ~ 9,223,372,036,854,775,807, 64-bit。这个类型不在C89标准里，但是C99和GNU扩展的一部分。
	- `unsigned long long int`: 0 ~ 18,446,744,073,709,551,615, 64-bit。个类型不在C89标准里，但是C99和GNU扩展的一部分。
- **Real Number Types**
	- 由于历史原因，实数类型在不同的机器上有不同的范围，所以使用宏来规定指代具体范围。这些宏存储在`float.h`中。
	- `float`: 它的最小值存储在`FLT_MIN`，它不应该大于1e-37。它的最大值存储于`FLT_MAX`，它不应该小于1e37。
	- `double`: `double`的范围至少要和`float`一样，它的最小值存储于`DBL_MIN`，最大值存储于`DBL_MAX`。
	- `long double`: `long double`的范围至少和`float`一样，它的最小值存储于`LDBL_MIN`，最大值存储于`LDBL_MAX`
	- #+BEGIN_NOTE
	  C中的实数类型精度有限，不是所有的实数都可以准确表示，比如4.2。所以最好不要进行实数的比较，除非在一个可接受的tolerence下。
	  #+END_NOTE
- **Complex Number Types**
	- gcc引进了一些对C89的复数扩展，和C99中的有些类似，但也有很多不同。
	- **Standard Complex Number Types**
		- C99中的复数类型:
			- `float _Complex`
			- `double _Complex`
			- `long double _Complex`
		- C99中的`complex.h`引入了一些宏来让上面的类型更易于使用:
			- `complex`
				- `_Complex`的替代，使用起来更自然，比如`double complex`
			- `I`
				- 代表虚数$i$
		- `complex.h`中同样定义了一些方便使用的函数，比如`creal()`获取实部，`cimg()`获取虚部。
		- 例子
			- ```C
			  #include <complex.h>    
			  #include <stdio.h>  
			  
			  void example (void) 
			  {    
			    complex double z = 1.0 + 3.0*I; 
			    printf ("Phase is %f, modulus is %f\n", carg(z), cabs(z));        
			  } 
			  ```
	- **GNU Extensions for Complex Number Types**
		- GCC C89扩展中的复数类型:
			- `__complex__ float`
			- `__complex__ double`
			- `__complex__ long double`
		- GCC扩展除了支持复数浮点数还有其他类型的复数类型，所以可以声明复数的字符类型和复数的整数类型。
			- `__complex__ float`
				- 这个类型包含实部和虚部，都是`float`类型
			- `__complex__ int`
				- 这个类型包含实部和虚部，都是`int`类型
		- 可以使用关键字`__real__`和`__imag__`来获取复数的实部和虚部。
			- ```C
			  __complex__ float a = 4 + 3i;
			  float b = __real__ a;		// a 等于 4
			  float c = __imag__ a;		// c 等于 3
			  ```
-