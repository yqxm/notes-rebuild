- #+BEGIN_PINNED
  Lippman, S. B., Lajoie, J., & Moo, B. E. (2013). C++ Primer 中文版 (王刚 & 杨巨峰, Trans.; 5th ed.). 电子工业出版社.p400
  #+END_PINNED
- ## `new`和`delete`
	- `new`: 为对象分配空间并返回指针。
	- `delete`: 销毁对象，删除为对象分配的空间。
	- *常常出现的问题*:
		- 常常忘了释放内存造成内存泄漏
		- 在还有指针指向内存的时候就释放了它。
- ## 智能指针
	- C++提供了两种智能指针来管理指针，和普通指针的区别是它们会自动释放所指向的对象。它们本身的区别的区别主要是管理内存的方式。
		- `shared_ptr`允许多个指针指向同一个对象。
			- 伴随类`weak_ptr`，指向`shared_ptr`所管理的对象。
		- `unique_ptr`独占所指向的对象。
-
- [[R4A12A1 --- shared_ptr类]]
-