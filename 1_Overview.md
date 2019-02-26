# Overview

## ARM characteristics

ARM : Advanced RISC Machine

- fixed size opcode

- thumbs mode : supports 16 bit length opcode. have some limits.

귀찮은 점 중 하나는 32bit - AArch32, 64bit - AArch64 이 둘의

차이점이 꽤 있다는 것이야..

## Register use & Calling Convention

### 32bit
register use
- r15. PC(Program Counter) : Instruction Pointer
- r14. link register : stores RET
- r13. stack pointer
- r12. intra-procedure-call register : no need to backup & restore its value.
- r4~11. local var
- r0~3. args & return values.

calling convention

- prologue

1. prepare `args` in r0~3
2. bl (branch link)
3. store caller's local var & RET to stack

- epilogue
4. restore data.

### 64bit

register use
- x31. Stack Pointer or zero pointer
- x30. link register
- x29. frame register
- x19~29. callee has to save it!
- x18. platform register : used for OS specific purpose.
- x9~15. local var
- x8. indirect return value addr
- x0~7. args & retrun val.

x0~31 : 64bit size

x가 아니라 w를 prefix로 붙이면 하위32bit register로써 접근 가능. 
