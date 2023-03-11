

## Types
Python objects have `__class__` and `__name__` attributes.

`type(x)` returns the type of x as a type object.
`issubclass(x: type, y: type)` reports if `x` is a subclass of `y`.
`isinstance(x: object, y: type)` reports if `x` is an instance or descendant of  `y`.

`issubclass` and `isinstance` can take a type or a tuple of types in the second argument.
The statement is true if the first argument matches ANY of the second argument's types.

## Objects
`dir(x: object)` returns all the attributes and methods of `x` as a list of strings.
`getattr(x: object, attrname: str)` returns the attribute named from the object.
`callable(x: object)` determines if the object is callable.
`hasattr(x: object, attrname: str)` indicates whether object has attribute

## Scopes
`globals()` - dict of symbols in global scope
`locals()` - dict of symbols in local scope

## Inspect module
`inspect.ismodule(x: object)` - Whether x is a module
`inspect.getmembers(x: object)` - Everything in module namespace including builtins.
`inspect.getmembers(x: object, inspect.isclass)` - Filter for classes
`inspect.getmembers(x: object, inspect.isfunction)` - Filter for functions
`inspect.signature(x: function)` - Signature for function x
	`signature.parameters` - Dict of parameters to function.
	Functions implemented in C don't have the right metadata.

## Type Annotations
`sig.parameters[paramname].annotation` - type based on type annotations in fn declaration
`sig.return_annotation` - Annotation of function return value
These are also available under `__annotations__`.

## Get Attributes and Methods
```python
attr_names = set(dir(obj))
method_names = set(
		filter(
			lambda attr_name: callable(getattr(obj, attr_name)),
			attr_names
		)
)
assert method_names <= attr_names            # Check if subset
attr_names = all_attr_names - method_names   # All but methods
```
