Sequences are collections that support numeric indexing and thus are ordered.
```toc

```

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

## Slicing
Taking a subset of a collection in order.

Note that `stop` takes the number(s) up to, but not including index `stop` itself.
Numbers may be omitted with their place held by the `:`
```python
# 1-argument form:  [stop]
numbers[4]    # indices 0-3

# 2-argument form: [start:stop]
numbers[2:5]  # indices 2-4
numbers[:5]   # indices 0-4
numbers[2:]   # indices 2-end
numbers[:]    # ALL indices, 0-end

# 3-argument form: [start:stop:step]
numbers[2:8:2]  # indices 2, 4, 6
numbers[7:20:3] # indices 7, 10, 13, 16, 18
numbers[::2]    # Every other item (0, 2, 4...)
numbers[:12:2]  # indices 0, 2, 4, 6, 8, 10
numbers[5::2]   # indices 5, 7, 9, ... end
```

### Why Exclude the Last (stop) item?
- It's easy to see the length of the range returned:   `range(3)` and `list[:3]` return 3 items.
- It's easy to compute the length when start and stop are both used:  `list[4:9]` is 5 items (stop - start)
- It's easy to paginate or split a sequence into parts:
```python
mylist = list(range(101))
start = 0
length = 10
while start < len(mylist):
	stop = start + length
	print(mylist[start:stop])
	start = stop
```

```output
[0, 1, 2, 3, 4, 5, 6, 7, 8, 9]
[10, 11, 12, 13, 14, 15, 16, 17, 18, 19],
...
[90, 91, 92, 93, 94, 95, 96, 97, 98, 99],
[100]
```

### Assigning to Slices
This will replace the slice with the given values, even if they are of a different size:

```python
>>> x = list(range(10))
>>> x[3:5] = [ 33, 44, 55, 66 ]
>>> x
[0, 1, 2, 33, 44, 55, 66, 5, 6, 7, 8, 9]
```

To insert a number between other numbers, use a zero-length slice (start = stop)
```python
>>> x = list(range(10))
>>> x[3:3] = [ 33, 44, 55, 66 ]
>>> x
[0, 1, 2, 33, 44, 55, 66, 3, 4, 5, 6, 7, 8, 9]
```