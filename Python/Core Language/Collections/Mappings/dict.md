
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
