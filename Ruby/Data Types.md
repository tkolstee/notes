
## Numbers
Literal numbers with/without sign
Binary starts with `0b`, octal with `0`, hex with `0x`
Scientific notation: `6.8E9` (equiv to $6.8 \times 10^9$)

## Strings

Double-quotes: allows interpolation and escapes
Single-quotes: prevents interpolation and **most** escapes

```ruby
two_lines = "This is\ntwo lines"           # Escape - \n is newline

full_name = first_name + " " + last_name   # Concatenation with +
full_name = "#{first_name} #{last_name}"   # Interpolation
result = "X + Y is #{x+y}"                 # Interpolation with expression

full_name = '#{first_name}\n#{last_name}'  # No escapes or interpolation between single-quotes

multiline_string = <<EOM
This is a very long string
that contains interpolation
like #{4+5} \n\n
EOM

s.chomp               # Remove trailing newline sequence
s.include?("xyz")     # Check for substring
s.size                # Return size in chars
s.count("aeiou")      # Return number of vowels
s.count("^aeiou")     # Return non-vowels
s.start_with?("John") # Test from start of var
s.index("foo")        # Find index of string occurrence
s1 == s2              # Equal value
s1.equal?(s2)         # Same identity / object
s.upcase              # Convert to uppercase
s.downcase            # Convert to lowercase
s.swapcase            # Upper to lower and vice versa
s.lstrip              # Strip whitespace from beginning
s.rstrip              # Strip whitespace from end
s.strip               # Strip whitespace from beginning/end
s.rjust(20, '.')      # Padded right justification
s.ljust(20, '.')      # Padded left justification
s.center(20, '.')     # Padded centering
s.chop                # Remove last character (non-destructive)
s.chop!               # Remove last character (destructive)
s.chomp               # Remove trailing newline
s.chomp('xyz')        # Remove 'xyz', if present, from end of string
s.split(//)           # Split every character into array
s.split(/,/)          # Split into array by commas
s.to_i  s.to_f, s.to_sym  # Convert to integer, float, symbol
s.length              # Length in characters
```

## Converting between strings and numbers
`String` has the `.to_i` and `.to_f` methods to convert to integer or float
Numeric types have a `.to_s` method (with optional base argument) to convert to string
```ruby
254.to_s(16)   # "fe"
25.to_s        # "25"
"295.75".to_f  # 295.75
"295.75".to_i  # 295
```

## Symbols
Conserve memory and speed comparison
Immutable and don't have access to string methods
```ruby
puts :derek            # derek
puts :derek.to_s       # derek
puts :derek.class      # Symbol
puts :derek.object_id  # 833628

## Cannot be compared directly
:derek == "derek"         # false
:derek.to_s == "derek"    # true
"derek".to_sym == :derek  # true
```
