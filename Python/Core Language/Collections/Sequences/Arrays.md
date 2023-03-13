## Arrays
`array.array` is more efficient than a list, but can contain only one type of value.
Supports standard mutable sequence methods (`.pop`, `.insert`, `.extend`)
Supports additional fast (de)serialization with `.frombytes` and `.tofile`

```python
>>> from array import array
>>> from random import random
>>> floats = array('d', (random() for i in range(10**7)))
>>> floats[-1]
0.3106329370135986
>>> with open('floats.bin', 'wb') as fp:
...   floats.tofile(fp)
...
>>> floats2=array('d')
>>> with open('floats.bin', 'rb') as fp:
...   floats2.fromfile(fp, 10**7)
...
>>> floats2[-1]
0.3106329370135986
>>> floats2 == floats
True
```
`array('d')` is a type code that maps this to a C type.
