---
aliases: [ "Basic I/O", puts, gets, print ]
---

## Console Input
The `gets` function reads user input up to newline and returns string including the EOL char.

```ruby
x = gets         # Takes in input up to and including newline
x = gets.chomp   # Removes trailing newline
x = gets.to_i    # Convert to integer
```

## Console Output
The `puts` function writes a string to the console, automatically adding a newline.
```ruby
puts x                    # Output with newline
```

`print` also writes a string but without a trailing newline
```ruby
print "Hello, "
print "#{name}!"
```

`printf` works as in C
```ruby
printf "Value is %s", v   # Formatted output (equiv to C printf)
```

`p` prints an "inspect" version of an object for debug (like `repr` in Python)
```ruby
p myObject
```

## File I/O

`File.new` creates a new file and `File.open` opens an existing file.
Both return an object as handle.

`File.read` reads the file in its entirety and returns the contents as a single string.
`File.readlines` returns the file contents in an array of individual lines.

`file.puts` writes a string to the file
`file.close` closes the file.
`f.each` takes a block and iterates through each line of the file.

A file object can be used with a block so that it is automatically closed outside the block's scope.

```ruby
file = File.new("myfile.txt", "w")  # r - read, w - write, a - append
file.puts("Hello, world!")
file.close

file_contents = File.read("myfile.txt")
file_lines_array = File.readlines("myfiles.txt")

file.open("srcfile.txt") do |f|
	f.each do |line|
	  name, lang, specialty, sales = line.split(',')
	end
end   # No need to close. Done by "do" and fall out of scope
```
