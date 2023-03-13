Sequences are collections that support numeric indexing and thus are ordered.
Examples include `list`, `tuple`, `str`, `bytes`.

Elements in a sequence can be accessed with [[Indexing and Slicing]].
Sequences are [[Classifying Sequences|classified]] as [[Classifying Sequences#Mutable vs. Immutable|Mutable or Immutable]] and [[Classifying Sequences#Container vs. Flat|Flat or Container]].

[[Built-In Sequences]] are made with C and are extremely fast. These include [[Lists]], [[Tuples]], [[Deque]]s, [[Strings]], [[Bytes]], [[Byte Array]]s, [[Memory Views]], and [[Python/Core Language/Collections/Sequences/Arrays|Arrays]]

[[Comprehensions]] are fast ways of creating a sequence with a compact, for-loop like structure.
[[Tuples]] are useful as immutable lists or records with positional or [[Tuples#Named Tuples|named]] fields.
[[Sorting]] can be done either in natural order or with custom functions used to compare them.

[[Memory Views]] are mapped to shared areas of memory without copying and allow for [[Python Memory Mapping|Memory Mapping]] to take place.


## Common Sequence Operations
| Operation              | Result                                                                                                                       |
| ---------------------- | ---------------------------------------------------------------------------------------------------------------------------- |
| `x in s`               | `True` if an item of `s` is equal to `x`, else `False`.^[Sometimes used for subsequence testing, as `'car' in 'precarious'`] |
| `x not in s`           | `False` if an item of `s` is equal to `x`, else `True`.                                                                      |
| `s + t`                | Concatenation of `s` and `t`^[Results in new object if list is immutable.]                                                                                                 |
| `s * n` or `n * s`     | Adding `s` to itself `n` times ^[References, doesn't append. This can lead to difficult bugs.]                                                                                              |
| `s[i]`                 | `i`th item of `s` starting from 0 (see [[#Indexing]])                                                                        |
| `s[i:j]`               | Slice of `s` from `i` to `j` (see [[#Slicing]])                                                                              |
| `s[i:j:k]`             | Every `k`th item from `i` to `j` (see [[#Slicing]])                                                                          |
| `len(s)`               | Number of items in `s`                                                                                                       |
| `min(s)`               | Smallest item of `s`                                                                                                         |
| `max(s)`               | Largest item of `s`                                                                                                          |
| `s.index(x[, i[, j]])` | Index of 1st occurrence of `x` in `s`, at or after `i` but before `j` if given                                               |
| `s.count(x)`           | Number of occurrences of `x` in `s`                                                                                          |

## Queues
[[Deque]], `queue.Queue`, `multiprocessing.Queue`, `asyncio.Queue`, `asyncio.LifoQueue`, `asyncio.PriorityQueue`, `asyncio.JoinableQueue`, `heapq`

# Sources
[Built-in Types — Python 3.11.2 documentation](https://docs.python.org/3/library/stdtypes.html)
*Fluent Python*, Luciano Ramalho, 2015
