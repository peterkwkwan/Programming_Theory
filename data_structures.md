# ARRAYS

### RAM (Random Access Memory)
- ram stores data in bytes
    - a byte is 8 bits
    - each bit can store a zero (0) or one (1)
  
- two components to RAM
  - VALUE and ADDRESS
    
- How can we store arrays in memory?
  - each element in array is stored as a series of bits
  - elements in an array are always contiguous, meaning they are adjacent to each other

![image](https://github.com/peterkwkwan/Programming_Theory/assets/37263010/4496d295-a418-4b05-b822-7b5ab3670419)

### Static Arrays

- How can we read the first element of the array?
    - `myArray[0]`
    - this operation is `O(1)` - _constant time_
 
- Static arrays are fixed size
- Cannot increment size because RAM may have allocated other data in the `arr.length + 1` spot
