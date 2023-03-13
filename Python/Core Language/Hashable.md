An object is hashable if it has a hash value which never changes during its lifetime.
This value is provided by implementing the `__hash__()` method.
Hashable objects which compare equal must have the same hash value.

Atomic immutable types (`str`, `bytes`, numeric types) are hashable.
`frozenset` objects are also hashable because its elements must be hashable.
`tuple` is hashable only if all items are hashable.

User-defined types are hashable by default because their hash value is their `id()` and they all compare not equal. If an object implements a custom `__eq__` that uses its internal state, it may be hashable only if all its attributes are immutable.

----
# Sources
[Glossary — Python 3.11.2 documentation](https://docs.python.org/3/glossary.html#term-hashable)
*Fluent Python*, Luciano Ramalho, 2015
