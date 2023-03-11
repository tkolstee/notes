
```toc
```


## Variables

### Naming
Contain letters, numbers, and underscores
Cannot start with a number or match a reserved word
By convention should use snake_case and be all lower case
Names beginning with an underscore are reserved for specific purposes.

### Typing
Variables are dynamically typed - not restricted to only hold a given type
All variables are object references, and every type in Python is a class.

### Declaration and Assignment
Are not explicitly declared, created on assignment.
Using an uninitialized variable raises `NameError`.

```python
x = 5

# Multiple assignment (tuple unpacking)
x, y = 5, 4

(a, (b, (c, d))) = (4, (3, (2, 1)))

# Unassign/remove variable
del x

# Import variable into local scope
global x
nonlocal y
```

## Scoping
- LEGB Order is used to resolve variables:
	- **L**ocal function
	- **E**nclosing functions
	- **G**lobal variables
	- **B**uiltin variables
- Created and bound on assignment
- Each function body (stack frame) is a local scope
- Unresolved variable names cause a `NameError` to be raised
- Variables may be brought into local scope for modification with `global` or `nonlocal` keywords
- `del varname` will delete a variable from the mapping

When a variable name is used, it is searched in LEGB order and the first "hit" is used. If no matches are made a `NameError` is raised. This means a "more local" scope can mask a higher-level variable. 

To import a variable from global scope, use the `global` keyword. Use `nonlocal` for an enclosing scope. This allows you to modify the original variable instead of masking it.

If a variable is referenced before being reassigned (imported from outer scope and then assigned/created locally) a `UnboundLocalError` is raised. If it is reassigned and then later imported with `global` or `nonlocal` keywords, a `SyntaxError` is raised.

## Constants
No official constant type exists in Python.
Convention is to use variables in SCREAMING_SNAKE_CASE.
