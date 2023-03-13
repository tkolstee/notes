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
| Method | Description | Example |
|---|---|---|
| `__add__($self, value, /)` | Return self+value. | |
| `__class__None` | type(object) -> the object's typetype(name, bases, dict, **kwds) -> a new type | |
| `__class_getitem__None` | See PEP 585 | |
| `__contains__($self, key, /)` | Return key in self. | |
| `__delattr__($self, name, /)` | Implement delattr(self, name). | |
| `__delitem__($self, key, /)` | Delete self[key]. | |
| `__dir__($self, /)` | Default dir() implementation. | |
| `__eq__($self, value, /)` | Return self==value. | |
| `__format__($self, format_spec, /)` | Default object formatter. | |
| `__ge__($self, value, /)` | Return self>=value. | |
| `__getattribute__($self, name, /)` | Return getattr(self, name). | |
| `__getitem__None` | x.__getitem__(y) <==> x[y] | |
| `__gt__($self, value, /)` | Return self>value. | |
| `__iadd__($self, value, /)` | Implement self+=value. | |
| `__imul__($self, value, /)` | Implement self*=value. | |
| `__init__($self, /, *args, **kwargs)` | Initialize self.  See help(type(self)) for accurate signature. | |
| `__init_subclass__None` | This method is called when a class is subclassed.The default implementation does nothing. It may beoverridden to extend subclasses. | |
| `__iter__($self, /)` | Implement iter(self). | |
| `__le__($self, value, /)` | Return self<=value. | |
| `__len__($self, /)` | Return len(self). | |
| `__lt__($self, value, /)` | Return self<value. | |
| `__mul__($self, value, /)` | Return self*value. | |
| `__ne__($self, value, /)` | Return self!=value. | |
| `__new__($type, *args, **kwargs)` | Create and return a new object.  See help(type) for accurate signature. | |
| `__reduce__($self, /)` | Helper for pickle. | |
| `__reduce_ex__($self, protocol, /)` | Helper for pickle. | |
| `__repr__($self, /)` | Return repr(self). | |
| `__reversed__($self, /)` | Return a reverse iterator over the list. | |
| `__rmul__($self, value, /)` | Return value*self. | |
| `__setattr__($self, name, value, /)` | Implement setattr(self, name, value). | |
| `__setitem__($self, key, value, /)` | Set self[key] to value. | |
| `__sizeof__($self, /)` | Return the size of the list in memory, in bytes. | |
| `__str__($self, /)` | Return str(self). | |
| `__subclasshook__None` | Abstract classes can override this to customize issubclass().This is invoked early on by abc.ABCMeta.__subclasscheck__().It should return True, False or NotImplemented.  If it returnsNotImplemented, the normal algorithm is used.  Otherwise, itoverrides the normal algorithm (and the outcome is cached). | |
| `append($self, object, /)` | Append object to the end of the list. | |
| `clear($self, /)` | Remove all items from list. | |
| `copy($self, /)` | Return a shallow copy of the list. | |
| `count($self, value, /)` | Return number of occurrences of value. | |
| `extend($self, iterable, /)` | Extend list by appending elements from the iterable. | |
| `index($self, value, start=0, stop=sys.maxsize, /)` | Return first index of value.Raises ValueError if the value is not present. | |
| `insert($self, index, object, /)` | Insert object before index. | |
| `pop($self, index=-1, /)` | Remove and return item at index (default last).Raises IndexError if list is empty or index is out of range. | |
| `remove($self, value, /)` | Remove first occurrence of value.Raises ValueError if the value is not present. | |
| `reverse($self, /)` | Reverse *IN PLACE*. | |
| `sort($self, /, *, key=None, reverse=False)` | Sort the list in ascending order and return None.The sort is in-place (i.e. the list itself is modified) and stable (i.e. theorder of two equal elements is maintained).If a key function is given, apply it once to each list item and sort them,ascending or descending, according to their function values.The reverse flag can be set to sort in descending order. | |