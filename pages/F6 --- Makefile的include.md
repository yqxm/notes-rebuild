- 在`Makefile`里的`include`和C中的`include`规则一样，它只负责包含，所以要注意相对路径。
- 以下面的结构为例:
	- ```text
	  asm
	  ├── rules.mk
	  ├── commons.mk
	  ├── add
	      ├── Makefile
	      ├── test.s
	  ```
	- `rules.mk`
		- ```make
		  include ./commons.mk	
		  ...
		  ```
	- `add/Makefile`
		- ```make
		  include ../rules.mk
		  ...
		  ```
	- #+BEGIN_WARNING
	  `add`下的`Makefile`会找不到`commons.mk`
	  #+END_WARNING
-