# OOP (CPP)

Mainly C++ stuffs.

Don't ask me 'Is C++ Really OOP?'.

I've seen a lot of haters..

actually, It is not ARM-specialized topic. Applied on other ISA.

Thought I would need to study this part, cause CPP is commonly used.

Plus, Its structure is quite complicated. 

## summary

- instance's member variables are allocated dynamically
- but methods, static variables aren't. already made-up when compiled.
- Little bit complicated with class inheritance.
- check [Itanium C++ ABI](https://itanium-cxx-abi.github.io/cxx-abi/abi.html) for standard spec.
	- for gcc-created code. ( MSVC :negative_squared_cross_mark: )

## Inheritance

1. simple, basic inheritance

In this case, the new inherited class ONLY includes overridden methods

2. Multiple inheritance

In this case, when calling the parent's method (non-overridden method),

It passes the `this` pointer offset with the matched class-layout.

for instnace..
- if class `A` has a two member vars. - a1, a2
- and class `B` has a one member vars. - b1
- and class `C` overrides `A`,`B`

then, the created(allocated) instance would have a memory layout like..
```
| a1 | a2 | b1 |
↑
this
```
and when C calls the unoverriden method from class `B`, C passes the `this` pointer offset like..

```
| a1 | a2 | b1 |
          ↑
         this
```

3. virtual method

A method without virtual, type is binded in compile time.

nice description about virtual methods : [link](https://stackoverflow.com/questions/2391679/why-do-we-need-virtual-functions-in-c)

When a Polynomial-Class is created, RTTI (Run-Time Type Information) is created.

explanation with RTTI : [here](https://www.blackhat.com/presentations/bh-dc-07/Sabanal_Yason/Paper/bh-dc-07-Sabanal_Yason-WP.pdf)

without RTTI, [here](https://alschwalm.com/blog/static/2016/12/17/reversing-c-virtual-functions/)'s a good explanation with gcc.

and vtable for multi-inheritance, [here](https://alschwalm.com/blog/static/2017/01/24/reversing-c-virtual-functions-part-2-2/)

