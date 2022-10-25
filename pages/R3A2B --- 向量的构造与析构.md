- #+BEGIN_PINNED
  邓俊辉. (2013). 数据结构: C++语言版 (3rd ed.). 清华大学出版社.p32-33
  #+END_PINNED
- 在实现中向量元素存放在`_elem[]`中，`_capacity`指示它的容量，`_size`指示已经有效元素的数量。向量中秩`r`的元素和`_elem`的关系是:
	- ==向量的第r个元素对应`_elem[r]`，它的地址位于`_elem+r`==
- 向量的构造和析造将围绕这些私有变量和数据区的初始化和销毁展开。
- ## 默认构造方法
	- ```C++
	  Vector(int c = DEFAULT_CAPACITY, Rank s = 0, T v = 0) { 
	    _elem = new T[_capacity = c]; 
	    for (_size = 0; _size < s; _size++) { 
	      _elem[_size] = v; 
	    }
	  }
	  ```
	- 根据`c`初始化`_elem`数组，将秩为`s`以下的元素设置为`v`。同时更新`_size`。
	- ==默认情况下==，`s`和`v`都为0，`c`为`DEFAULT_CAPACITY`。即设置`_elem`为默认容量，整个向量为空。
- ## 基于复制的构造方法
	- ### copyFrom
		- 这些基于复制的构造方法都使用了`copyFrom`函数。函数中将`_capacity`设置为元素个数的两倍。
		- ```C++
		  template <typename T>
		  void Vector<T>::copyFrom(T const* A, Rank lo, Rank hi) {
		      _elem = new T[ _capacity = (hi-lo)*2];
		      _size = 0;
		      while (lo < hi) {
		          _elem[_size++] = A[lo++];
		      }
		  }
		  ```
	- ### 重载赋值运算符
		- 因为向量包含动态内存的使用，默认的赋值运算符无法提供相关的功能。所以需要对赋值运算进行重载
		- ```C++
		  template <typename T>
		  Vector<T> &Vector<T>::operator=(const Vector<T> &toa) {
		    if (this == &toa) return *this; //  处理 self-assignment
		    delete [] _elem;
		    copyFrom(toa, 0, toa.size());
		    return *this;
		  }
		  ```
- ## 析构方法
	- 向量的析构主要是针对动态申请的`_elem`数组。基于`谁申请谁释放`的原则，这里不考虑向量中的元素申请了是动态内存的。
	- ```C++
	  ~Vector() { delete [] _elem;}
	  ```
-
-