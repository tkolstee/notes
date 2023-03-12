
## if...elsif...else
```ruby
if a == 0
	puts("A is zero")
elsif a < 0
	puts("A is negative")
else
	puts("A is positive")
end
```

## unless...else
```ruby
unless cond1
	action1
else
	action2
end
```

## Single-line if and unless
```ruby
action if condition
action unless condition
```

## case...when
```ruby
case a
when 0
	puts "A is zero"
when 1, 2, 3, 4
	puts "A is less than 5"
when 5, 6, 7, 8, 9
	puts "A is greater than 5"
else
	puts "A is not a single-digit number"
end
```

## Ternary Operator
```ruby
cond ? val_if_true : val_if_false
```
