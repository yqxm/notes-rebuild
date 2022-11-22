- #+BEGIN_PINNED
  Rothwell, T., & Youngman, J. (2016). The GNU C Reference Manual (0.2.5). Free Software Foundation, Inc. c1.6
  #+END_PINNED
- 空白符包含几个字符: 空格、tab、换行、vertical tab、form-feed。空白符常常会被忽略，所以它是可选的，尤其是当它用来分隔token的时候。
- 操作数和运算符之间不需要空白，其他分隔符和它们所分隔的东西之间也不需要空白。
	- ```C
	  /* All of these are valid. */
	  x++;
	  x ++ ;
	  x=y+z;
	  x = y + z ;
	  x=array[2];
	  x = array [ 2 ] ;
	  fraction=numerator / *denominator_ptr;
	  fraction = numerator / * denominator_ptr ;
	  ```
- 如果一个地方空白符是可以存在的，那么这个地方就可以放置任意个空白符。
	- ```C
	  /* These two statements are functionally identical. */
	  x++;
	  - x
	       ++       ;
	  ```
	-