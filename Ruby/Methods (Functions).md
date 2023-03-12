---
aliases: [ functions, methods ]
---

By convention mutating methods are suffixed with `!`, and Boolean-returning with `?`

## Defining Methods
```ruby
# Without parameters
def genericGreeting ()
	puts("Hello, person!")
end
```

### Parameters
Params are pass-by-value but in many cases the value is a reference
- Exceptions: `FixNum`, `NilClass`, `TrueClass`, `FalseClass`
- Reassignment changes local copy, accesses may mutate
```ruby
def greetPerson(name)
	puts("Hello, #{name}!")
end
```

Convention is to add a `!` to the function name when it modifies params or `?` when it returns Boolean.
```ruby
def file_exists?(filename)
# .....

def add(a, b)
	a + b
end

def add!(a, b)
	a += b
end

```
#### Default values
Given with `=`
`def greetPerson(name="Jimbo") ... end`
Parameters without defaults come first, since parameters are positional.

#### Multiple Parameters
Append `*` to a parameter in a method definition to collect an arbitrary number of arguments as an array. This must be listed last.

#### Block as Parameter
Prepending `&` to the last argument in a method definition expects a block following the method call, which will be converted to a `Proc` object and assigned to that parameter.

### Return Values
Returns value of last statement executed by default
```ruby
def add_three(x)
	x + 3
end

puts(add_three(10))   # 13
```

Explicitly return a value (and exit early) with `return`
```ruby

def add_three_if_even(x)
	if x % 2 == 0
		return x + 3
	end
	x
end
puts(add_three_if_even(10))  # 13
puts(add_three_if_even(11))  # 11
```

Explicit `return`s can also return multiple values:
```ruby
def add_three_and_orig(x)
	return x, x+3
end
puts(add_three_and_orig(10))  # [10, 13]
```

## Calling Methods
```ruby
# Without parameters
genericGreeting

# With parameters
greetPerson("Jimbo")
```

Prepend `*` to an array passed to a method to expand it into individual arguments.