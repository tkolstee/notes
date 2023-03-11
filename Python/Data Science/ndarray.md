Short for *n-dimensional array*.
A data structure in [[BEFORE/OldOrg/40 - Knowledge Base/41 - Computing/21 - Data Science and AI/Python Libraries for Data Analysis#NumPy|NumPy]] that represents tabular data.

```toc
```

## Creating
```python
import numpy as np

# 1D array
data1 = [6, 7.5, 8, 0, 1]
arr1 = np.array(data1)

# 2D array - equal-sized lists nested in another list
data2 = [[1, 2, 3, 4], [5, 6, 7, 8]]
arr2 = np.array(data2)

# zeros - arrays of a shape where all elements are zero
arr3 = np.zeros(10)  # 1x10 array of 0.
arr4 = np.zeros((3, 6)) # 3x6 array of 0.

# ones - arrays of a shape where all elements are 1.
arr5 = np.ones((5, 6, 3)) # 5x6x3 array of 1.

# empty - uninitialized array
arr6 = np.empty((2, 4)) # Uninitialized values

# arange - 
arr7 = np.arange(15) # 15-element array of values 0-14
```

## Shape and Dimensions
```python
>>> arr2.ndim
2

>>> arr2.shape
(2, 4)
```

## Data Type
```python
>>> arr1.dtype
dtype('float64')

>>> arr2.dtype
dtype('int64')
```

## Operations
### Scalar Multiplication
```python
>>> data = np.array([[1.5, -0.1, 3], [0, -3, 6.5]])
>>> data * 10
array([[15.,  -1., 30. ],
	   [ 0., -30., 65.]])
```

### Array Addition
```python
>>> data = np.array([[1.5, -0.1, 3], [0, -3, 6.5]])
>>> data + data
array([[3., -0.2,  6.],
	   [0., -6.,  13.]])
```


## Methods
### array()
`array(object, dtype=None, *, copy=True, order='K', subok=False, ndmin=0, like=None)`

`object`: array-like object or nested sequence used as source for values

`dtype`: Desired data type for the array. Inferred if not specified.

`copy`: if true, the object is copied, otherwise a copy will only be made if:
	- `object.__array__` returns a copy
	- `object` is a nested sequence, or
	- if a copy is needed to satisfy the other requirements

`order`: ('K', 'A', 'C', or 'F') - specify row order:
```tx
order | no copy                      | copy=True                                           
----- | ---------------------------- | --------------------------------------------------- 
'K'   | unchanged                    | F & C order preserved, otherwise most similar order 
'A'   | unchanged                    | F order if input if F and not C, otherwise C order  
'C'   | C order (row-major)                                                               ||
'F'   | Fortran order (column major)                                                      ||
```
`subok`: If True, then sub-classes will be passed-through, otherwise the returned array will be forced to be a base-class array (default).

`ndmin`: int, optional
       Specifies the minimum number of dimensions that the resulting array should have.  
       Ones will be pre-pended to the shape as needed to meet this requirement.

`like`: array_like
		Reference object to allow the creation of arrays which are not NumPy arrays. 
		If an array-like passed in as ``like`` supports the ``__array_function__`` protocol, the result will be defined by it.
		In this case, it ensures the creation of an array object compatible with that passed in via this argument.


---
# Source
[[Python for Data Analysis]]




