- #+BEGIN_PINNED
  邓俊辉. (2013). 数据结构: C++语言版 (3rd ed.). 清华大学出版社.p30-31
  #+END_PINNED
- ```C++
  #ifndef ALGO_VECTOR_HPP
  #define ALGO_VECTOR_HPP
  
  using Rank = int;
  #define DEFAULT_CAPACITY 3
  
  template<typename T>
  class Vector {
  protected:
      Rank _size;
      Rank _capacity;
      T *_elem;
      void expand();
      void shrink();
      bool bubble(Rank lo, Rank hi); //扫描交换
      void bubbleSort(Rank lo, Rank hi); // 冒泡排序
      Rank maxItem(Rank lo, Rank hi);
      void selectionSort(Rank lo, Rank hi);
      void merge(Rank lo, Rank mid, Rank hi);
      void mergeSort(Rank lo, Rank hi);
      void heapSort(Rank lo, Rank hi);
      Rank partition(Rank lo, Rank hi);
      void quickSort(Rank lo, Rank hi);
      void shellSort(Rank lo, Rank hi);
  
  public:
      Vector(int c = DEFAULT_CAPACITY, Rank s = 0, T v = 0)
      { _elem = new T[_capacity = c]; for (_size = 0; _size < s; _size++) { _elem[_size] = v; }}
  
      Vector(T const* A, Rank n) { copyFrom(A, 0, n);}
      Vector(T const* A,Rank lo, Rank hi) { copyFrom(A, lo, hi);}
      Vector(Vector<T> const& V) { copyFrom(V._elem, 0, V._size);}
      Vector(Vector<T> const& V, Rank lo, Rank hi) { copyFrom(V._elem, lo, hi);}
  
      ~Vector() { delete [] _elem; };
  
      // 只读接口
      Rank size() const { return _size;}
      bool empty() const { return _size == 0; }
      Rank find (T const& e) const { return find(e , 0, size());}
      Rank find (T const& e, Rank lo, Rank hi) const;
      Rank search (T const& e) const
      { return (0 >= _size)? -1 : search(e, 0, size());}
      Rank search (T const& e, Rank lo, Rank hi) const;
  
      //可写接口
      T& operator[] (Rank r);
      const T& operator[] (Rank r) const;
      Vector<T> & operator= ( Vector<T> const&);
      T remove (Rank r);
      int remove (Rank lo, Rank hi);
      Rank insert (Rank r, T const& e);
      Rank insert (T const& e) { return insert(_size, e);}
      void sort ( Rank lo, Rank hi);
      void sort () { sort(0, _size);}
      void unsort ( Rank lo, Rank hi);
      void unsort () { unsort(0, _size);}
      Rank deduplicate();
      Rank uniquify();
  
      //遍历
      void traverse ( void (*) ( T&));
      template<typename VST> void traverse( VST&);
  };
  
  #endif //ALGO_VECTOR_HPP
  
  ```