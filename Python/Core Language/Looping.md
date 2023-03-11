## break and continue
A `break` statement within a loop causes the loop to exit immediately.
`continue` restarts the next iteration, including reevaluating the loop condition.

## while loop
```python
while condition:
  action
```

Loops until condition is False.

## for loop
```python
for item in iterable:
	action
```

Iterates over an iterable object, assigning the value to the loop variable (item). If the loop variable won't be used, convention is to use an underscore as the variable name.

## else clause
Both `while` and `for` loops can make use of an `else` clause. 

The `else` clause runs when the loop exits normally (not the result of a `break`). 

This behavior is obscure and thus should be commented or handled carefully. Either add a comment (`#nobreak`) or refactor the loop into a function that returns early instead of using `break`.
