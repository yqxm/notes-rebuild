- #+BEGIN_PINNED
  Bryant, Randal E., and David R. O’Hallaron. 深入理解计算机系统. Translated by 龚奕利 and 贺莲. Third Edition. Beijing: 机械工业出版社, 2016.p31
  #+END_PINNED
- ```C
  #include <stdio.h>
  
  typedef unsigned char * byte_pointer;
  
  void show_bytes(byte_pointer bp, size_t sz) {
    for (size_t i = 0; i < sz; i++) {
      printf(" %.2x", bp[i]);
    }
    printf("\n");
  }
  
  // 查看int的排列
  void show_int(int k) {
    show_bytes( (byte_pointer)&k, sizeof(int) );
  }
  
  // 查看float的排列
  void show_float(float f) {
    show_bytes( (byte_pointer)&f, sizeof(float) );
  }
  ```
- [[RE1A1A3A --- 练习 2-5]]
- [[RE1A1A3B --- 练习 2-6]]
-