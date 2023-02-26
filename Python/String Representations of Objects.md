## repr vs. str
`__repr__` should return valid code which can recreate the object.
`__str__` is more informal and is meant for user consumption.

`str(obj)` dispatches to `obj.__str__()`, then `obj.__repr__()`.
`repr(obj)` calls `obj.__repr__()`

## format
Used by `str.format()` calls and f-strings

One-argument form should return a "common" representation, often just delegating to `__str__()`.

Optional second argument is format_spec, e.g. `>+20.11f`

