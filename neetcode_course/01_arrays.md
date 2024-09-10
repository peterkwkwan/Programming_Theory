## Static Arrays

- fixed size
  - cannot increase size/length of the array
- read and write operations for arrays (e.g. `my_array[0]`)
  - time complexity: `O(1)`
  - instant operation, _constant time_
- inserting or removing values in the beginning or middle of array
  - time complexity: `O(n)`
  - `n` is number of elements inside array
  - we need to shift _all_ elements in the array `index +/- 1`

## Dynamic Arrays

- can increase size of array
  - programming languages like python and javascript use dynamic arrays by default
