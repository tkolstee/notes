---
alias: [ "tuple unpacking" ]
---
Also called *tuple unpacking* but not just useful for tuples

```toc
```

## Unpacking into multiple variables
```python
coords = (33.9425, -118.408056)
lat, long = coords   # lat=coords[0]; long=coords[1]

b, a = a, b          # Swap without temporary variable
```

## Capturing Multiple Values with `*`
`*` will capture any number of variables, is greedy, and can only be used once in the expression to avoid ambiguity.
```python
first, second, *rest = range(5)  # 0, 1, [2, 3, 4]
first, *middle, last = range(5)  # 0, [1, 2, 3], 4
first, *middle, last = range(2)  # 0, [], 1
```

## Unpacking in Function Calls
```python
args = (20, 8)
quotient, remainder = divmod(*args)   # Equiv to divmod(20, 8)
```

## Discarding Extra Values
Convention is to use `_` as a dummy variable.
```ad-warning
Do not use `_` in internationalized code, as `_` is a common alias for gettext.gettext.
```

```python
_, filename = os.path.split('/home/tony/file.txt')  # Splits into path and filename.
```

## Unpacking Nested Structures

```python
metro_areas = [
	('Tokyo', 'JP', 36.933, (35.689722, 136.691667)),
	('Delhi NCR', 'IN', 21.935, (28.613889, 77.208889)),
    ('Mexico City', 'MX', 20.142, (19.433333, -99.133333)),
    ('New York-Newark', 'US', 20.104, (40.808611, -74.020386)),
    ('Sao Paulo', 'BR', 19.649, (-23.547778, -46.635833)),
]
print('{:15} | {:^9} | {:^9}'.format('', 'lat.', 'long.'))
fmt = '{:15} | {:9.4f} | {:9.4f}'
for name, cc, pop, (latitude, longitude) in metro_areas:
    if longitude <= 0:
        print(fmt.format(name, latitude, longitude))
```
For loop arguments unpack outer (metro_areas), city records, and nested lat/long pair all in one.
`if longitude <=0` limits to Western hemisphere

```output
                |   lat.    |   long.
Mexico City     |   19.4333 |  -99.1333
New York-Newark |   40.8086 |  -74.0204
Sao Paulo       |  -23.5478 |  -46.6358
```

