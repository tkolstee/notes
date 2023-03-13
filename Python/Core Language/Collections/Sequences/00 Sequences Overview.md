Sequences are collections that support numeric indexing and thus are ordered.
Examples include `list`, `tuple`, `str`, `bytes`.

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


# Sources
[Built-in Types — Python 3.11.2 documentation](https://docs.python.org/3/library/stdtypes.html)
*Fluent Python*, Luciano Ramalho, 2015
