## Indexing
Positive indices are positions into the collection starting with zero.
Negative indices (not supported by all collections) start with `-1` as the last element and proceed to the left.
```python
numbers = [ 24, 2, 88, 26, 77, 71 ]
numbers[0]  # 24
numbers[2]  # 88
numbers[-1] # 71
numbers[-3] # 26
```

Assignment is only possible when replacing a single element:
```python
>>> x = list(range(10))
>>> x
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
>>> x[3] = 33
>>> x
[0, 1, 2, 33, 4, 5, 6, 7, 8, 9]
>>> x[10] = 10
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IndexError: list assignment index out of range
```
