Objects designed to be used in a `with` statement ([PEP 343](https://peps.python.org/pep-0343/)).

Defines code for setting up and cleaning up a resource.
Cleanup will be executed regardless of how the `with` block terminates.

## Using
```python
with expression as varname:
	with_block
```

### Multiple Context Managers
```python
with cm1() as a, cm2() as b:
	do_stuff(a, b)
```

is equvalent to:
```python
with cm1() as a:
	with cm2() as b:
		do_stuff(a, b)
```

Entry order: cm1, cm2
Exit order: cm2, cm1
Exceptions will be caught by cm2 first, then cm1 if re-raised or not caught.

## Implementing
### From Scratch
Context managers implement two methods:
`__enter__`: returns an object which is bound to the `as` variable.
`__exit__`: Cleanup code

#### enter method
`def __enter__(self):`
Sets up the resource and returns an object which is bound to the `as` variable (if used).
This can return anything, even a simple variable, and is not the context manager itself.

#### exit method
`def __exit__(self, exc_type, exc_val, exc_tb):`
Called with exception information if the `with` block raised one, or `None` for all three parameters on normal exit.
Responsible for tearing down the resource created in the enter method.
Returns a boolean indicating whether exception should be re-raised after `__exit__` is done.


### Implementing with Context Manager Decorator
The `contextlib` module provides a [[BEFORE/OldOrg/STEMpunk/Python/Python Decorators|decorator]] for `contextmanager`.

1. Create a generator.
2. Decorate it with `@contextmanager` - returns a contextmanager factory.

```python
import contextlib
import sys

@contextlib.contextmanager
def my_context_manager():
	# enter code goes here.
	try:
		# yield the with variable
		# normal exit code.
	except Exception:
		# code for exceptional exit

with logging_context_manager as x:
	do_stuff(x)
```
Re-raising or not catching the exception will cause `with` to re-raise and propagate it.


### with Statement Behavior

```python
with expr as var:
	block
```

- `expr` is executed and returns a context manager.
- The context manager's `__enter__()` method is called with no arguments
	- Returns an object. If `as` is used, the return value is bound to that variable.
	- If `__enter__` throws an exception, execution stops here.
- The `with` block is executed with `var` made available.
- After the `with` block exits, the context manager's `__exit__()` method is called.
	- If the `with` block throws an exception, this is passed to `__exit__`.

Equivalent code:
```python
mgr = expr
clean_exit = True

try:
	try:
		var = mgr.__enter__()
		do_block(var)
	except:
		clean_exit = False
		mgr.__exit__(*sys.exc_info()) or raise
finally:
	if clean_exit:
		mgr.__exit__(None, None, None)
```

### Example

```python
class LoggingContextManager:

	def __enter__(self):
		print('LoggingContextManager.__enter__()')
		return "You're in a with block!"

	def __exit__(self, exc_type, exc_val, exc_tb):
		print(f'LoggingContextManager.__exit__({exc_type}, {exc_val}, {exc_tb})')
		return

with LoggingContextManager() as foo:
	print(f"foo is {foo}")

print("Done.")
```

#### Happy Path
```python
LoggingContextManager.__enter__()
foo is You're in a with block!
LoggingContextManager.__exit__(None, None, None)
Done.
```

#### Default Exception Handling
If we raise an exception in the with block, `__exit__` is called with exception information.
The exception is then re-raised after `__exit__`, because it's allowed to propagate past `with`.

```python
with LoggingContextManager() as foo:
	print(f"foo is {foo}")
	raise Exception("Raising an exception")
```
```
LoggingContextManager.__enter__()
foo is You're in a with block!
LoggingContextManager.__exit__(<class 'Exception'>, Raising an exception, <traceback object at 0x101c6ea00>)
Traceback (most recent call last):
[...]
Exception: Raising an exception
```

#### Handling Exceptions Without Re-raising
If `__exit__()` returns a Falsey value, any exceptions are propagated.
If it returns a Truthy value,  exceptions are not propagated:

```python
	def __exit__(self, exc_type, exc_val, exc_tb):
		print('LoggingContextManager.__exit__()')
		if exc_type:
			print("An error was detected ({exc_val}) but I handled it.")
		else:
			print("all is well.")
		return True
```

Should not re-raise exceptions from within `__exit__`, only return False.

