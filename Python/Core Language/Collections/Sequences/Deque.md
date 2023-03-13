`collections.deque` is a thread-safe, double-ended queue.

```toc
```

## Removing Elements
```python
>>> dq = deque(range(10)) #      deque([0, 1, 2, 3, 4, 5, 6, 7, 8, 9])
>>> dq.pop()              # 9    deque([0, 1, 2, 3, 4, 5, 6, 7, 8])
>>> dq.pop()              # 8    deque([0, 1, 2, 3, 4, 5, 6, 7])
>>> dq.popleft()          # 0    deque([1, 2, 3, 4, 5, 6, 7])
>>> dq.popleft()          # 1    deque([2, 3, 4, 5, 6, 7])
>>> dq.pop()              # 7    deque([2, 3, 4, 5, 6])
>>> del dq[2]             #      deque([2, 3, 5, 6])
```

## Adding Elements
`append(x)` and `appendleft(x)` add an element to the right or left side of the deque.
`extend(i)` and `extendleft(i)` add all elements from an iterable to the right or left side of the deque.
```python
>>> dq = deque(range(2))       # deque([0, 1])
>>> dq.append('a')             # deque([0, 1, 'a'])
>>> dq.appendleft('b')         # deque(['b', 0, 1, 'a'])
>>> dq.extend(['C', 'D', 'E']) # deque(['b', 0, 1, 'a', 'C', 'D', 'E'])
>>> dq.extendleft(['F', 'G'])  # deque(['G', 'F', 'b', 0, 1, 'a', 'C', 'D', 'E'])
```

```ad-note
`.extendleft` adds items in "reverse" order, queueing them one at a time.
```

## Maximum Length
Creating with `maxlen` will cause elements beyond that to be discarded from the opposite side of the deque.
```python
>>> dq = deque(range(3), maxlen=5)  # deque([0, 1, 2], maxlen=5)
>>> dq.append('a')                  # deque([0, 1, 2, 'a'], maxlen=5)
>>> dq.append('b')                  # deque([0, 1, 2, 'a', 'b'], maxlen=5)
>>> dq.append('c')                  # deque([1, 2, 'a', 'b', 'c'], maxlen=5)
>>> dq.appendleft('d')              # deque(['d', 1, 2, 'a', 'b'], maxlen=5)
```

## Rotating
`.rotate(n)` rotates the entire queue right (positive n) or left (negative n) with wraparound:
```python
>>> dq = deque(
...   range(10), maxlen=10
... )                               # deque([0, 1, 2, 3, 4, 5, 6, 7, 8, 9], maxlen=10)
>>> dq.rotate(3)                    # deque([7, 8, 9, 0, 1, 2, 3, 4, 5, 6], maxlen=10)
>>> dq.rotate(-4)                   # deque([1, 2, 3, 4, 5, 6, 7, 8, 9, 0], maxlen=10)
>>> dq.appendleft(-1)               # deque([-1, 1, 2, 3, 4, 5, 6, 7, 8, 9], maxlen=10)
>>> dq.extend([11, 22, 33])         # deque([3, 4, 5, 6, 7, 8, 9, 11, 22, 33], maxlen=10)
>>> dq.extendleft([10, 20, 30, 40]) # deque([40, 30, 20, 10, 3, 4, 5, 6, 7, 8], maxlen=10)
```

## Data Model Support
| Function       | Operation Supported                | Example                  |
| -------------- | ---------------------------------- | ------------------------ |
| `__ladd__`     | In-place concatenation             | `s += s2`                |
| `append`       | Append one element to right        | `s.append(e)`            |
| `appendleft`   | Append one element to left         | `s.appendleft(e)`        |
| `clear`        | Delete all items                   | `s.clear()`              |
| `__copy__`     | Shallow copy                       | `copy.copy(s)`           |
| `count`        | Count occurrences of an element    | `s.count(e)`             |
| `__delitem__`  | Remove item at position            | `del s[p]`               |
| `extend`       | Add items from iterable to right   | `s.extend([e1, e2])`     |
| `extendleft`   | Add items from iterable to left    | `s.extendleft([e1, e2])` |
| `__getitem__`  | Allows numeric indexing            | `s[3]`, `s[-2]`          |
| `__iter__`     | Returns iterator                   | `for x in s:`            |
| `__len__`      | Gets number of items               | `len(s)`                 |
| `pop`          | Remove and return last item        | `s.pop()`                |
| `popleft`      | Remove and return first item       | `s.popleft()`            |
| `remove`       | Remove first occurrence by value   | `s.remove(e)`            |
| `reverse`      | Reverse in-place                   | `s.reverse()`            |
| `__reversed__` | Get iterator to scan in reverse    | `reversed(s)`            |
| `rotate`       | Rotate items right or left (+/-)   | `s.rotate(n)`            |
| `__setitem__`  | Replace existing item with new one | `s[3] = e`               |
|                |                                    |                          |

Not supported: `__add__`, `__contains__`, `.copy`, `.index`, `insert`, `__mul__`, `__lmul__`, `__rmul__`, `.sort`

