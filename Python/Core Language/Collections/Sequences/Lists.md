Lists are the "default option" for sequences in Python and provide a nice balance of functionality, ease, and performance.

They are Mutable, Ordered Collections.

## Creating a List
```python
>>> mylist = list()                             # []
>>> mylist = ['apple|  'banana|  3, True]       # ['apple|  'banana|  3, True]
>>> mylist = list(['apple|  'banana|  3, True]) # ['apple|  'banana|  3, True]
```

## Accessing and Changing Items
This can be done through Numeric [[Indexing and Slicing]]

## Supported Methods:

| Method                                                                                                                                                                                                                                                                                                                                                                                                   | Description                                                                                                 |
| -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
| `append(object)`                                                                                                                                                                                                                                                                                                                                                                                         | Append object to the end of the list.                                                                       |
| `clear()`                                                                                                                                                                                                                                                                                                                                                                                                | Remove all items from list.                                                                                 |
| `copy()`                                                                                                                                                                                                                                                                                                                                                                                                 | Return a shallow copy of the list.                                                                          |
| `count(value)`                                                                                                                                                                                                                                                                                                                                                                                           | Return number of occurrences of value.                                                                      |
| `extend(iterable)`                                                                                                                                                                                                                                                                                                                                                                                       | Extend list by appending elements from the iterable.                                                        |
| `index(value, start=0, stop=sys.maxsize)`                                                                                                                                                                                                                                                                                                                                                                | Return first index of value.Raises ValueError if the value is not present.                                  |
| `insert(index, object)`                                                                                                                                                                                                                                                                                                                                                                                  | Insert object before index.                                                                                 |
| `pop(index=-1)`                                                                                                                                                                                                                                                                                                                                                                                          | Remove and return item at index (default last).Raises IndexError if list is empty or index is out of range. |
| `remove(value)`                                                                                                                                                                                                                                                                                                                                                                                          | Remove first occurrence of value.Raises ValueError if the value is not present.                             |
| `reverse()`                                                                                                                                                                                                                                                                                                                                                                                              | Reverse *IN PLACE*.                                                                                         |
| `sort(key=None, reverse=False)` | Sort the list in-place in ascending order and return None.^[order of two equal elements is maintained.]^[If a key function is given, apply it once to each list item and sort them, ascending or descending, according to their function values.]^[The reverse flag can be set to sort in descending order.] |                                                                                                             |

## Data Model: Dunder Methods Supported:
Operators: `__add__`, `__iadd__`, `__imul__`, `__rmul__`, `__mul__`
Comparison: `__eq__`, `__ge__`, `__gt__`, `__le__`, `__lt__`, `__ne__`
Membership: `__contains__`
Indexing: `__delitem__`, `__getitem__`, `__setitem__`
Iteration: `__iter__`
Representation: `__repr__`, `__str__`
Sizing: `__len__`, `__sizeof__`
Ordering: `__reversed__`
