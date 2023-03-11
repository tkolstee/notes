Anything that can be executed directly
- Functions
- Lambdas
- Classes (`__init__` is the called function)

Class instances can be made callable by implementing a `__call__` method.

`callable(obj)` will tell if an object *appears* to be callable, but false positives are possible.

You should also Inherit from abstract class `collections.abc.Callable`.  This will mark our intention to make the object callable, and raise a TypeError if the `__call__` method is not overridden.

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


## Object Factories