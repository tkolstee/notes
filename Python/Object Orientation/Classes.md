
## Minimal Example

```python
class MyClass:   # Class Declaration
	pass

x = MyClass()    # Instantiate new class
print(type(x))   # <class '__main__.MyClass'>
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

## Methods
Methods are functions defined within a class definition.

| Method Type | Arguments    | Called via            | Decorator       | Access instance state | Access class state   |
| ----------- | ------------ | --------------------- | --------------- | --------------------- | -------------------- |
| Instance    | `self, args` | `instance.name(args)` | none            | via `self`            | via `self.__class__` |
| Class       | `cls, args`  | `class.name(args)`    | `@classmethod`  | none                  | via `cls`            |
| Static      | `args`       | `class.name(args)`    | `@staticmethod` | none                  | none                     |

Class methods are often used for factories whereas static methods are often for utility methods.

### Initializers
Named `__init__`, and takes `self` as a first argument.
No need to call `return`, as the new object is returned automatically.
Should call `super().__init__()` when inheriting and overriding.

