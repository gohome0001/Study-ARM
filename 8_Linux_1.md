# Linux specifics

## Position-independent code (PIC)

This was used for obsolete computers, that didn't had MMU (Memory Management Unit).

As every processed used one memory space, they needed to locate codes & global variables to preserved space 
- hardcoded offset from base 

Nowdays, it is used for embedded devices, and *NIX system's shared library
- typically, embedded devices has no MMU
- in *NIX systems, shared library is loaded once in the memory
  - but each processes can map it diffrently, so it is used.

It's about PLT and GOT, so if you're familar with pwning.. you'll already know it!

and this was it!
