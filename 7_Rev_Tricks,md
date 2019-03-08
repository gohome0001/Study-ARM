# some tricks that would be helpful for analysis

1. Strings

2. constants
- crc-precomputed tables (crc32, ..)

search on internet and get to know if it is open-algorithm

3. magic numbers
- same as constants.
- comparing to such numbers
  - can think it is an file-type check or something
  - can get more clues.
  
4. suspicious code patterns
- xor
  - mostly used for initializing register value to zero
  - and stack canary check
  - but if not, could be some cryptographic routine.
- hand_written asm code
  - there are some code patterns that compilers don't use.
  
5. memory snapshot comparing
- ex) cheetengine
