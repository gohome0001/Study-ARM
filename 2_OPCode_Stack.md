# Opcode

Just see this doc.

http://infocenter.arm.com/help/index.jsp?topic=/com.arm.doc.dui0068b/CIHEDHIF.html

for more detailed information about each opcode, search for it from the given url.

# code patterns

There are some code patterns that might help.

## how it uses stack

### exclamation mark(point?) : `!`

it means, value will be modified after the instruction executes.
- the base pointer will be modified

It is used like this
```
STMFD lr! {r11,r12,lr,pc}
```
means, LR's value will be pointing where the pc's value is stored in stack 
lr -= wordsize*4

```
str lr,[sp,#-18]!
```
means, `sp -= 18`

### how sp(stack pointer) inc/dec

when store/load ing multiple values,

`STMIA` : store and increase after
- *(p++)

`STMIB` : increase before
- *(++p)

`STMDA` : decrease after

`STMDB` : decrease before

used for multiple value store

when loading change `ST` to `LD`

### function prologue

1. passing the arguments 
- use the registers.
- but, when its num is more than the register num
  - 부족한 만큼의 args만 스택에 넣은 후 나머지는 기존 register에 넣어서 call.
2. storing the caller's data
- just push(STR) into the stack!

### function epilogue

1. restore the caller's data
- just pop(LD) from the stack!
2. return to orginal flow.
- branch (b, bx) to `lr`
