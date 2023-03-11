
## Calling Functions

```python
function_name()

# Positional Parameters
function_name('x')
function_name('x', 'y')

# Keyword Parameters
function_name(param2='x', param1='y')

# Can be mixed - list positional first
function_name('x', param2='y')

# Use * to unpack a list to fill several positional args
get_args(*my_list)

# Use ** to unpack a dict of keyword args
get_args(**my_kwargs)
```

### Passing Additional Parameters
In a function call, additional parameters can be taken in through a list or dict.

`*args` unpacks an iterable, in order, into positional parameters in place.
`**kwargs` unpacks a dictionary into named parameters, (keyword=value).


## Defining Functions
```python
def function_name():
	pass
```
`def` is executed immediately as a statement. The function is not available before definition and can be redefined at any time.

### Parameters
```python
def function_name(param1, param2=default_value)
	pass

# / means all arguments before it are positional-only
# * means all arguments after it are keyword-only
def plot_point(x, y, /, *, color=blue, size=1)
	pass

# *args    consumes all extra positional args as a list
# **kwargs consumes all extra keyword args as a dict
def get_args(x, y, *args, **kwargs):
	print(f"(x, y) is ({x}, {y})")
	print(f"positional: {', '.join(args)}")
	for k, v in kwargs.items():
		print(f"keyword argument {k}={v}")
```

#### Default Values
Defaults to parameters can be supplied in the declaration as `param=def_value`.
Parameters without defaults are mandatory, those with defaults are optional.
Mandatory parameters must be listed before optional parameters in the declaration.

#### Positional vs. Named
By default, parameters can be supplied positionally OR by name.
When using both in a function call, positional parameters must come before named parameters.

In the parameter list of a declaration:
`*` indicates that all arguments afterward are named-only
`/` indicates that all arguments before are positional-only

#### Consuming Additional Parameters
In a function declaration, additional unspecified parameters can be collected.
`*args` consumes all remaining positional parameters into a list variable called `args`.
`**kwargs` consumes uncaught named parameters into a dictionary (keyword=value).

### Return Values
```python
return      # Returns from function with None
return val  # Returns with specific value
```
Without a return call, value of last statement executed is returned.

Lambdas are anonymous functions which can be assigned to a variable or used in-place.

They usually contain an expression which is then used as the return value of the function.

## Lambdas
```python
# Takes one value, returns its square
lambda x: x**2

# Takes two values, returns true if absolute value is equal.
lambda x, y: abs(x) == abs(y) 
```

### Uses
#### Mapping and Filtering Collections
They may be used to perform an operation over all items in a collection with map and filter:
```python
data = [ 1, 2, 3, 4, 5 ]
squares = list(map( lambda x: x**2, data ))         # [1, 4, 9, 16, 25]
only_odds = list(filter(lambda x: x%2 != 0, data))  # [1, 3, 5]
```

#### Passing a Function to Another Function
 `sorted` doesn't know how to compare arbitrary programmer-defined objects . However, the sorted function takes a lambda that can return a value `sorted` knows how to compare. In this case it's a tuple of author and title extracted from an object representing a book.
```python
library = sorted(books, key=lambda x: (x.author, x.title))
```

