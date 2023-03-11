Anything that can be executed directly
- Functions
- Lambdas
- Classes (`__init__` is the called function)

Class instances can be made callable by implementing a `__call__` method.

`callable(obj)` will tell if an object *appears* to be callable, but false positives are possible.

````ad-example
title: Simple example: A callable object

```python
class Foo:
	def __call__(self):
		print("Hello, world!")

x = Foo()
if (callable(x)):
	x()      # Hello, world!
```
````

## Implementing
Inherit from abstract class `collections.abc.Callable` and override `__call__` method.

