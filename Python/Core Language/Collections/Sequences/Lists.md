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
| ------ | ----------- | ------- |
| `__add__` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `__class__` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `__class_getitem__` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `__contains__` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `__delattr__` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `__delitem__` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `__dir__` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `__doc__` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `__eq__` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `__format__` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `__ge__` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `__getattribute__` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `__getitem__` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `__gt__` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `__hash__` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `__iadd__` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `__imul__` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `__init__` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `__init_subclass__` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `__iter__` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `__le__` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `__len__` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `__lt__` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `__mul__` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `__ne__` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `__new__` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `__reduce__` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `__reduce_ex__` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `__repr__` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `__reversed__` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `__rmul__` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `__setattr__` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `__setitem__` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `__sizeof__` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `__str__` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `__subclasshook__` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `append` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `clear` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `copy` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `count` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `extend` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `index` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `insert` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `pop` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `remove` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `reverse` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |
| `sort` | Built-in mutable sequence.If no argument is given, the constructor creates a new empty list.The argument must be an iterable if specified. |  |