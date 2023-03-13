Binary search over a collection.


```python
import bisect
import sys

HAYSTACK = [1, 4, 5, 6, 8, 12, 15, 20, 21, 23, 23, 26, 29, 30]
needle = 10

def demo():
	position = bisect.bisect(HAYSTACK, needle)
```
`position = bisect_fn(HAYSTACK, needle)` gets the insertion point
`offset = `

----
# Source
*Fluent Python*, Luciano Ramalho, 2015