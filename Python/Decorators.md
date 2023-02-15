## Using Decorators
Add the decorator (starting with `@`) to the line above the function declaration.
Multiple decorators are applied from last to first as if nested.

`````ad-example
```python
@decorator2
@decorator1
def do_stuff():
	code_block()
```
`````

## Implementing Function Decorators

### Decorating Functions with Functions
The decorator should take in a function reference as an argument, and return a new function.
The new function often wraps the original.

`````ad-example
Decorator:
```python
def trace(fn):
	"""prints the inputs and the outputs of the wrapped function call"""
	def print_call_info(*args, **kwargs):
		nonlocal fn
		print(f"args = {args}, kwargs = {kwargs}")
		result = fn(*args, **kwargs)
		print(f"result = {result}")
		return result
	return call_info
```
Consumer:
```python
@trace
def greeting(name):
	return f"Hello, {name}!"

greeting("Bob")
```
Output:
```
args = ('Bob',), kwargs = {}
result = Hello, Bob!
```
`````
