
```toc

```

## Collections

### Basic Collection Types
* str
* bytes
* range
* tuple
* list
* dict
* set

### Protocols
#### Container Protocol
Supports `in` and `not in` operators
Implementing:
- Inherit from `collections.abc.Container`
- Override abstract method `__contains__`

#### Sized Protocol
Supports `len()`

#### Iterable
Yields an iterator when requested
Implementing:
- Inherit from `collections.abc.Iterable`
- Override abstract method `__iter__`

#### Sequence
Numerically indexed, supports `index`, `count`, `reversed`, etc.

#### Iterator Protocol
Iterates through the elements of an iterable (possibly `self`)
- Inherit from abstract class `collections.abc.Iterator`
- Override abstract method `__next__`
- Inherits from Iterable as well including `__iter__` method.

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

---
# See Also
[Python Docs: collections.abc](https://docs.python.org/3/library/collections.abc.html)
