
Seeding NumPy random number 

## Numpy Arrays
```python
import numpy as np

# Instantiating
ar = np.array([[1,2,3],[4,5,6],[7,8,9]])
ar = np.zeros((2, 2))
ar = np.ones((2, 2), dtype=int)

# Accessing Elements
ar[1, 3]      # Not a[1][3]. Can assign to as well.
ar[1:3,2:8]   # Slicing
ar[1] = 23
ar[1:3,2:4] = [ ['a', 'b'], ['c', 'd'] ]

# Shape
ar.shape                    # Tuple of dimensions e.g. (2, 3, 4)
np.reshape(ar, (2, 4, 3))   # Must have same num of elements

# Transposition - Flips array along diagonal
ar.T

# Vectorization; perform operation on each element
ar + 2
ar * 10
ar ** 2
np.abs(ar)
np.sqrt(ar)

# Methods
np.random.seed(x)  # Seed PRNG with value x
rand_array = np.random.rand(2, 3)   # Array of shape (2, 3), vals 0-1
np.random.normal(loc, scale, size)  # From normal distribution
np.random.poisson(lam, size)
np.random.randint(low, high, size, dtype)
np.random.choice(ar, size, replace, p) # Random choices from 1D array a
np.random.shuffle(ar)   # Shuffle in place


```

NumPy Arrays all have same datatype, in multiple dimensions all rows have the same length.

----
# Sources
[NumPy Reference — NumPy v1.23 Manual](https://numpy.org/doc/stable/reference/index.html#reference)
[[The Statistics and Calculus with Python Workshop]]



