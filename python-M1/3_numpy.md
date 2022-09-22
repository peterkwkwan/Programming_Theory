# Numpy

- Popular Python library that deals with numbers
- A.K.A Numberical Python
- Uses a special data type called `Numpy Arrays`
- Arrays:
  - a collection of items of the same type
  - different from `lists` - lists store different data types

#### Why use it?

- Many built-in functions and capabilities array/number manipulation
- Import aspects of Numpy
  - arrays
  - vectors
  - matrices
  - number generation

#### Installation & use
```
pip install numpy

-----

import numpy as np

```
#### Numpy arrays

- Numpy arrays come in 2 flavors: vectors & matrices
- Vectors: 1-d arrays (`N-dimensional array`)
- Matrices: 2-d arrays

#### N-dimensional array
- One way to create an array is using the `arange` method (arrange + range)

```
np.arange(8) // array([0, 1, 2, 3, 4, 5, 6, 7])

type(type(np.arange(8)) // numpy.ndarray
```
- `8` is the _stop value_
- we can also specify a _start value_

```
np.arange(1, 8) // array([1, 2, 3, 4, 5, 6, 7])
```

- how about only include the odd values?
- we can include a _step_

```
np.arange(1, 8, 2) // array([1, 3, 5, 7])
```

- we can also use decimals/fractional numbers

```
np.arange(1,8,0.5) // array([1. , 1.5, 2. , 2.5, 3. , 3.5, 4. , 4.5, 5. , 5.5, 6. , 6.5, 7. ,7.5])
```

- negative values also work!

```
np.arange(-1, 8.5, 0.5) // array([-1. , -0.5,  0. ,  0.5,  1. ,  1.5,  2. ,  2.5,  3. ,  3.5,  4. ,4.5,  5. ,  5.5,  6. ,  6.5,  7. ,  7.5,  8. ])
```

#### Generate from a list
- We can also create arrays using lists

```
from_list = np.array([1,2,3])
print(from_list)
```

- why would we want to change from list to array? Whats the point? Aren't they similar?
- main purpose is _memory efficiency_
- `lists` can store any type of data (dict, boolean, str, etc.)
  - this flexiblilty has a downside, it takes up a lot more space/memory
  - _str_ for example, can be 26 lowercase, 26 uppercase, symbols, digits, etc. And this is just for 1 character!
  - _boolean_ on the other hand, can only be 2 values - true or false
- let's check the memory usage of our list

```
from_list = np.array([1,2,3])
type(from_list[0]) // numpy.int64
```
- do we really need 64 bits to convey _1,2,3_?
- Decimal to binrary (https://www.rapidtables.com/convert/number/decimal-to-binary.html)

Decimal | Binary 
--- | --- 
1 | 1
2 | 10
3 | 11

- our biggest number `3` only takes 2 bits! We don't need 64 bits!
- we can convert the data type from int64 to something more memory efficient

```
from_list = np.array([1,2,3], dtype=np.int8)
type(from_list[0]) // numpy.int8
```
- however, just because our code takes up less space, it doesn't mean it will run faster!
- depends on your hardware, algorithms, operating system!


#### 2-dimensional array

```
from_list_2d = np.array([[1,2,3],[4,5,6]], dtype=np.int8)
print(from_list_2d)
```

- this is a 2-D array because we are dealing with multiple rows of data

```
array_2d = np.array((np.arange(0,8,2),np.arange(1,8,2)))
print(array_2d)

// [[0 2 4 6]
//  [1 3 5 7]]
```

- we can verify it is a 2-D array by printing its `shape`

```
print("1D shape: ", from_list.shape)
print("2D shape: ", array_2d.shape) 

// 1D shape:  (3,)
// 2D shape:  (2, 4)

```
