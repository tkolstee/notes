
Comprehensions are quick ways of generating a collection from another iterable object.

## By Type
```python
[ i*2 for i in range(10) ]     # list
{ i: i*2 for i in range(10) }  # dict
{ i*2 for i in range(10) }     # set
( i for i in range(10) )       # generator
```

## Conditionals
```python
[ expr(x) for x in collection if cond ]
[ expr(x) if cond else expr(x) for x in collection ]
```

```python
[ x for x in range(10) if x%2==0 ]            # [0, 2, 4, 6, 8]
[ x if x%2==0 else 'odd' for x in range(5) ]  # [0, 'odd', 2, 'odd', 4]
```


## Multiple Inputs
```python
[ (x, y) for x in range(5) for y in range(5) ]
```

Note that y loop is the "inner" loop:
`[(0, 0), (0, 1), ..., (0, 4), (1, 0), (1, 1), ... (4, 4)]`

```python
[ (x, y) for x in range(10) for y in range(x) ]
# (1, 0),
# (2, 0), (2, 1),
# (3, 0), (3, 1), (3, 2),
# ... (9, 8)
```

## Multiple Conditionals
```python
[ expr(x, y) 
   for x in coll1 if cond1 
   for y in coll2 if cond2
]

# Equivalent to
values = []
for x in coll1:
  if cond1:
    for y in coll2:
      if cond2:
        values.append(expr(x, y))
```

## Nested Comprehensions
Yo dawg, we heard you like lists so we put a comprehension in your comprehension so you can list your lists.
```python
vals = [ [y*3 for y in range(x)] for x in range(10) ]

# Equivalent:
outer=[]
for x in range(10):
	inner = []
	for y in range(x):
		inner.append(y*3)
	outer.append(inner)

# Output:
vals = [ [], [0], [0, 3], [0, 3, 6], [0, 3, 6, 9], ...., [0, 3, 6, 9, ..., 24] ]
```


```python
[ [ expr(x, y) for y in coll1 ] for x in coll2 ]

# Equivalent to:
outer = []
for x in coll2:
  inner = []
  for y in coll1:
    inner.append(expr(x, y))
  outer.append(inner)
```
