Binary search over a sorted collection to find an item or insertion point.

`bisect` is an alias for `bisect_right` which returns an insertion point after an existing item.
`bisect_left` returns the position of the existing item so insertion would occur before it.
```python
>>> from bisect import bisect, bisect_left
>>> HAYSTACK = [ x**2 for x in range(1000) ]

>>> bisect(HAYSTACK, 100000)
317
>>> HAYSTACK[316:318]
[99856, 100489]

>>> bisect(HAYSTACK, 544644)
739
>>> bisect_left(HAYSTACK, 544644)
738
>>> HAYSTACK[738:740]
[544644, 546121]
```

Bisect can be used as a faster version of `list.index(x)` when the list is sorted.
```python
>>> def grade(score, breakpoints=[60, 70, 80, 90], grades='FDCBA')
...     i = bisect.bisect(breakpoints, score)
...     return grades[i]
...
>>> [grade(score) for score in [33, 99, 77, 70, 89, 90, 100]]
['F', 'A', 'C', 'C', 'B', 'A', 'A']
```

`insort(seq, item)` inserts an item into the correct place in a sorted collection:
```python
>>> import bisect
>>> import random
>>> SIZE=7
>>> random.seed(1729)
>>> my_list = []

>>> for i in range(SIZE):
...   new_item = random.randrange(SIZE*2)
...   bisect.insort(my_list, new_item)
...   print('%2d =>' % new_item, my_list)
...
 0 => [0, 10]
 6 => [0, 6, 10]
 8 => [0, 6, 8, 10]
 7 => [0, 6, 7, 8, 10]
 2 => [0, 2, 6, 7, 8, 10]
10 => [0, 2, 6, 7, 8, 10, 10]
 0 => [0, 0, 2, 6, 7, 8, 10, 10]
```


----
# Source
*Fluent Python*, Luciano Ramalho, 2015