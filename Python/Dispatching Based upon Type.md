
```toc
```

## Single Dispatch and Functions
Functions can't be overloaded with different argument types because of dynamic typing in Python. 

Mappings with type and introspection are fragile ways of doing this. Python 3.4 introduced a `@singledispatch` decorator from functools to implement generics.

One function is marked as `@singledispatch`, and other functions are passed through a decorator factory `register`. The function names don't matter as they are only called by the dispatcher, so we use `_`.

````ad-example
title: Using singledispatch
collapse: true
```python
from functools import singledispatch

@singledispatch
def draw(shape):
	# Called if a better match is not found.
	raise TypeError(f"Can't draw shape {shape!r}!")

@draw.register(Rectangle):  # Decorator factory
def _(rect):
	pass # ...

@draw.register(Circle)
def _(circle):
	pass # ...

@draw.register(Polygon)
def _(polygon):
	pass # ...

for s in shape:
	draw(s)
```
````

## Single Dispatch and Object Methods
Object methods are more tricky. We dan't define the singledispatch method within the class definition, because we dispatch based upon the first argument and here the argument is `self`.

If we move the dispatched function to global scope, we can call it from a method inside the class. The dispatched argument type will need to be first, and the other argument called with `self`.

````ad-example
title: Example: singledispatch and object methods
collapse: true
```python
class Rectangle:
	# ...
	def intersects(self, shape):
		return intersects_with_rectangle(shape, self)

@singledispatch
def intersects_with_rectanble(shape, rectangle):
	raise TypeError(f"Cannot intersect with {type(shape)}")

@intersects_with_rectangle.register(Circle):
def _(shape, rectangle):
	pass # ...

# Other handlers follow for other shapes...
```
````
