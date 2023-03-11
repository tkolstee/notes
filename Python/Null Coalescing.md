

## Using Short-Circuit Evaluation
[[BEFORE/OldOrg/STEMpunk/Python/Python Boolean#Short-Circuit Evaluation|Short-circuit evaluation]] can be used to provide a default value around None or Falsy values.
```python
x = possibly_null_value or value_if_null

# For example...
x = settings.get('foo') or 'bar'
```

## Guarding Expressions
```python

# "Look Before You Leap" (LYBL) Principle.
def shares(resources, people):
	if people == 0: return 0
	return resources // people

# Easier to ask forgiveness than permission (EAFP) - more pythonic
def shares(resources, people):
	try:
		return resources // people
	except ZeroDivisionError:
		return 0

# Concise, but might not be obvious why it works.
def shares(resources, people):
	return people and resources // people

# Better yet, just propagate what should be an exception.
def shares(resources, people):
	return resources // people
```
