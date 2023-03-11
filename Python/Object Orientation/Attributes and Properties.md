
```toc
```

## Attributes

### Instance Attributes
- Defined within an instance method.
- Referenced as `self.attr_name` inside instance methods.
- Referenced as `obj.attr_name` from outside the class.
- Can enforce invariants, transform values, etc.

### Class Attributes
- Defined within the main body of the class declaration
- Shared among all classes
- Masked by creation/modification of an instance method with same name
- Referenced internally as `self.__class__.attr_name`
- Referenced externally as `class_name.attr_name`

### Properties
- Attributes which are accessed through methods ("getters" and "setters").
- May be backed by attributes or implemented as "virtual" attributes.
- When backed by attributes, name of attribute starts with underscore by convention.

#### Property Decorators

Implement a "getter" function:
- Same name as desired property
- Takes only `self` as argument
- Returns the value of the property (real or virtual)
- Decorated with `@property`

If property is to be assignable, implement the "setter" function
- Takes `self` and `value` as arguments
- Sets the value of the property to `value`.
- Decorated with `@propertyname.setter

> [!Example]- Example: Class with property decorators
> 
> ```python
> import math
> 
> class Circle:
> 
> 	def __init__(self, radius):
> 		self.radius = radius
> 	
> 	@property
> 	def circumference(self):
> 		return self.radius * 2 * math.pi
> 	
> 	@circumference.setter
> 	def circumference(self, value):
> 		self.radius = value / (2 * math.pi)
> 
> 	@property
> 	def area(self):
> 		return math.pi * (self.radius ** 2)
> 
> c = Circle(10)
> 
> print(f"r = {c.radius:.2f}, c = {c.circumference:.2f}, a = {c.area:.2f}")
> # r = 10.00, c = 62.83, a = 314.16
> 
> c.circumference = 17
> 
> print(f"r = {c.radius:.2f}, c = {c.circumference:.2f}, a = {c.area:.2f}")
> # r = 2.71, c = 17.00, a = 23.00
> ```

The `@property` decorator replaces the getter with a callable object and puts the original wrapped method into `propname.fget()`. When defining a setter, it maps the wrapped method to `propname.fset()`.


## Default Method

Normally these are accessed via builtin functions:
| Function                    | Delegates to                                                  |     |
| --------------------------- | ------------------------------------------------------------- | --- |
| `getattr(obj, name)`        | `obj.__getattribute__(name)`, then<br>`obj.__getattr__(name)` |     |
| `setattr(obj, name, value)` | `obj.__setattr__(name, value)`                                |     |
| `del(obj.name)`             | `obj.__delattr__(name)`                                                              |     |

At a low level, `__dict__` is a dict that lists names and values of object attributes. The default `__getattr__`, `__setattr__`, etc. methods use `__dict__` to access attributes.

`__getattribute__` does the following.
- Use [[#Slots|__slots__]] mechanism if in use.
- Use `vars(obj)[name]`
- Use `hasattr(cls, name)` and `getattr(cls, name)`
- Use `cls.__getattr__(obj, name)`
- raise `AttributeError` if all of these fail.

## Slots
Slots are a simple and automatic way to reduce the memory footprint and overhead of an object. This replaces `__dict__` with an indexed collection.

To use, define a class attribute `__slots__` as a tuple of attribute names, then use the object as normal.

Using `__slots__` limits you to only the attribute names provided. Referencing an attributed not listed in `__slots__` raises an `AttributeError`.

```python
class two_d_point:

	__slots__ = ('x', 'y')

	def __init__(self, x, y):
		self.x = x
		self.y = y
```


## Dynamic Attributes

Allows you to provide (additional) attributes that circumvent `__dict__` and `__slots__`.

```ad-warning
This may break debuggers and other introspective features that depend upon default behavior.
```

These can be used to:
- Transform attribute names or make the names dynamically assignable
- Alter how attributes are stored
- Implement virtual attributes

### Implementing
Override `__getattr__`, `__setattr__`, `__delattr__` with your lookup mechanism.
Leave __getattribute__ alone.

From outside object, `__getattribute__` is called first and handles "regular" attributes
Your `__getattr__` method will have a chance to provide any dynamic attributes.
Within the new `__getattr__` code, you cannot use `self.attrname` to retrieve attributes.

````ad-example
title: Vector object with dynamic attributes
collapse: true

Vectors are referenced as (x, y, z) or (p, q, r) or (x1, x2, x3) in mathematics.
This class allows the vector components to be assigned names dynamically.
```python
class Vector:
    """An n-dimensional vector."""

    def __init__(self, **components):
        private_components = { f"_{k}": v for k,v in components.items() }
        self.__dict__.update(private_components)

    def __repr__(self):
        return "{}({})".format(
            type(self).__name__,
            ", ".join(
                "{k}={v}".format(
                    k=k[1:],   # Slice removes underscore
                    v=v,
                ) for k, v in self.__dict__.items()
            )
        )
    
    # Intercept Attributes - override __getattr__ (not __getattribute__)
	# Transforms name, adding underscore to "private" attribute.
    def __getattr__(self, name):
        private_name = f"_{name}"
        try:
            return self.__dict__[private_name]
        except KeyError:
			# Re-raise lookup KeyError as AttributeError.
            raise AttributeError(f"{self!r} object has no attribute {name!r}")

	# We're immutable, so set/delattr are easy...

    def __setattr__(self, name, value):
        raise AttributeError(f"Can't set attribute {name!r}")

    def __delattr__(self, name):
        raise AttributeError(f"Can't delete attribute {name}")
```

Usage:
```python
v = Vector(p=10, q=-3, r=7)
print(v)
print(f"v.p is {v.p})
print(f"v.x is {v.x}) # Raises AttributeError
v.p = 11              # Raises AttributeError
del(v.p)              # Raises AttributeError
```
````

Note that it's a good idea to override `__repr__` to print out the dynamic attributes as well, especially if the attributes are assigned as part of the constructor.

---
# Sources
Pluralsight course [Core Python 3.9: Custom Attributes and Descriptors](https://app.pluralsight.com/library/courses/core-python-custom-attributes-descriptors)
