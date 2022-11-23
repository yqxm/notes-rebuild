- #+BEGIN_PINNED
  Carter, P. A. (2003). PC Assembly Language. Self-published. p11 c1.3
  #+END_PINNED
- **机器语言**
	- 每条指令都有它的唯一编码，叫作*opcode*。
	- 机器代码很难读，所以有了汇编语言和assembler。
- **汇编语言**
	- 不同的指令集使用不同的汇编语言，不同的汇编器还有它自己的方言。
- **指令操作数**
	- 机器指令有不同数量不同类型的操作数，但操作数的数量是固定的(0 ~ 3个)。操作数的类型有以下几种:
	- *register*
		- 这些操作数直接查取寄存器中的内容
	- *memory*
		- 这些操作数查取内存中的数据。数据的地址可能是常数硬编码进指令或者由寄存器的值计算而来。地址是segment距离起始处的偏移量。
	- *immediate*
		- 指令中的固定值，存储在指令中。
	- *implied*
		- 操作数没有显式的写出来。
- **Directives**
	- 汇编器指令用来指示汇编器的工作或者给汇编器提供信息。它们不会被翻译成机器码。它们通常用来:
		- 定义常量
		- 定义数据要存入的内存
		- 将内存打包放入segments
		- 包含(include)源码
		- 包含(include)其他文件
	- NASM使用`%`来进行包含(include)
	- **The equ directive**
		- `equ`可以用来定义*symbol*。`symbol equ value`。*symbol*的值之后不能重新定义。
	- **The %define directive**
		- `%define`和C中的`#define`，有点类似，常被用来定义常量宏。
	- **Data directives**
		- 数据汇编指令用来在数据段定义内存空间。有两种方式来保留内存。第一种方式只定义空间，第二种方式定义空间和初始值。
			- `RESX`，`X`指要被存储的对象的大小。使用时替换成`b w d q t`
			- `DX`，`X`也是指被存储的对象的大小。
		- **标签**
			- 使用标签标记内存地址是非常普遍的。
			- ```asm
			  L1		db		0						; byte labled L1 with initial value 0 
			  L2		dw		1000					; word labled L1 with initial value 1000
			  L3		db		110101b					;
			  L4		db		12h						; byte initialized to hex 12 (18 in decimal)
			  L5		db		17o						;
			  L6		dd		1A92h					; double word initialized to hex 1A92
			  L7		resb	1						; 1 uninitialized byte
			  L8		db		"A"						; byte initialized to ASCII code for A (65)
			  L9		db		0, 1, 2, 3				; defines 4 bytes
			  L10		db		"w", "o", "r", 'd', 0 	; defines a C string = "word"
			  L11 	db		'word', 0				; same as L10
			  L12		times	100	db 0				; equivalent to 100 (db 0)'s
			  L13		resw	100						; reserve room for 100 words
			  ```
				- 不区分单引号和双引号。
				- 连续的数据定义在内存中也是按顺序存储的。即，L2紧跟在L1之后。
				- `times`将指令重复，如`L12`。
			- 可以将标签当作指针，使用`[]`来将它解引用。
				- ```asm
				  mov		al, [L1]	; copy byte at L1 into AL
				  mov 	eax, L1		; EAX = address of byte at L1
				  mov		al,	[L6]	; copy first byte of double word at L6 in AL
				  ```
				- NASM不会跟踪标签的数据类型，所以是由程序员决定自己是否正确的使用标签。
			- 可以使用size specifier来指定操作的数据的大小。`BYTE WORD QWORD TWORD`
				- ```asm
				  mov		dword [L6], 1		; store a 1 at L6
				  ```
-