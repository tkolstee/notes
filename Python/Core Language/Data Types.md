
```toc
```

## Detecting Types and Classes

| Function                        | Purpose                                                                                                                                            |
| ------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------- |
| `type(x)`                       | Returns type of object                                                                                                                             |
| `isinstance(x, sometype)`       | True if x is an instance of the given type^[or if instance inherits from that type] |
| `isinstance(x, [type1, type2])` | True if x is an instance of ANY of the given types.                                                                                                                                                   |
| `issubclass(typeA, typeB)`      | True if A descends from B                                                                                                                          |

## Type Annotations
Type annotations are specified in [PEP 484](https://peps.python.org/pep-0484/) and [PEP 526](https://peps.python.org/pep-0526/)

They are basically treated like comments to the compiler, but tools like 
[MyPy](https://mypy.readthedocs.io/en/stable/) can be used to statically analyze the code for violations. 

```python
def greeting(name: str = "human") -> str:
	return 'Hello, ' + name
```

A more complex example:
```python
from typing import TypeVar, Iterable, Tuple

T = TypeVar('T', int, float, complex)
Vector = Iterable[Tuple[T, T]]

def inproduct(v: Vector[T]) -> T:
  return sum(x*y for x, y in v)
  
def dilate(v: Vector[T], scale: T) -> Vector[T]
  return((x*scale, y*scale) for x, y in v)

vec = [] # type: Vector[float]
```


## Scalar Types

### Boolean
`bool`
`True` or `False` only. 
Numeric 0 and empty collections are falsey, all else are truthy
`True` and `False` are single instances of class `bool`

### Numeric
`int`, `float`, and `complex`

## Collections
| Type  | Literal                    | Comprehension                 |     |
| ----- | -------------------------- | ----------------------------- | --- |
| list  | `[ a, b, c ]`              | `[ i*2 for i in range(10) ]`  |     |
| dict  | `{'a': a, 'b': b} `        | `{i:i*2 for i in range(10) }` |     |
| set   | `{a, b, c}`                | `(i*2 for i in range(10))`     |     |
| tuple | `(a, b, c)`                | none                          |     |
| range | `range(start, stop, step)` | none                          |     |
| str   | "This is a string"         | none                          |     |
| bytes | b"This is a string"        | none                              |     |
