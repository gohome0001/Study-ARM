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

### 1. std::string

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

So, the metadata for the string object's position is like
```C
struct std_string{
	size-t length;
	size-t capacity;
	size-t refcount;
}

// std::string 's metadata is located in 
// (object's address - sizeof(struct std_string))
```

If you find `std::string` in real code, there will be a lot of cmp instruction with immediate 16,

Which is the string size is compared, and it determines which const/deconstructor to call.
- 'cause string length >= 16, is allocated to heap!

Then, What will happen global variable with std::string type?

It won't be much different. you would see some const/deconstructor.

But, It would be called by CRT (C Runtime Library) before main.

And there's something that I first heard of, `atexit()`. I should learn more about this. 

*TODO : detailed description about atexit()*

seem like gcc just uses `atexit()` and MSVC does more with it.

### 2. std::list

TODO : rest of it..
