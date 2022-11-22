- #+BEGIN_PINNED
  Rothwell, T., & Youngman, J. (2016). The GNU C Reference Manual (0.2.5). Free Software Foundation, Inc. c1.2
  #+END_PINNED
- **关键词**
	- 关键词是编程语言的一部分，不能以另外的方式使用。
- **C89关键词**
	- ```C
	  auto break case char const continue default do double else 
	  enum extern float for goto if int long register return 
	  short signed sizeof static struct switch typedef union 
	  unsigned void volatile while
	  ```
- **C99增加的关键词**
	- ```C
	  inline _Bool _Complex _Imaginary
	  ```
- **GNU扩展的关键词**
	- ```C
	  __FUNCTION__ __PRETTY_FUNCTION__ __alignof __alignof__ __asm
	  __asm__ __attribute __attribute__ __builtin_offsetof 
	  __builtin_va_arg __complex __complex__ __const __extension__ 
	  __func__ __imag __imag__ __inline __inline__ __label__ 
	  __null __real __real__ __restrict __restrict__ __signed 
	  __signed__ __thread __typeof __volatile __volatile__
	  ```
- 包含了GNU扩展的ISO C89和ISO C99都会将`restrict`视为关键词
-