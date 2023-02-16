```toc
```

## Generator Functions

Can be implemented by using the `yield` keyword within a function.
The function will return an object of class `generator`.
`generator` is iterable (implements `__next__()` and  `StopIteration`)
Each item is evaluated lazily. The function is run until the `yield` statement and returns the value.

`````ad-example
```python
def gen123():
	""" Generates the numbers 1-3 """
	for i in range(1, 4):
		yield i
```
`````

A generator does not have to be finite - just don't try to coalesce it to a list.
`````ad-example
```python
def gen_even_numbers():
	nextnum = 0
	while True:
		nextnum += 2
		yield nextnum
```
`````

## Generator Expressions
These are comprehensions that yield generators.

`````ad-example
```python
(expr(item) for item in iterable)

# Generate the first 100M squares, returns instantly
(x*x for x in range(1, 100_000_001))

# Sum of first 100M squares, returns in about 13s for me.
sum(x*x for x in range(1, 100_000_001))
```
`````

## Chaining Multiple Generators
When generators take a parameter as input and act as a filter, they can be chained together:

`````ad-example
```python
def first_three(x):
	count = 0
	for i in x:
		if count > 2:
			break
		yield i
		count += 1

def add_one(x):
	for i in x:
		yield i+1

def distinct_items(x):
	for i in set(x):
		yield i

mylist = [ 1, 2, 2, 1, 3, 4, 5, 4, 6 ]
x = list( first_three( distinct_items( add_one ( mylist ) ) ) )
```
result: `[ 2, 3, 4 ]`

`````

