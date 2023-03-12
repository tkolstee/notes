
```toc
```

```python
import numpy as np
```


## Constructing
Can be constructed by passing a list of initial values. 
```python
>>> a = np.array([1, 2, 3])
>>> a
array([1, 2, 3])
>>> a[1]
2
```

### Data Types
Values must be of same type.
NumPy will forciby convert all elements into the same type.
```python
>>> b = np.array([1, 2, 'a'])
>>> b
array(['1', '2', 'a'], dtype='<U21')
```
*(U21 is unicode strings with fewer than 21 chars)*

### Multi-Dimensional Arrays
```python
>>> c = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
>>> c
array([[1, 2, 3],
	   [4, 5, 6],
	   [7, 8, 9]])
>>> # elements are accessed by using commas
>>> c[1, 1]   # NOT c[1][1]
5
>>> # Slicing works similarly
>>> a[1, 0:2, 1:]
```

### Automatically Filling Arrays
```python
>>> zero_array = np.zeros((2, 2))  # Shape as tuple
>>> zero_array
array([[0., 0.],
	   [0., 0.]])
>>> one_array = np.ones((2, 2, 3), dtype=int)  # Shape as tuple
>>> one_array
array([[[1, 1, 1],
	    [1, 1, 1]],
	    [[1, 1, 1],
	    [1, 1, 1]]])
```

## Reshaping Arrays
```python
>>> a.shape
(2, 3, 4)
>>> b = np.reshape(a, (3, 2, 4))  # Passes a copy
>>> b.shape
(3, 2, 4)
```

### Transposing

Flips array along diagonal. Returns a copy.
```python
>>> import numpy as np
>>> x = np.array([[1, 2, 3], [4, 5, 6], [7, 8, 9]])
>>> x
array([[1, 2, 3],
       [4, 5, 6],
       [7, 8, 9]])
>>> x.T
array([[1, 4, 7],
       [2, 5, 8],
       [3, 6, 9]])
```

## Vectorization
Performing the same operation against each element in the array separately (e.g. scalar multiplication, adding a scalar to each element).

Faster than an equivalent `for` loop by a large factor.
```python
my_array * 2   # equiv: [ x*2 for x in my_array ]
my_array + 1   # equiv: [ x+1 for x in my_array ]
np.sqrt(my_array) # equiv: list(map(math.sqrt, my_array))
```


## Generating a Random Sample

```python
>>> rand_array = np.random.rand(2, 3)  # Shape as args
>>> rand_array
array([[0.90581261, 0.88732623, 0.291661 ],
	   [0.44705149, 0.25966191, 0.73547706]])
```

| Function              | Meaning                            |
| --------------------- | ---------------------------------- |
| `np.random.normal`    | Sample from normal distribution    |
| `np.random.poisson`   | Sample from poisson distribution   |
| `np.random.randint`   | Random integer between two numbers |
| `np.random.choice()`  | Random item from 1D array          |
| `np.random.shuffle()` | Shuffles a 1D array in place       |

### Seeding
Seeding with the same value will produce the same random numbers with each program run:
```python
import random
random.seed(0)

import numpy as np
np.random.seed(0)
```

