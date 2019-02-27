# tricks for optimization

actually, this 'tricks' are used in general.

1. division to multiplication

https://research.swtch.com/divmult

for example, when dividing to 9,

compiler generates code like this

```C
// want to perform a = a/9

a = a * 2^33 / 9
a = a >> 33
```
like this, so there are specific magic number for each div-number.

2. multiplication trick

using `mul` instruction, 
```
// little bit akward using x86...
// want eax * 5

lea ecx, dword ptr [eax,eax*4]
```
wow!

3. inline functions

in past, inline function needed `inline` keyword.

however, in these days, inline functions are chosen by compiler.

usually once-used function..

it's more cheap for once-used functions.
