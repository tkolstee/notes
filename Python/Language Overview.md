
```toc
```

## Syntax and Statements
````ad-example
title: Assertions
collapse: true
Dies with AssertionError and message if condition is False
```python
assert condition, message
```
````

````ad-example
title: Comments
collapse: true
Inline comment
```python
# This is an inline comment
x = 4   # so is this
```

Multiline comment
```python
"""
this is a comment.
actually it's a bare string literal,
since python doesn't support real
multiline comments
"""
```
````

````ad-example
title: Conditional Statements
collapse: true

if...elif...else
```python
if cond:
	action
elif cond:
	action
else:
	action
```

Compact if...else
```python
action1 if cond else action2
```

Emulating switch statements
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

Short-circuit evaluation
```python
if hasattr(mydict, 'foo') and mydict['foo'] == 'bar':
	pass

attrval = mydict.get('foo') or 'defaultvalue'
```

````

````ad-example
title: Looping
collapse: true

While inside loop:
```python
break    # exits the loop, do not execute else
continue # restart loop at top, including conditional
```

while...else
```python
while cond:
	action
else:  
	# nobreak
	action
```

for...in
```python
for value in iterable:
	action
else:
	# nobreak
	action   
```
````

## Data Types

### Boolean
`bool`
`True` or `False` only. 
Numeric 0 and empty collections are falsey, all else are truthy
`True` and `False` are single instances of class `bool`

### Numeric
`int`, `float`, and `complex`

### Collections
| Type  | Literal                    | Comprehension                 |     |
| ----- | -------------------------- | ----------------------------- | --- |
| list  | `[ a, b, c ]`              | `[ i*2 for i in range(10) ]`  |     |
| dict  | `{'a': a, 'b': b} `        | `{i:i*2 for i in range(10) }` |     |
| set   | `{a, b, c}`                | `(i*2 for i in range(10)`     |     |
| tuple | `(a, b, c)`                | none                          |     |
| range | `range(start, stop, step)` | none                          |     |
| str   | "This is a string"         | none                          |     |
| bytes | b"This is a string"        | none                              |     |


## Variables
Scoping: LEGB
- Local function
- Enclosing functions
- Global
- Builtin

`del x` - Remove variable from namespace
`global x` - Import variable from global scope into local function
`nonlocal x` - Import from enclosing scope into local function

`type(x)` - Get class that x is an instance of
`isinstance(x, Classname)` - True if x inherits from the given class
`issubclass(ClassA, ClassB)` - True if A is or inherits from B

## Operators
Arithmetic:  `+ - * / % // **`
Assignment: `= += -= *= /= %= //= **=`
Comparison: `== != < > <= >=`
Sign: `+ -`
Bitwise: `| ^ & << >>`
Bitwise Assignment: `&= |= ^= >>= <<=`
Identity: `is`, `is not`
Logical: `and`, `or`, `not`
Membership: `in`, `not in`

## Functions
Functions: `def function_name(arg1, arg2=def):`
- `/` - all past arguments are positional-only
- `*` - all future arguments are keyword-only
- `*args` and `**kwargs` swallow positional as list, keywords as dict

Lambdas: `lambda x, y: x+y`

