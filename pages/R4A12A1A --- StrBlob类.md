- #+BEGIN_PINNED
  Lippman, S. B., Lajoie, J., & Moo, B. E. (2013). C++ Primer 中文版 (王刚 & 杨巨峰, Trans.; 5th ed.). 电子工业出版社.p404-406
  #+END_PINNED
- `StrBlob`类的每一个对象都共享同一个`vector`，所以使用`shared_ptr`来创建共享数据。
- ## 定义StrBlob
	- ```C++
	  class StrBlob {
	  public:
	      typedef vector<string>::size_type size_type;
	      StrBlob();
	      StrBlob(std::initializer_list<string> il);
	      size_type size() const {return data->size();}
	      bool empty() const { return data->empty();}
	      void push_back(const string &t) { data->push_back(t);}
	      void pop_back();
	  
	      string &front();
	      string &front() const;
	      string &back();
	      string &back() const;
	  private:
	      std::shared_ptr<vector<string >> data;
	      void check(size_type i, const string &msg) const;
	  };
	  ```
- ## 构造函数
	- ```C++
	  StrBlob::StrBlob():data(std::make_shared<vector<string>>()) {}
	  StrBlob::StrBlob(std::initializer_list<string> il) {
	      data = std::make_shared<vector<string>>(il);
	  }
	  ```
	- `data`使用`make_shared()`函数初始化
- ## 元素访问函数
	- ```C++
	  // 检查访问的索引是否越界
	  void StrBlob::check(StrBlob::size_type i, const string &msg) const {
	      if (data->size() <= i) {
	          throw std::out_of_range(msg);
	      }
	  }
	  
	  std::string &StrBlob::front() {
	      check(0, "Front not exist.");
	      return data->front();
	  }
	  
	  std::string &StrBlob::back() {
	      check(0, "Back not exist.");
	      return data->back();
	  }
	  
	  void StrBlob::pop_back()  {
	      check(0, "StrBlob is empty");
	      data->pop_back();
	  }
	  ```
- ## StrBlob的拷贝、赋值和销毁
	- 它使用默认的拷贝、赋值和销毁策略，所以唯一的数据成员`shared_ptr`类型的`data`也会被拷贝、赋值和销毁。当所有的`StrBlob`对象都销毁的时候，这个数据成员指向的内存也会被释放。
-