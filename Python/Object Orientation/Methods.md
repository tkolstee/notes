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
