
```toc

```

## Collections

## Basic Collection Types
* str
* bytes
* range
* tuple
* list
* dict
* set


## Key Indexing
Some collections use immutable objects as keys into their items (e.g. `dict`).
If assigning to an existing key the previous value will be overwritten.
Referencing a nonexistent key raises `KeyError`.

```python
mydict = { 'foo': 1, 'bar': 2, 'baz': 3 }
mydict['foo']   # 1
mydict['baz']   # 3

mydict['bar'] = 10  # { 'foo': 1, 'bar': 10, 'baz': 3 }

del mydict['foo']   # { 'bar': 2, 'baz': 3 }
```



## Protocols
| Name                              | Description                                                                                                              | Override Abstract                                                  | Also inherits                    |
| --------------------------------- | ------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------ | -------------------------------- |
| `collections.abc.Container`       | Supports `in`, `not in`                                                                                                  | `__contains__`                                                     |                                  |
| `collections.abc.Iterable`        | Yields an iterator                                                                                                       | `__iter__`                                                         |                                  |
| `collections.abc.Iterator`        | Allows iteration                                                                                                         | `__next__`                                                         | `Iterable`                       |
| `collections.abc.ItemsView`       | View of items from mapping e.g. `dict.items()`                                                                           | `__contains__`, `__iter__`                                         | `MappingView`, `Set`             |
| `collections.abc.KeysView`        | View of keys from a mapping, e.g. `dict.keys()`                                                                          | `__contains__`, `__iter__`                                         | `MappingView`, `Set`             |
| `collections.abc.ByteString`      | Read-only, mutable sequence                                                                                              | `__len__`                                                          |                                  |
| `collections.abc.Collection`      | Union of sized, iterable, container                                                                                      | `__contains__`, `__iter__`, `__len__`                              | `Sized`, `Iterable`, `Container` |
| `collections.abc.Generator`       | Implements [PEP-342](https://peps.python.org/pep-0342/) (send, throw, close)                                             | `close`, `__iter__`, `__next__`                                    | `Iterator`                       |
| `collections.abc.Hashable `       | Identifies objects in a repeatable way                                                                                   | `__hash__`                                                         |                                  |
| `collections.abc.Mapping`         | Represents a mapping by immutable keys, e.g. dict (`__contains__`, `keys`, `items`, `values`, `get`, `__eq__`, `__ne__`) | `__getitem__`, `__iter__`, `__len__`                               | `Collection`                     |
| `collections.abc.MappingView`     | Represents a view from a mapping, e.g. `dict.keys()`                                                                     | `__len__`                                                          | `Sized`                          |
| `collections.abc.MutableMapping`  | Represents a mapping (e.g. dict) whose contents are mutable (`pop`, `popitem`, `clear`, `update`, `setdefault`)          | `__getitem__`, `__setitem__`, `__delitem__`, `__iter__`, `__len__` | `Mapping`                        |
| `collections.abc.Set`             | Allows set algebra via methods and infix operators                                                                       | `__contains__`, `__iter__`, `__len__`                              | `Collection`                     |
| `collections.abc.Sized`           | Allows retrieval of length (number of items or size)                                                                     | `__len__`                                                          |                                  |
| `collections.abc.ValuesView`      | Allows use with `values()` as seen with `dict`                                                                           | `__contains__`, `__iter__`                                         | `MappingView`, `Collection`      |
| `collections.abc.Sequence`        | Allows numeric indexing and slicing (`contains`, `iter`, `reversed`, `index`, `count`)                                   | `__getitem__`, `__len__`                                           | `Reversible`, `Collection`       |
| `collections.abc.Reversible`      | Allows reversing of item ordering                                                                                        | `__reversed__`                                                     | `Iterable`                       |
| `collections.abc.MutableSet`      | Represents a mutable set collection (clear, pop, remove, ior, iand, ixor, isub)                                          | `__contains__`, `__iter__`, `__len__`, `add`, `discard`            | `Set`                            |
| `collections.abc.MutableSequence` | Mutable collection of numerically indexed items                                                                          | `__getitem__`, `__setitem__`, `__delitem__`, `__len__`, `insert`   | `Sequence`                       |

## Iteration
### Default Process

#### Client-side Process
An *iterable* object is a long-lived object that represents a collection.
An *iterator* is a short-lived object that represents the "place" in the iteration, like a cursor.

The client:
- Requests and gets an iterator from an iterable object using `iter(object)`.
- Calls `__next__()` when it wants the next item.
- Catches `StopIteration` when the collection is exhausted.
- Discards the iterator as it is now useless.


#### Iterable Objects
- Inherits from abstract class `collections.abc.Iterable`.
- Implements abstract method `__iter__()` which returns an iterator.

#### Iterator Objects
- Implement `__next__()` which returns the next element or raises `StopIteration` when done.
- Iterators are also iterable. Usually their `__iter__()` method just calls `return self`.

#### The iter() function
The global `iter()` backend can handle objects that don't fully implement `__iter__()`.

A call to `iter(object)`:
- First calls `object.__iter__()` and returns the iterator if received.
- Tries calling `object.__getitem__(0)` and returns a custom iterator that:
	- Keeps track of current index starting with zero
	- Each call to `__next__()` returns the value and increments the index
	- Catches `IndexError` and re-raises as `StopIteration`

##### Two-argument form of iter()
If passed two arguments, iter produces a special custom iterator.
The iterator returned by `iter(callable, sentinel)` whose `__next__` does the following:
	- Calls the `callable` and saves the return value.
	- If the return value matches the sentinel, raises `StopIteration`
	- Otherwise, returns the value received by the callable.

### Iteration Functions
Some of these are native, some in the `itertools` module.

| Function                        | Purpose                                                 |
| ------------------------------- | ------------------------------------------------------- |
| `enumerate(i)`                  | Returns tuples of (index, value)                        |
| `sum(i)`                        | Returns sum of all elements                             |
| `min(i)` / `max(i)`             | Returns smallest/largest values in iterable             |
| `i.count('val')`                | Counts instances of matching elements                   |
| `itertools.islice(i, count)`    | Returns a new iterator representing a slice of another  |
| `any(i)` / `all(i)`             | Returns true if any/all elements are truthy             |
| `zip(i1, i2, i3)`               | Interleaves elements, stopping once first is exhausted. |
| `map(fn, i)`                    | Runs a function across all items and returns results    |
| `filter(fn, i)`                 | Returns only results where fn returns True              |
| `functools.reduce(fn, l, init)` | See below                                                        |

`islice` is evaluated lazily, so it affects the parent iterator's state.
````ad-example
title: Example: Use of `islice`
collapse: true
```python
import itertools

squares = (x*x for x in range(1,100_000_001))
y = itertools.islice(squares, 3)
next(y)       # 1
next(squares) # 4
next(squares) # 9
next(y)       # 16
next(y)       # 25
next(y)       # (raises StopIteration)
next(squares) # 36
```
````

`map` is evaluated lazily in Python 3 but not Python 2.x
````ad-example
title: Example: Use of `map`
collapse: true
```python
l = [ 1, 2, 3 ]
m = map(lambda x: f"ITEM: {x}", l)

"""
m = <map object at 0x...>
list(m) = [ 'ITEM: 1', 'ITEM: 2', 'ITEM: 3' ]
"""
```

Map can use multiple arguments for multiple collections
Lambda should have the same number of arguments as the number of collections.
```python
l = [1, 2, 3]
m = ['a', 'b', 'c']
n = map(lambda x, y: f"{x}={y}", m, l)


""" 
list(n) = [ 'a=1', 'b=2', 'c=3' ]
"""
```

````

`reduce` iteratively accumulates a value from a sequence
````ad-example
title: Example: Use of `reduce`
collapse: true


`reduce` takes a two-argument function, a collection, and an optional initialization value.

The function arguments are:
- Returned value from previous run (first run is initialization value if given or first value in collection if not)
- Current value in iteration

Returns the final accumulated value.

```python
import functools

s = functools.reduce(
	lambda accum, cur: accum+cur,   # Add value in list to accumulated sum
	range(10),                       # Add numbers from 0-9
	100                              # Start with sum at 100
)
```
Sum of numbers from 0-9 is 45, but since we started at 100 the returned result is 145.
````

## Generators

### Generator Functions

Can be implemented by using the `yield` keyword within a function.
The function will return an object of class `generator`.
`generator` is iterable (implements `__next__()` and  `StopIteration`)
Each item is evaluated lazily. The function is run until the `yield` statement and returns the value.

`````ad-example
```python
def gen123():
	""" Generates the numbers 1-3 """
	for i in range(1, 4):
		yield i
```
`````

A generator does not have to be finite - just don't try to coalesce it to a list.
`````ad-example
```python
def gen_even_numbers():
	nextnum = 0
	while True:
		nextnum += 2
		yield nextnum
```
`````

### Generator Expressions
These are comprehensions that yield generators.

`````ad-example
```python
(expr(item) for item in iterable)

# Generate the first 100M squares, returns instantly
(x*x for x in range(1, 100_000_001))

# Sum of first 100M squares, returns in about 13s for me.
sum(x*x for x in range(1, 100_000_001))
```
`````

### Chaining Multiple Generators
When generators take a parameter as input and act as a filter, they can be chained together:

`````ad-example
```python
def first_three(x):
	count = 0
	for i in x:
		if count > 2:
			break
		yield i
		count += 1

def add_one(x):
	for i in x:
		yield i+1

def distinct_items(x):
	for i in set(x):
		yield i

mylist = [ 1, 2, 2, 1, 3, 4, 5, 4, 6 ]
x = list( first_three( distinct_items( add_one ( mylist ) ) ) )
```
result: `[ 2, 3, 4 ]`

`````



---
# See Also
[Python Docs: collections.abc](https://docs.python.org/3/library/collections.abc.html)
