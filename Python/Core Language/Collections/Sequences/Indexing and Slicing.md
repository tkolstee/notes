
```toc
```

## Numeric Indexing
Collections that accept numeric indexes are numbered starting from 0.
Negative indexing starts with -1 at the end, -2 second-to-last, etc.
If the collection is mutable, assignment can be made the same way.
Accessing an element which doesn't exist (for reading or assignment) results in an `IndexError`.
`del` can delete an individual element if indexed.

```python
>>> mylist = [ 'a', 'b', 'c', 'd', 'e' ]

>>> mylist[0]
'a'
>>> mylist[3]
'd'
>>> mylist[-2]
'd'

>>> mylist[3] = 'D'
>>> mylist
['a', 'b', 'c', 'D', 'e']

>>> mylist[5]
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
IndexError: list index out of range

>>> del mylist[3]
>>> mylist
['a', 'b', 'c', 'e']
```

## Slicing
Reference a subset of a sequence in order.

Syntax is `collection[start:stop:step]` with each part being optional.

`start` indicates the element to start with, inclusive with a default of 0.
`stop` indicates the element to end BEFORE. Defaults to end of collection.
`step` indicates the number of items to advance, default 1.

```python
>>> mylist = [ 'a', 'b', 'c', 'd', 'e', 'f', 'g']
>>> mylist[2:5]
['c', 'd', 'e']
>>> mylist[:2]
['a', 'b']
>>> mylist[4:]
['e', 'f', 'g']
>>> mylist[0:5:2]
['a', 'c', 'e']
>>> mylist[1:5:2]
['b', 'd']
>>> mylist[::2]
['a', 'c', 'e', 'g']
>>> mylist[:]
['a', 'b', 'c', 'd', 'e', 'f', 'g']
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
`step` can be used, but the replacement slice must be the same size as the original.

```python
>>> mylist = [ 1, 1, 1, 1, 1, 1 ]

>>> mylist[0:3] = [2, 2, 2]        # [2, 2, 2, 1, 1, 1]
>>> mylist[1:4] = [ 3, 3 ]         # [2, 3, 3, 1, 1]
>>> mylist[1::2] = [ 4, 4 ]        # [2, 4, 3, 4, 1]

>>> del mylist[1::2]               # [2, 3, 1]

>>> mylist = [ 1, 1, 1, 1, 1, 1 ]
>>> mylist[0:3:2] = [ 'a', 'b', 'c', 'd' ]
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
ValueError: attempt to assign sequence of size 4 to extended slice of size 2
```

