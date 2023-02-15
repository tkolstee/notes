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

## Implementing Function Decorators

