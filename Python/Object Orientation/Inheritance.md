Classes can inherit properties and methods from another parent class.

```toc
```

```python
class Vehicle:
	def drive(self):
		print("Driving...")

class Car(Vehicle):   # Inherits from Vehicle
	pass

car = Car()
car.drive()    # Driving...
```

A child class can choose to override a method in the parent class by defining another method of the same name.

## Overriding the Initializer
When you define an `__init__()` in a child class, it should call the base class' initializer as well. This can be done via `super().__init__()`.

## Tips when Overriding
When calling static methods from within a class method, but want to account for child classes that override it, call through `self` to pick up the overridden method, rather than calling through the class name.

When creating a static or class method that returns a new instance, accept `**kwargs`, so that you can pass through arguments to a child class initializer. On the overriding side, use `*` in the arg list to make the additional arguments keyword-only so they are passed in properly.

Overriding property getters is straightforward. Call the parent via `super` if needed.

For setters, use the decorator with the fully-qualified name: `@ClassName.propertyname.setter`. Calling `super().propertyname` as a setter doesn't work correctly. Use the fset alias `Classname.propertyname.fset()`. To avoid all the hassle of overriding setters directly, just have the base class setter call a regular method, and override that method in your child class.

## Multiple Inheritance
Classes can inherit from multiple base classes by specifying a comma-separated list:
```python
class Car(Vehicle, ConsumerProduct, Asset):
	pass
```

`__bases__` will contain a tuple of all the base types.

### Base Class Initializer
When no overridden initializer is given, a child class of multiple base classes will automatically call the initializer of the first listed base class and no others. `Car` above would only call `Vehicle.__init__()`.

### Method Resolution Order
Python stores an *inheritance graph* of parent classes, which can be found in `ClassName.__mro__`. This is a tuple of types that will be searched for method names. The first match found is the one that is called.

The inheritance graph is generated using the C3 algorithm, and always ensures that
- Subclasses come before base classes
- Base class order in class definition is preserved.

If a graph cannot be created that does not violate these constraints, Python throws an exception.

```python
class A: pass
class B(A): pass
class C(A): pass
class D(B, A, C): pass   # Will not compile
class D(B, C, A): pass   # Will compile
```
The situation above will not compile because:
- C must come before A (subclasses before base class) but 
- A must come before C (base class order in definition is preserved)

#### super() and MRO
When using super(), you get back a proxy object that resolves function calls using the MRO. 

The actual call to super() takes two arguments: the calling class, and the class of the object whose MRO to use. You can explicitly call `super()` this way but not clear when this would be useful.

The proxy object returned by super() searches the part of the MRO that appears AFTER the calling class.

When using super in a class method, super uses the MRO of the class itself since it has no calling object to refer to.


