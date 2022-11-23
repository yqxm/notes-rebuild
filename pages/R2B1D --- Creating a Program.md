- #+BEGIN_PINNED
  Carter, P. A. (2003). PC Assembly Language. Self-published. p18 c1.4
  #+END_PINNED
- ```asm
  
  %include "asm_io.inc"
  
  ; 初始化后的数据放入 .data区域
  segment .data
  
  prompt1 db "Enter a number: ", 0
  prompt2 db "Enter another number: ", 0
  outmsg1 db "You entered ", 0
  outmsg2 db " and ", 0
  outmsg3 db ", the sum of these is ", 0
  
  ; 未被初始化的数据放入 .bss区域
  segment .bss
  
  input1 resd 1
  input2 resd 2
  
  segment .text
          global asm_main
  asm_main:
          enter   0,0
          pusha
  
          mov     eax, prompt1
          call    print_string
  
          call    read_int
          mov     [input1], eax
  
          mov     eax, prompt2
          call    print_string
  
          call    read_int
          mov     [input2], eax
  
          mov     eax, [input1]
          add     eax, [input2]
          mov     ebx, eax
          dump_regs 1
          dump_mem 2, outmsg1, 1
  
          mov     eax, outmsg1
          call    print_string
          mov     eax, [input1]
          call    print_int
          mov     eax, outmsg2
          call    print_string
          mov     eax, [input2]
          call    print_int
          mov     eax, outmsg3
          call    print_string
          mov     eax, ebx
          call    print_int
          call    print_nl
  
          popa
          mov     eax, 0
          leave
          ret
  ```
- `global`告诉汇编器让`asm_main`标签变成全局的。这样它就可以调用`asm_io`中的`print_int`。
-
-