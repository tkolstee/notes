## Create an array
```ruby
# Empty
Array.new(10)

# Populated
nums = Array [1, 7, -5, 4, 7]
# or just
stuff = [ 1, 2, 3, "foo", 5 ]
```

## Iterating
```ruby
myarray.each do |item|
	action(item)
end
```

## Accessing Elements
```ruby
x = nums[0]    # First element
nums[0] = 10   # Assign to element

# Access several elements, returns array
array[1, 3, 5] 
array4.values_at(0, 1, 3)
```

## Assigning to Elements
Can assign to elements outside existing. If intermediate elements exist, they will be assigned `nil`.
```ruby
x = Array ['a', 'b']
x[6] = 'g'
puts(x)  # ["a", "b", nil, nil, nil, nil, "g"]
```

## Arrays
```ruby
array.join(', ')

array4.shift()             # Removes and returns first item
array4.pop()               # Removes and returns last item
array4.unshift(0)          # Adds to beginning of array
array4.push(6, 7)               # Adds to end of array (returns len of updated array)
array4.concat(['a', 'b', 'c'])  # Adds to end of array (returns new array)
array4.size
array4.include?("two")
array4.count("E")
array4.empty?
array.length

array4.each do |value|
  action(value)
end
```
