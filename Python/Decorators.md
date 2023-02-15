```toc
```

## Using Decorators
Add the decorator (starting with `@`) to the line above the function declaration.
Multiple decorators are applied from last to first as if nested.

`````ad-example
```python
@decorator2
@decorator1
def do_stuff():
	code_block()
```
`````

## Decorating Functions

### Decorating Functions with Functions
The decorator should take in a function reference as an argument, and return a new function.
The new function often wraps the original.

`````ad-example
collapse: true
Decorator:
```python
def trace(fn):
	"""prints the inputs and the outputs of the wrapped function call"""
	def print_call_info(*args, **kwargs):
		nonlocal fn
		print(f"args = {args}, kwargs = {kwargs}")
		result = fn(*args, **kwargs)
		print(f"result = {result}")
		return result
	return call_info
```
Consumer:
```python
@trace
def greeting(name):
	return f"Hello, {name}!"

greeting("Bob")
```
Output:
```
args = ('Bob',), kwargs = {}
result = Hello, Bob!
```
`````

### Decorating Functions with Classes
A callable class (one that implements `__call__`) can be used as a decorator as well.
The class can store persistent data and implement other methods.
Note that each wrapped function gets its own distinct instance and count.

`````ad-example
collapse: true
Class Decorator:
```python
class CallCount:
	""" 
		Counts the number of times the wrapped function is called. 
		Count is accessible using the count property on the wrapped function.
	"""
	def __init__(self, fn):
		self.fn = fn
		self.count = 0
	def __call__(self, *args, **kwargs):
		self.count += 1
		return self.fn(*args, **kwargs})
```
Consumer:
```python
@CallCount
def foo(str): return str

@CallCount
def bar(str): return str

for i in range(10):
	foo(str(i))
	if (i%2 == 0): bar(str(i))

print(
	f"foo was called {foo.count} times " +
	f"and bar was called {bar.count} times."
)
```
Output:
```
foo was called 10 times and bar was called 5 times.
```
`````

### Decorating Functions with Instances of Classes
Instead of decorating a function with a raw class, a function can be decorated with a particular *instance* of a class which is callable. 

Instead of getting a unique instance of the class, all wrapped functions share the same class instance, so in this case tracing can be set on or off for all wrapped functions at once.

`````ad-example
collapse: true
Decorator:
```python
class Trace:
	"""
		Prints parameters and return value of function.
		Tracing output can be disabled or enabled globally
	"""
	def __init__(self):
		self.enabled = False
	def __call__(self, f):
		def wrap(*args, **kwargs):
			if self.enabled:
				print(f"Calling {f} with\n  args={args}\n  kwargs={kwargs}')
			result = f(*args, **kwargs)
			if self.enabled:
				print(f"  result = {result}")
			return result
	return wrap
```

Consumer:
```python
tracer = Trace()

@tracer
def my_function(*args, **kwargs):
	return "xyz"
def my_function(*args, **kwargs):
	return "abc"

my_function('tracing is off')
my_other_fn('tracing is off')

tracer.enabled = True

my_function('tracing is on!')
my_other_fn('tracing is on!')
```
Output:
```
Calling <function my_function at 0x....>
  args=('tracing is on!',)
  kwargs={}
  result = xyz
Calling <function mo_other_fn at 0x....>
  args=('Tracing is on!',)
  kwargs = {}
  result = abc
```
`````

## Passing Arguments to Decorators

Wrap the decorator in an outer function that takes these arguments.
The function can generate a decorator dynamically that uses these arguments.
This is often used to enforce invariants and other limits.

`````ad-example
Decorator
```python
def check_non_negative(argnumber):
	def validator(f):
		def wrap(*args):
			if args[argnumber] < 0:
				raise ValueError(f'must be >= 0')
			return f(*args)
		return wrap
	return validator
```
Consumer
```python
@check_non_negative(1)  # Check argument 1 (size)
def my_func(value, size):
  pass
```
`````

## Decorating Classes

Class decorators take in a class as an argument and return a new class.
Often the returned class is a modified version of the original.

### Using Class Decorators

`````ad-example
```python
@decorator1
@decorator2
class My_Class:
	pass
```
`````

### Implementing Class Decorators

`````ad-example
title: Example 1: Adding a new method to an existing class
collapse: true
Decorator:
```python
def add_ping_method(cls):
	def my_ping(self):
		print("PONG!")
	setattr(cls, 'ping', my_ping)
	return cls
```
Consumer:
```python
@add_ping_method
class Foo:
	pass

f = Foo()
f.ping()     # prints "PONG!"
```
`````


`````ad-example
title: Example 2: Adding a `__repr__` method based upon attributes
collapse: true
Decorator:
```python
import inspect

def auto_repr(cls):
	members = vars(cls)
	clsname = cls.__name__
	if "__repr__" in members:
		raise TypeError("__repr__ is already defined!")
	if "__init__" not in members:
		raise TypeError("No constructor!")
	sig = inspect.signature(cls.__init__)
	params = list(sig.parameters)[1:]  # Remove "self"
	for x in params:
		if not (isinstance(members.get(x, None), property)):
			raise TypeError("All initializer params must be properties")

	def synthetic_repr(self):
		typename = type(self).__name__
		args = list()
		for name in params:
			val = getattr(self, name).__repr__()
			args.append(f"{name}={val}")
		argstr = ", ".join(args)
		return f"{typename}({argstr})

	setattr(cls, "__repr__", synthetic_repr)
	return cls
```
Consumer:
```python
@auto_repr
class Foo:
	def __init__(self, x, y):
		self._x = x
		self._y = y
		
	@property
	def x(self): return self._x
	
	@property
	def y(self): return self._y

f = Foo(10, 15)
print(repr(f))   # Foo(x=10, y=15)
```
`````

## Decorator Factories

Produce custom decorators by varying parameters.

`````ad-example
collapse: true
Invariant decorator takes a predicate and enforces it.
Modifies every method in a class to perform invariant checking.
```python
import functools
import inspect

def postcondition(predicate):
	def function_decorator(f):
		@functools.wraps(f)   # Preserve function metadata like 'help'
		def wrapper(self, *args, **kwargs):
			result = f(self, *args, **kwargs)
			if not predicate(self):
				n = predicate.__name__
				raise RuntimeError(f"Postcondition {n} failed.")
			return result
		return wrapper
	return function_decorator

def invariant(predicate):
	function_decorator = postcondition(predicate)
	def class_decorator(cls):
		members = list(vars(cls).items())
		for name, member in members:
			if inspect.isfunction(member):
				decorated_member = function_decorator(member)
				setattr(cls, name, decorated_member)
		return cls
	return class_decorator
```
Consumer:
```python
def at_least_two_locations(itinerary):
	return len(itinerary._locations) >= 2

def no_duplicates(itinerary):
	locs = list(itinerary._locations)
	nodupes = list(set(locs))
	return sorted(locs) == sorted(nodupes)

@invariant(no_duplicates)
@invariant(at_least_two_locations)
class Itinerary:
	def __init__(self):
		self._locations = [ 'Lisbon', 'Amsterdam', 'Venice' ]
	def add(self, loc):
		self._locations.append(loc)
	def remove(self, loc):
		self._locations.remove(loc)

i = itinerary()
try:
	i.add("Amsterdam")  # Add duplicate
except RuntimeError as e:
	print(f"Raised error - {e} - {str(i._locations)}")

i = itinerary()
try:
	i.remove("Amsterdam")  # This should work.
except RuntimeError as e:
	print(f"Raised error - {e} - {str(i._locaionts)}")

i = itinerary()
try:
	i.remove("Venice")    # Left with <2 destinations - raises error.
except RuntimeError as e:
	print(f"Raised error - {e} - {str(i._locaionts)}")
```
`````
