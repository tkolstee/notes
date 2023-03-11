Lightweight classes used only to store structured data

## Declaring
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


## Parameters
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

### init, repr, and eq
If these are set, their corresponding functions are created automatically.
If these functions are already defined, this will override automatic creation

`__init__()`
Accepts default members of the class. If `kw_only` is set, `__init__()` will only accept keyword arugments.

`__eq__()` Default method will return true if class and all field values match. It only compares instances of the same type.


### order
If this parameter is set, the `lt`, `le`, `gt`, and `ge` methods will be created.
By default they compare the two instances as tuples of the field values in order.
Raises `ValueError` if `eq` not set, or `TypeError` if one of the methods is already defined.

### frozen
Declares the class as immutable. Assigning to fields will create an exception.
Raises `TypeError` if `__setattr__` or `__delattr__` are defined.

### match_args
If True, the `__match_args__` tuple is created from the initializer call.

### slots
If true, the `__slots__` attribute will be generated and a new class returned instead of th original one. Raises `TypeError` if `__slots__` is already defined.

### unsafe_hash
If true, forces the creation of a `__hash__` method.
If false:
- A `__hash__` method is generated if `eq` and `frozen` are both set.
- If `eq` is true but `frozen` is false, `__hash__` will return `None` by default.
- If `eq` is false, `__hash__` will be left untouched.

## Invariants
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

