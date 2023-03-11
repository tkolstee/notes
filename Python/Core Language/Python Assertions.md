```python
assert condition
assert condition, message
```

Raises `AssertionError` if condition evaluates to `False`.

Can negatively impact performance.

Disable assertions with `python -O`.