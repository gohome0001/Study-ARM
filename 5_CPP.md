# CPP
 
why cpp again? you did this at 4_OOP.md!

well, I thought oop could be adopted in other native-oop languages (if there exists..)

And the content for this post has a distance with OOP.

## iostream

how `<<` operator works internally as a function.
```
std::cout << "Hello, " << "World!\n";
```

It works like this
```cpp
// say << is f()
f(f(std::cout, "Hello. "), "World!\n");
```

## References

Reference variables in cpp is like
```cpp
void f(int x, int y, int & sum)
{
  sum = x + y;
}
```
`&` is use after var type.

Well, there are some rules that reference var. has to keep.

but, in implementation code, there aren't much special code seen.

## STL

1. std::string

there aren't such "Standards" how to implement std::string,

but usually implemented as
- pointer to the buffer containing string
- variable containing current string length
- variable containing current buffer size

for MSVC, string that its length is shorter than 16-byte, is not allocated in heap.

NOTE : you have to manually null-terminate the strings, or use supportive methods

for GCC, string object has one more variable : reference count

unlike MSVC, pointer to string object is not the beginning of the structure,

it is pointer to the buffer. 
- for easy debugging








