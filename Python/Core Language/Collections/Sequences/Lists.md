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
| Method              | Description                               | Example |     |
| ------------------- | ----------------------------------------- | ------- | --- |
| `append`            | add item to end of list                   |         |     |
| `clear`             | Remove all items                          |         |     |
| `copy`              | Shallow copy                              |         |     |
| `count`             | Number of occurrences of value            |         |     |
| `extend`            | Append elements from an interable         |         |     |
| `index`             | Index of first occurence of a value       |         |     |
| `insert`            | Insert object before index                |         |     |
| `pop`               | Remove and return item at index (def: -1) |         |     |
| `remove`            | Remove first occurrence of a value        |         |     |
| `reverse`           | Reverse in place                          |         |     |
| `sort`              | Sort in place                                          |         |     |
| `__add__`           | Concatenate lists                                         |         |     |
| `__class_getitem__` |                                           |         |     |
| `__contains__`      |                                           |         |     |
| `__delattr__`       |                                           |         |     |
| `__delitem__`       |                                           |         |     |
| `__dir__`           |                                           |         |     |
| `__doc__`           |                                           |         |     |
| `__eq__`            |                                           |         |     |
| `__format__`        |                                           |         |     |
| `__ge__`            |                                           |         |     |
| `__getattribute__`  |                                           |         |     |
| `__getitem__`       |                                           |         |     |
| `__gt__`            |                                           |         |     |
| `__hash__`          |                                           |         |     |
| `__iadd__`          |                                           |         |     |
| `__imul__`          |                                           |         |     |
| `__init__`          |                                           |         |     |
| `__init_subclass__` |                                           |         |     |
| `__iter__`          |                                           |         |     |
| `__le__`            |                                           |         |     |
| `__len__`           |                                           |         |     |
| `__lt__`            |                                           |         |     |
| `__mul__`           |                                           |         |     |
| `__ne__`            |                                           |         |     |
| `__new__`           |                                           |         |     |
| `__reduce__`        |                                           |         |     |
| `__reduce_ex__`     |                                           |         |     |
| `__repr__`          |                                           |         |     |
| `__reversed__`      |                                           |         |     |
| `__rmul__`          |                                           |         |     |
| `__setattr__`       |                                           |         |     |
| `__setitem__`       |                                           |         |     |
| `__sizeof__`        |                                           |         |     |
| `__str__`           |                                           |         |     |
| `__subclasshook__`  |                                           |         |     |


| Method | Description | Example |
|---|---|---|
| `__add__(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `__class__(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `__class_getitem__(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `__contains__(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `__delattr__(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `__delitem__(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `__dir__(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `__doc__(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `__eq__(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `__format__(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `__ge__(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `__getattribute__(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `__getitem__(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `__gt__(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `__hash__(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `__iadd__(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `__imul__(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `__init__(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `__init_subclass__(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `__iter__(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `__le__(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `__len__(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `__lt__(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `__mul__(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `__ne__(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `__new__(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `__reduce__(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `__reduce_ex__(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `__repr__(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `__reversed__(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `__rmul__(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `__setattr__(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `__setitem__(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `__sizeof__(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `__str__(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `__subclasshook__(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `append(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `clear(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `copy(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `count(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `extend(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `index(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `insert(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `pop(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `remove(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `reverse(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |
| `sort(iterable=(), /)` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. | |