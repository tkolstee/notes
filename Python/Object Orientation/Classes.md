
```toc
```
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


## Data Classes
Lightweight classes used only to store structured data

### Declaring
```python
from dataclasses import dataclass


""" Declaration """
@dataclass
class Location:
	name: str
	latitude: float
	longitude: float
	in_EU: bool = True

""" Usage """
paris = Location("Paris", +45.8566, +2.3522)
print(paris)

# Location(name='Paris', latitude=45.8566, longitude=2.3522, in_EU=True)
```

### Parameters
```python
@dataclass(
	init        = True,       # creates __init__ automatically
	kw_only     = False,      # init uses only keyword args
	repr        = True,       # create __repr__ automatically
	eq          = True,       # create __eq__ automatically
	order       = False,      # see below
	unsafe_hash = False,      # see below
	frozen      = False       # Class is immutable
)
```

#### init, repr, and eq
If these are set, their corresponding functions are created automatically.
If these functions are already defined, this will override automatic creation

`__init__()`
Accepts default members of the class. If `kw_only` is set, `__init__()` will only accept keyword arugments.

`__eq__()` Default method will return true if class and all field values match. It only compares instances of the same type.

#### order
If this parameter is set, the `lt`, `le`, `gt`, and `ge` methods will be created.
By default they compare the two instances as tuples of the field values in order.
Raises `ValueError` if `eq` not set, or `TypeError` if one of the methods is already defined.

#### frozen
Declares the class as immutable. Assigning to fields will create an exception.
Raises `TypeError` if `__setattr__` or `__delattr__` are defined.

#### match_args
If True, the `__match_args__` tuple is created from the initializer call.

#### slots
If true, the `__slots__` attribute will be generated and a new class returned instead of th original one. Raises `TypeError` if `__slots__` is already defined.

#### unsafe_hash
If true, forces the creation of a `__hash__` method.
If false:
- A `__hash__` method is generated if `eq` and `frozen` are both set.
- If `eq` is true but `frozen` is false, `__hash__` will return `None` by default.
- If `eq` is false, `__hash__` will be left untouched.

### Invariants
To enforce invariants, create `__post_init__(self)` which will be called by the generated `__init__()`.

```python
@dataclass
class MyDataClass:
	fred: int
	jim: int
	sheila: int

	def __post_init__(self):
		if self.fred < 0:
			raise ValueError
```

For immutable classes this may be enough.
Overriding setters is problematic, so if you need to create a mutable class, you will likely want to upgrade to a full "regular" class.

