Ignored by the interpreter and used to annotate code.

## Single-Line Comments
Single-line comments start with a `#` character that isn't part of a quoted string.
They end at the end of the physical line and may not be continued with line joining.

Other Python statements or expressions may come before the comment on the same line.

```python
# This is a single-line comment.

print("Hello, world!")  # This is also a single-line comment.

# '#' inside the password string below doesn't start a comment.
password = 'abc#123' 
```

## Multiple-Line Comments
Multiple-line comments don't officially exist in Python.
The convention is to use multi-line string literals delimited with triple quotes (`'''` or `"""`).
```python
"""
This is a string literal
but functions as a comment
that spans multiple lines
"""
```
