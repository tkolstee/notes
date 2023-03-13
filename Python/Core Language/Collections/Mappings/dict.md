
## Initialization
There are several ways to create a `dict`, all are equivalent.
```python
>>> a = dict(one=1, two=2, three=3)
>>> b = {'one': 1, 'two': 2, 'three': 3}
>>> c = dict(zip(['one', 'two', 'three'], [1, 2, 3]))
>>> d = dict([('two', 2), ('one', 1), ('three', 3)])
>>> e = dict({'three': 3, 'one': 1, 'two': 2})
>>> a == b == c == d == e
True
```

## Dict Comprehensions

Enclosed in curly braces, uses `key: value` notation.
```python
squares = { i: i**2 for i in range(10) }
```

## API
| Method                                  | Description                                                                                                                                                                                                                                                                                                      |
| --------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| `clear()`                               | Remove all items                                                                                                                                                                                                                                                                                                 |
| `copy()`                                | Shallow copy                                                                                                                                                                                                                                                                                                     |
| `fromkeys($type, iterable, value=None)` | Create a new dictionary with keys from iterable and values set to value.                                                                                                                                                                                                                                         |
| `get(key, default=None)`                | Return the value for key if key is in the dictionary, else default.                                                                                                                                                                                                                                              |
| `items`                                 | A set-like object containing tuples of (key, value)                                                                                                                                                                                                                                                              |
| `keys`                                  | A set-like object providing a list of dict keys                                                                                                                                                                                                                                                                  |
| `pop(key, default=<unrepresentable>)`   | Remove specified key and return the corresponding value.^[If the key is not found, return the default if given; otherwise,raise a KeyError.]                                                                                                                                                                     |
| `popitem()`                             | Remove and return a (key, value) pair as a 2-tuple.^[Pairs are returned in LIFO (last-in, first-out) order. Raises KeyError if the dict is empty.]                                                                                                                                                               |
| `setdefault(key, default=None)`         | Insert key with a value of default if key is not in the dictionary. ^[Return the value for key if key is in the dictionary, else default.]                                                                                                                                                                       |
| `update([E, ]**F)`                      | Update from dict/iterable E and F. ^[If E is present and has a .keys() method, then does:  `for k in E: D[k] = E[k]`. <br>If E is present and lacks a .keys() method, then does:  `for k, v in E: D[k] = v`.<br>In either case, this is followed by: `for k in F:  D[k] = F[k]`.]                                  |
| `values()`                              | An list-like object providing values in the dict                                                                                                                                                                                                                                                                |

## Data Model: Dunder Methods
Membership: `__contains__(k)` (based upon key)
Item access: `__delitem__`, `__getitem__`, `__setitem__`
Comparison: `__eq__`, `__ge__`, `__gt__`, `__le__`, `__lt__`, `__ne__`
Logic: `__ior__`, `__or__`, `__ror__`
Iteration: `__iter__`
Size: `__len__`, `__sizeof__`
Representation: `__repr__`, `__str__`
Ordering: `__reversed__`
