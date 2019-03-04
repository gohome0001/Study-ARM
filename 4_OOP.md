# OOP

Mainly C++ stuffs.

Don't ask me 'Is C++ Really OOP?'.

I've seen a lot of haters..

actually, It is not ARM-specialized topic. same thing for other arch.

## summary

- instance's member variables are allocated dynamically
- but methods, static variables 
- complicated things happen with class inheritance.

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
