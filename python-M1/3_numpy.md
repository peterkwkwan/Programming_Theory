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
