## Static Arrays

- fixed size
  - cannot increase size/length of the array
- read and write operations for arrays (e.g. `my_array[0]`)
  - time complexity: `O(1)` / _Constant Time_
  - instant Operation, _constant time_
- inserting or removing values in the beginning or middle of array
  - time complexity: `O(n)`
  - `n` is number of elements inside array
  - we need to shift _all_ elements in the array `index +/- 1`

## Dynamic Arrays

- can increase/decrease size of array
  - programming languages like python and javascript use dynamic arrays by default
- creating a new array when space runs out
  - find a new place in memory and double the size of the original array
  - creating a new array is `O(n)` since we need to move all the elements of array to new array location
- _amoritized time complexity_
  - the average time of pushing a new value to end of dynamic array is _usually_ `O(1)`, not `O(n)`, since we usually don't need to create a new array
  - a way to find a middle ground for creating a new array and not having to create it everytime we need more size
  - explained by mathematical _power series_ theory

## Stack

- Push, Pop, and Peek / Top (read last element)
  - time complexity: `O(1)`
- a dynamic array fulfills all these operations
- a pointer that indicates the end position of the stack
- LIFO
  - Last-In First-Out
