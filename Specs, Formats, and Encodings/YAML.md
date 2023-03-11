
Yet Another Markup Language

Simple YAML document:

```YAML
---
foo: 1
bar: two
```

## Structure

### Beginning of document marker
- `---` starts document.
- More than one document can be in the same file.

### Keys and Values
-   Keys should be unique at same level of indentation in same block
-   Key and value separated by colon.

### Whitespace
-   Significant for both indentation and end-of-line
-   Indents are one or more spaces
-   Levels should be consistent (e.g. x spaces per level).
-   Tabs should not be used

### Comments
-   Prefixed with `#` outside of quotes
-   Continue to end-of-line

## Values

#### Simple Values

##### Single-Line Strings
Enclosed in single or double quotes.
Escape sequences can be used with double quotes.
```YAML
foo: "A metasyntactic\n variable"      # \n interpreted as linefeed
bar: 'A different\n variable'          # \n is literal
baz: This is a string\n without quotes # \n is literal
```

##### Integers
```yaml
foo: 123   # Decimal
bar: 0x20  # Hexidecimal
baz: 0775  # Octal
```

##### Floating-Point Numbers
```YAML
pi: 3.14159265
c: 2.99792458e+08
```

##### Booleans
True values are represented by `true`, `yes`, or `on`; false by `false`, `no`, or `off`.
```YAML
true1: true
true2: yes
true3: on
false1: false
false2: no
false3: off
```

##### Null Values
Represented by `null` or `~`
```YAML
null1: null
null2: ~
```

##### Multi-line strings
Indentations at beginning of line will be removed.
```YAML
# Note that in all cases indents at beginning of line will be removed

# '>' indicates that internal whitespace should be collapsed
foo: >
  This will appear as
  one long single-line
  string

# '|' indicates that internal whitespace should be preserved
bar: |
  This will show
  the embedded newline

# A '+' modifier means to retain the newline at the end of the string
baz: >+
  This will appear as
  one long line and 
  end in a newline

# A '-' modifier means to remove the newline at the end of the string.
quux: |-
  This string will
  not end in a
  newline
```

#### Complex Values

##### Lists / Arrays
```YAML
# Inline
inline_list: [ 'alice', 'bob', 'carol', 154 ]

# Multiline
multiline_list:
  - Alex
  - Barbara
  - Carl
  - 8088
```
		
##### Dictionaries
		
```YAML
# Inline
ghosts: { thing1: "inky", thing2: "blinky", thing3: "pinky", thing4: "clyde" }

# Multiline
chief_weapons:
  first: "surprise"
  second: "fear"
  third: "ruthless efficiency"
  fourth: "dedication"
```
		
#### Compound Values
		
```YAML
# List of dictionaries
xmas_list:
  - thing: "partridge"
    type: "bird"
    quantity: 1
    location: "pear tree"
  - thing: "turtledoves"
    quantity: 2
    type: "bird"
  - thing: "french hens"
    quantity: 3
    type: "bird"
```

---
# Source
[YAML Tutorial](https://www.cloudbees.com/blog/yaml-tutorial-everything-you-need-get-started)

