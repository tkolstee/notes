| Group                                     | Methods                                                                                                         |
| ----------------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| String/bytes representation               | `__repr__`, `__str__`, `__format__`, `__bytes__`                                                                |
|                                           |                                                                                                                 |
| Conversion to number                      | `__abs__`, `__bool__`, `__complex__`, `__int__`, `__float__`, `__hash__`, `__index__`                           |
| Emulating collections                     | `__len__`, `__getitem__`, `__setitem__`, `__delitem__`, `__contains__`                                          |
| Iteration                                 | `__iter__`, `__reversed__`, `__next__`                                                                          |
| Emulating callables                       | `__call__`                                                                                                      |
| Context management                        | `__enter__`, `__exit__`                                                                                         |
| Instance creation and destruction         | `__new__`, `__init__`, `__del__`                                                                                |
| Attribute management                      | `__getattr__`, `__getattribute__`, `__setattr__`, `__delattr__`, `__dir__`                                      |
| Attribute descriptors                     | `__get__`, `__set__`, `__delete__`                                                                              |
| Class services                            | `__prepare__`, `__instancecheck__`, `__subclasscheck__`                                                         |
| Unary numeric operators                   | `__neg__`, `__pos__`, `__abs__`                                                                                 |
| Rich comparison operators                 | `__lt__`, `__le__`, `__eq__`, `__ne__`, `__gt__`, `__ge__`                                                      |
| Arithmetic operators                      | `__add__`, `__sub__`, `__mul__`, `__truediv__`, `__floordiv__`, `__mod__`, `__divmod__`, `__pow__`, `__round__` |
| Reversed arithmetic operators             | `__radd__`, `__rsub__`, `__rmul__`, `__rtruediv__`, `__rfloordiv__`, `__rmod__`, `__rdivmod__`, `__rpow__`      |
| Augmented assignment arithmetic operators | `__iadd__`, `__isub__`, `__imul__`, `__itruediv__`, `__ifloordiv__`, `__imod__`, `__ipow__`                     |
| Bitwise operators                         | `__invert__`, `__lshift__`, `__rshift__`, `__and__`, `__or__`, `__xor__`                                        |
| Reversed bitwise operators                | `__rlshift__`, `__rrshift__`, `__rand__`, `__rxor__`, `__ror__`                                                 |
| Augmented assignment bitwise operators    | `__ilshift__`, `__irshift__`, `__iand__`, `__ixor__`, `__ior__`                                                 |


----
# Source
*Fluent Python*, Luciano Ramalho