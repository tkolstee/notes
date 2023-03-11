Anything that can be executed directly
- Functions
- Lambdas
- Classes (`__init__` is the called function)

Class instances can be made callable by implementing a `__call__` method.

`callable(obj)` will tell if an object *appears* to be callable, but false positives are possible.

You should also Inherit from abstract class `collections.abc.Callable`.  This will mark our intention to make the object callable, and raise a TypeError if the `__call__` method is not overridden.

```python
import collections.abc

class Foo(collections.abc.Callable):
    def __call__(self):
        print("Hello, world!")

x = Foo()
if callable(x):
    x()
else:
    print("Not callable.")
```

## Object Factories
Callable objects can be factories that create and return other objects or values.


```python
import collections.abc

class Seq_Factory(collections.abc.Callable):
	""" Returns a list or tuple (if immutable) of objects passed in """
	
	def __call__(self, *args, immutable=False, **kwargs):
		return tuple(*args, **kwargs) if immutable else list(*args, **kwargs)

seq = Seq_Factory()                 # Creating an instance of the factory class
l = seq([1, 2, 3])                  # Calling the instance to get a list
t = seq([1, 3, 3], immutable=True)  # Calling the instance to get a tuple
```

