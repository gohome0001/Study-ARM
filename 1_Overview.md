# Overview

## ARM characteristics

ARM : Advanced RISC Machine

- fixed size opcode

- thumbs mode : supports 16 bit length opcode. have some limits.

- speculative execution

- Java Bytecode를 native처럼 실행하는 모드가 있다고 함.
  - Jazelle DBX(Direct Bytecode eXecution)

귀찮은 점 중 하나는 32bit - AArch32, 64bit - AArch64 이 둘의

차이점이 꽤 있다는 것이야..

## 32bit

- unaligned memory access not allowed.
  - in some versions do support it, but no guarantee with automicity.
- Can directly access to PC(Program Counter) 
- no branch prediector! 
- 2-priority-level interrupt has switched register banks.
- Trustzone 이라는 security extension 존재.
- NX (No eXecution) page protection 지원
  
### Register use & Calling Convention

register use
- r15. PC(Program Counter) : Instruction Pointer
- r14. link register : stores RET
- r13. stack pointer
- r12. intra-procedure-call register : no need to backup & restore its value.
- r4~11. local var
- r0~3. args & return values.

- CPSR(Current Program Status Register)
- more details [here](https://en.wikipedia.org/wiki/ARM_architecture#Registers)

calling convention

- prologue

1. prepare `args` in r0~3
2. bl (branch link)
  - sets `lr`
3. store caller's local var & RET to stack

- epilogue
4. restore data.

## 64bit

- Cryptography instructions added
  - AES, SHA series
- Can't directly access to PC(Program Counter)
- still 32bit len instructions
- and [more](https://en.wikipedia.org/wiki/ARM_architecture#64/32-bit_architecture)
- speculative execution for branch operations

### Register use & Calling Convention

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

## data type

[table of data-type](http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.dui0472m/chr1359125009502.html)

Just remember that `word` in arm is 32bit size.
- halfword : 16bit
- d(double)word : 64bit
