
`collections.namedtuple` is a factory that produces subclasses of tuple with field names and a class name.

```python
from collections import namedtuple

# requires 2 parameters: class name and field names (space-delimited or iterable)
City = namedtuple('City', 'name country population coordinates')  

# Data passed in positional arguments
tokyo = City('Tokyo', 'JP', 36.933, (35.689722, 139.691667))  

print(tokyo)
# City(name='Tokyo', country='JP', population=36.933, coordinates=(35.689722, 139.691667))

# Fields accessed by name or position
print(tokyo.population)  # 36.933
print(tokyo.coordinates) # (35.689722, 139.691667)
print(tokyo[1])          # JP

print(City._fields)  # or tokyo._fields
# ('name', 'country', 'population', 'coordinates')

print(tokyo._asdict) # {'name': 'Tokyo', 'country': 'JP', ... }

# Making a new City from an iterable:
delhi_data = ('Delhi NCR', 'IN', 21.935, LatLong(28.613889, 77.208889))
delhi = City._make(delhi_data)  
```

----
# Source
*Fluent Python*, Luciano Ramalho, 2015