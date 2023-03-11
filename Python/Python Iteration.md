
## Default Process

### Client-side Process
An *iterable* object is a long-lived object that represents a collection.
An *iterator* is a short-lived object that represents the "place" in the iteration, like a cursor.

The client:
- Requests and gets an iterator from an iterable object using `iter(object)`.
- Calls `__next__()` when it wants the next item.
- Catches `StopIteration` when the collection is exhausted.
- Discards the iterator as it is now useless.


### Iterable Objects
- Inherits from abstract class `collections.abc.Iterable`.
- Implements abstract method `__iter__()` which returns an iterator.

### Iterator Objects
- Implement `__next__()` which returns the next element or raises `StopIteration` when done.
- Iterators are also iterable. Usually their `__iter__()` method just calls `return self`.

### The iter() function
The global `iter()` backend can handle objects that don't fully implement `__iter__()`.

A call to `iter(object)`:
- First calls `object.__iter__()` and returns the iterator if received.
- Tries calling `object.__getitem__(0)` and returns a custom iterator that:
	- Keeps track of current index starting with zero
	- Each call to `__next__()` returns the value and increments the index
	- Catches `IndexError` and re-raises as `StopIteration`

#### Two-argument form of iter()
If passed two arguments, iter produces a special custom iterator.
The iterator returned by `iter(callable, sentinel)` whose `__next__` does the following:
	- Calls the `callable` and saves the return value.
	- If the return value matches the sentinel, raises `StopIteration`
	- Otherwise, returns the value received by the callable.

## Iterator Tools
In the itertools module we have several functions for iterating through objects:

| Function            | Purpose                                                    |
| ------------------- | ---------------------------------------------------------- |
| `enumerate(i)`      | Returns tuples of (index, value)                           |
| `sum(i)`            | Returns sum of all elements                                |
| `min(i)` / `max(i)` | Returns smallest/largest values in iterable                |
| `i.count('val')`    | Counts instances of matching elements                      |
| `islice(i, count)`         | Returns a new iterator representing a slice of another^[1] |

[^1]: Lazily evaluated, so each call depends upon and modifies original iterator's state.


```python
import itertools

# Get tuples of (index, value)
list(enumerate(['a', 'b', 'c', 'd']))  
# [(0, 'a'), (1, 'b'), (2, 'c'), (3, 'd')]

# Get sum of all elements
sum( x*x for x in range(1, 1000001))
# 333333833333500000

# Get min and max elements
smallest = min(l1)
largest = max(l1)

# Get count of matching elements
l1.count('a')

# islice()
# Iterable representing a slice of another iterable
# Lazily evaluated, so each call depends upon and
# modifies origintal iterator's state
squares = (x*x for x in range(1,100_000_001))
y = itertools.islice(squares, 3)
next(y)       # 1
next(squares) # 4
next(squares) # 9
next(y)       # 16
next(y)       # 25
next(y)       # (raises StopIteration)
next(squares) # 36

# Unbounded iterator of all integers >0
all_squares = (x*x for x in itertools.count())
# WARNING: Using generator comprehension here.
# Doing this as a list comprehension would be
# an infinite loop.

# Return true if any element is true/truthy.
any(l)  # Return true iff any elment is true/thy
all(l)  # Return true iff all elements are true/thy
any([]) # is false
all([]) # is true

# Interleave corresponding elements
lower = ['a', 'b', 'c']
upper = ['A', 'B', 'C', 'D']
nato = ['alpha', 'bravo', 'charlie', 'delta']
[ x for x in zip(lower, upper, nato)]
# [('a', 'A', 'alpha'),
#  ('b', 'B', 'bravo'),
#  ('c', 'C', 'charlie'),
#  # Note: Stops here as lower is exhausted.
#  ]

# Run a function across all items
# WARNING: Not lazy in Python 2.x
m = map(lambda x: f"ITEM: {x}", range(5))
# <map object at 0x....>
list(m)  # ['ITEM: 0', 'ITEM: 1', ..., 'ITEM: 4']

# Multiple args for multiple collections.
data1 = [ 'a', 'b', 'c' ]
data2 = [ 'alpha', 'bravo', 'charlie' ]
def printit(x, y):
	return f"{x} = {y}"
list(map(printit, data1, data2))
# [ 'a = alpha', 'b = bravo', 'c = charlie' ]

# Return only entities that pass a function test.
mylist(filter(lambda x: x>=0, nums))

# Applies a two-argument function over a collection.
# First argument is an accumulated value (initial value if given or takes first value in sequence).
# Second argument is next value in collection
# Often used for summation or multiplication (Use initial value of 1 for mult, 0 for summation).
x = functools.reduce(lambda x, y: x+y, range(10), 100)
# Equvalent code
x = 100
for value in range(10):
	x += value
```


---
# See Also
[Python Docs: collections.abc](https://docs.python.org/3/library/collections.abc.html)



---
# See Also
[Python Docs: collections.abc](https://docs.python.org/3/library/collections.abc.html)
