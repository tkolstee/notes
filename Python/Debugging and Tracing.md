## sys.settrace Function

`sys.settrace(fn)` calls a named function on each event.
```python
from sys import settrace

def my_tracer(frame, event, arg = None):
    # extracts frame code
    code = frame.f_code
  
    # extracts calling function name
    func_name = code.co_name
  
    # extracts the line number
    line_no = frame.f_lineno
  
    print(f"A {event} encountered in \
    {func_name}() at line number {line_no} ")
  
    return my_tracer

settrace(my_tracer)
```

## PDB Module
[pdb](https://docs.python.org/3/library/pdb.html) is a built-in module. Its `set_trace()` method can be used for debugging

## Breakpoint Function
Built into Python 3.7+

Pauses execution to allow for exploration
| Command  | Meaning                                                         |
| -------- | --------------------------------------------------------------- |
| h        | help                                                            |
| u / d    | up/down - Move running frame count one level                    |
| s        | step - step into, pausing at next instruction                   |
| n        | next - step over, pausing at next statement in current function |
| r        | return - continue until current function returns                |
| c        | continue - continue until next breakpoint                       |
| ll       | long list - print out source code for current instruction       |
| p [expr] | print value of expression                                       |

## code.interact

Drops you into the REPL at the point in the program where it occurs:
```python
import code

def brkpoint():
    print("BREAK!")
    code.interact(local=locals())
    print("Resuming...")

print("Hello, ")
brkpoint()
print("world!")
```

using `exit()` at the REPL will exit the program. Using CTRL-D (linux/OSX) or CTRL-Z (Windows) will resume execution.

`local=locals()` will pass the local namespace to the REPL. This could also be a dictionary or `globals()`, for instance.

## Hex Dumps

`bytes.hex()` provides a string with a hex dump of the bytes. A separator character can be provided.

```python
my_string = b'ascii'

# Print column headers with offset (00 01 02)
print(' '.join([str(n).zfill(2) for n in range(len(my_string))]))

# Print characters in string
print(my_string.hex(' '))

# 00 01 02 03 04
# 61 73 63 69 69
```

---
# See Also
[Python - sys.settrace() - GeeksforGeeks](https://www.geeksforgeeks.org/python-sys-settrace/)

