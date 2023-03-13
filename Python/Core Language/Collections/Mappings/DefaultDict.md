
Extension of [[dict]] which allows a default function to provide values for missing keys.
The function is provided when the object is instantiated.

```python
from collections import defaultdict
  
def def_value():
    return "Not Present"
      
# Defining the dict
d = defaultdict(def_value)
d["a"] = 1
d["b"] = 2
  
print(d["a"])  # 1
print(d["b"])  # 2
print(d["c"])  # Not Present
```


The base [[dict]] type is aware of the `__missing__` function but does not implement it.
Subclass `dict` and provide a `__missing__` function to emulate this behavior.

