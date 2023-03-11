
## Local Functions
Functions can be defined inside other functions and only remain within that scope.
This can keep function definitions closer to their use, improving organization and readability.

```python
def sort_by_last_letter(strings):
	def last_letter(s): return s[-1]
	return sorted(strings, key=last_letter)
```

## Closures
Functions can return a local function just like they were any other variable.
Dependencies are "bundled" with the function, called a *closure*.

> [!Example]- Example: Creating a closure
> 
> The address of x is stored in the function's `__closure__` attribute.
> This reference prevents x from being garbage-collected.
> 
> ```python
> def enclosing():
> 	x = "closed over"
> 	def local_func(): print(x)
> 	return local_func
> 
> lf = enclosing()
> lf()                   # "closed over"
> print(lf.__closure__)  # <cell at 0x....: str object at 0x....>
> ```

## Function Factories
Functions which take input and return a locally-defined function which varies based upon the input.
```python
def raise_to_power_fn_factory(exponent):
	def raise_to_exponent(x):
		return pow(x, exponent)
	return raise_to_exponent

square_fn = raise_to_power_fn_factory(2)
cube_fn = raise_to_power_fn_factory(3)
```

