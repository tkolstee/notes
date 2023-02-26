
Suppress traceback messages
```python
import sys
sys.tracebacklimit = 0
```

Tracebacks are objects. Every exception has a `__traceback__` attribute which references a `traceback` object.

You should handle traceback objects within the context of the `except` block. Keeping references to them forms a closure which includes all the stack frames, code, and local variables and can be quite large. Maintaining them prevents GC.

## Traceback Module
```python
import traceback

"""prints the traceback"""
traceback.print_tb(my_traceback)

"""renders as a string"""
tbstring = format_tb(my_traceback)
```

