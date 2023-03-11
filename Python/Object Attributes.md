
```toc
```

## Default Method

Normally these are accessed via builtin functions:
| Function                    | Delegates to                                                  |     |
| --------------------------- | ------------------------------------------------------------- | --- |
| `getattr(obj, name)`        | `obj.__getattribute__(name)`, then<br>`obj.__getattr__(name)` |     |
| `setattr(obj, name, value)` | `obj.__setattr__(name, value)`                                |     |
| `del(obj.name)`             | `obj.__delattr__(name)`                                                              |     |

At a low level, `__dict__` is a dict that lists names and values of object attributes. The default `__getattr__`, `__setattr__`, etc. methods use `__dict__` to access attributes.


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





------


## Slots
Slots are a way of reducing the memory footprint of an object and increasing its efficiency.
The default method of storing attributes is bypassed, using an indexed collection instead of `__dict__`.

Using `__slots__` limits you to only those attribute names. Assigning an attribute not listed raises an `AttributeError`.

To use, define a class attribute, `__slots__`, as a tuple and proceed as normal.

```python
class geometric_point:

	__slots__ = ('x', 'y')

	def __init__(self, x, y):
		  self.x = x
		  self.y = y
```


## Dynamic Attributes

Dynamic attributes are those whose names are not fixed (e.g. a vector that can take coordinates as x and y or p and q). 

These can be used to:
- Transform attribute names or make the names dynamically assignable
- Alter how attributes are stored
- Implement virtual attributes

An example would be a mathematical vector class that can accept coordinates as (x, y), (p, q), or (x, y, z) just as easily.

> [!Prerequisite] Prerequisite: [[000 ToSort/OldOrg2/STEMpunk/Python/Working/Stuff/Object Attributes|How object attributes are normally stored]]

### Implementing Dynamic Attributes
Implement the following methods:
`__init__`: Takes in arguments, e.g. using `**kwargs` to specify both attribute names and values.
`__repr__`: Should use the argument names as they should be provided to the initializer.
`__getattr__`: Should intercept attempts to get attributes, and return the attribute value or raise `AttributeError` if invalid.
`__setattr__`: Should intercept attempts to set attributes, and either set them appropriately or raise `AttributeError` if improper.
`__delattr__`: Should intercept calls to delete the attribute

By overriding `__getattr__` and leaving `__getattribute__` alone, we can still retrieve "real" attributes with calls to `getattr(self, name)`.

### Overriding getattribute

If overriding `__getattribute__` you must avoid using the dot operator on `self` anywhere in the code that performs the override.
This can also have a effects on debugging tools and other introspective features.

`__getattribute__` does all of the following.
- Use [[slots]] mechanism if in use.
- Use `vars(obj)[name]`
- Use `hasattr(cls, name)` and `getattr(cls, name)`
- Use `cls.__getattr__(obj, name)`
- raise `AttributeError` if all of these fail.

> [!Example:] Example: [[DEDUPED/Python/Code Samples/vector_dynamic_attributes.py]], an immutable Vector class



#status/imported_vetme






----

## How Attributes are Handled

`obj.__dict__` contains the dictionary of attributes - can view, modify, and delete through here though this is low-level and not generally recommended.

Instead, the object implements `hasattr`, `getattr`, `setattr`, `delattr`, etc. for python and programs to access attributes indirectly.

When getting an attribute, `__getattribute__()` is called first. 
If `__getattribute__()` fails, `__getattr__()` is called for a second chance.



## Dynamic Attributes















----

Dynamic attributes are those whose names are not fixed (e.g. a vector that can take coordinates as x and y or p and q). 

These can be used to:
- Transform attribute names or make the names dynamically assignable
- Alter how attributes are stored
- Implement virtual attributes

An example would be a mathematical vector class that can accept coordinates as (x, y), (p, q), or (x, y, z) just as easily.

> [!Prerequisite] Prerequisite: [[000 ToSort/OldOrg2/STEMpunk/Python/Working/Stuff/Object Attributes|How object attributes are normally stored]]

## Implementing Dynamic Attributes
Implement the following methods:
`__init__`: Takes in arguments, e.g. using `**kwargs` to specify both attribute names and values.
`__repr__`: Should use the argument names as they should be provided to the initializer.
`__getattr__`: Should intercept attempts to get attributes, and return the attribute value or raise `AttributeError` if invalid.
`__setattr__`: Should intercept attempts to set attributes, and either set them appropriately or raise `AttributeError` if improper.
`__delattr__`: Should intercept calls to delete the attribute

By overriding `__getattr__` and leaving `__getattribute__` alone, we can still retrieve "real" attributes with calls to `getattr(self, name)`.

> [!Example:]- Example: An immutable Vector class
> 
> ```python
> class Vector:
>     """An n-dimensional vector."""
> 
>     def __init__(self, **components):
>         private_components = { f"_{k}": v for k,v in components.items() }
>         self.__dict__.update(private_components)
> 
>     def __repr__(self):
>         return "{}({})".format(
>             type(self).__name__,
>             ", ".join(
>                 "{k}={v}".format(
>                     k=k[1:],   # Slice removes underscore
>                     v=v,
>                 ) for k, v in self.__dict__.items()
>             )
>         )
>     
>     # Intercept Attributes - override __getattr__ (not __getattribute__)
> 	# Transforms name, adding underscore to "private" attribute.
>     def __getattr__(self, name):
>         private_name = f"_{name}"
>         try:
>             return self.__dict__[private_name]
>         except KeyError:
> 			# Re-raise lookup KeyError as AttributeError.
>             raise AttributeError(f"{self!r} object has no attribute {name!r}")
> 
> 	# We're immutable, so set/delattr are easy...
> 
>     def __setattr__(self, name, value):
>         raise AttributeError(f"Can't set attribute {name!r}")
> 
>     def __delattr__(self, name):
>         raise AttributeError(f"Can't delete attribute {name}")
> 
> 
> #### Usage:
> # v = Vector(p=10, q=-3, r=7)
> # print(v)
> # print(f"v.p is {v.p})
> # print(f"v.x is {v.x}) # Raises AttributeError
> # v.p = 11              # Raises AttributeError
> # del(v.p)              # Raises AttributeError
> ```
----
# Sources
Pluralsight course [Core Python 3.9: Custom Attributes and Descriptors](https://app.pluralsight.com/library/courses/core-python-custom-attributes-descriptors)






-----

## Attributes
`obj.__dict__` contains the dictionary of attributes - can view, modify, and delete attributes.

Should use `hasattr`, `getattr`, `setattr`, `delattr`, etc. instead in most cases

## Dynamic Attributes

### Initializer
`__init__` can take in values as `**kwargs` and assign them using `self.__dict__.update()`.
Transform name during update to add underscore if you are going to intercept their use.

### Strings Representation
Override `__repr__` with a method that enumerates and joins the attributes from `__dict__`.

### Intercepting attributes with getattr
`__getattr__` is invoked after failed attribute lookups and ==should be the method to overrride==.
`__getattribute__` is used before attribute lookups and called for ALL attribute access. Should not generally override this one.

Override `__getattr__(self, name)` to check for existence of attribute name in `self.__dict__`.
- If attribute does not exist, raise AttributeError
- If attribute does exist, return value (private attributes in dict can be obtained with `getattr(self, private_name)`).

### Intercepting calls to set attributes
Calling `setattr()` can create a new attribute that masks the private one (via `__getattribute__`).
`__setattr__` can be overridden to do the right thing (if immutable, just raise AttributeError).

### Intercepting deletion
Override `__delattr__(self, name)`. This might just be to raise `AttributeError`.
