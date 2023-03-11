
## if...elif...else
```python
if cond:
	action
elif cond:
	action
else:
	action
```

### Compact if...else
```python
action1 if cond else action2
```

## Emulating switch statements
```python
# Use mapping of callables
locations = {
	(0, 0): lambda: print("You are at the start"),
	(0, 1): lambda: print("You are in the woods"),
	...
}
actions = {
	"E": lambda: position=(position.x + 1, position.y),
	"N": lambda: position=(position.x, position.y + 1),
	...
}
"""
You can use a `try` block to call the mapped function, and an `except KeyError` to catch unmapped values like with a switch 'else' clause.
"""
```

## Short-circuit evaluation
```python
if hasattr(mydict, 'foo') and mydict['foo'] == 'bar':
	pass

attrval = mydict.get('foo') or 'defaultvalue'
```
