---
aliases: [ variables, constants ]
---
Declaration is not required, assignment is declaration

```ruby
my_var1 = "foo"
var2 = 5
```


## Identifiers
- Alphanumeric and underscore, cannot start with digit.
- Constants (start with uppercase) will warn but allow modification

## Initialization and Assignment
- Variables are dynamically typed
- Use of unitialized variables throws `NameError`
- Multiple assignment: `name, age = "Tony", 47`
- All variables are references
- Assignment does not create a new copy of an object, except `FixNum`, `NilClass`, `TrueClass`, and `FalseClass` which are stored directly and copied.
- Method arguments are passed as references and may mutate objects. Reassigning an arg variable within a method changes the local variable but not the object passed in. 

## Scopes
- Global - name prefixed with `$`.
- Toplevel (main)
- Class or module
	- Instance variables prefixed with `@`.
	- Class variables prefixed with `@@`.
- Functions
	- `while`, `for`, and `until` are not methods and don't define a scope.
	- `loop` is a method and does define a scope.
- Block
	- Block variables are local if names are unique.
	- If same name exists in caller's scope, no masking variable is created.

### Global
Prefix with `$`:
```ruby
# $<varname> = <initial value>
$debugmode = false
```

### Method
Variables defined within a method are local to it.
Use `$` to access or declare globals from within a method.
`loop` is a method and does define a scope

### Block-Level
Variables within blocks are local if names are unique.
If local variable has same name as caller's scope, no new variable is created.
`while`, `until`, and `for` are not methods so don't define a scope.
