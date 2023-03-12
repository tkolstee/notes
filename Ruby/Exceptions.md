### Raising
```ruby
def divide(num, denom)
	raise ArgumentError, "denominator cannot be zero" if denom == 0
	num / denom
end
```

### Catching
```ruby
begin
	result = divide(x, y)
rescue ArgumentError
	puts("Sorry Dave, I'm afraid I can't do that")
end
```
