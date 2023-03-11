


## How Attributes are Handled

`obj.__dict__` contains the dictionary of attributes - can view, modify, and delete through here though this is low-level and not generally recommended.

Instead, the object implements `hasattr`, `getattr`, `setattr`, `delattr`, etc. for python and programs to access attributes indirectly.

When getting an attribute, `__getattribute__()` is called first. 
If `__getattribute__()` fails, `__getattr__()` is called for a second chance.



## Dynamic Attributes






### Initializer
`__init__` can take in values as **kw