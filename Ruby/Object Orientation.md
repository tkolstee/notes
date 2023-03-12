
*class* contains
- *data members* aka *properties* or *attributes*
	- *class* or *static* members shared across instances
	- *instance* members are unique to an instance
- *member functions* aka *methods*
	- *class* or *static* functions called without an instance
	- *instance* functions are called using an instance

Instance of class is an *object*

Accessing data members or member functions is done with the dot operator `.`
```ruby
# <object/class>.<data member/member function>
Math.sin(3.14)  # Class Math, static method sin
```


```ruby
obj.class      # Return object's class
cls.ancestors  # Return inheritance hierarchy of a class

class Foo
end

f = Foo.new
```

## Initializers
```ruby
# Defining a class
class Animal
  def initialize
    puts "Creating a new animal"
  end
end

morris = Animal.new
```
Ruby does not support method overloading.
Use variable number of args to vary behavior.
```ruby
class Animal
	def initialize(*args)
		@name = args.size > 0 ? args[0] : "Unnamed"
	end
    def get_name
		@name
	end
end

morris = Animal.new("Morris")
x = Animal.new
puts "#{morris.get_name} and #{x.get_name}"
```

## Getters and Setters
### Manual
```ruby
class Foo
	def get_name
		@name
	end
	
	def name
		@name
	end
	
	def set_name(new_name)
		raise ArgumentError, "Name cannot be empty" if new_name.empty?
		@name = new_name
	end
	
	def name=(new_name)          # Override '=' operator
		self.set_name(new_name)
	end
end

f = Foo.new
f.set_name("foo")

puts f.get_name
f.name = "bar"

puts f.name
```

### Automatic
```ruby
class Person
	attr_reader   :name, :height, :weight    # getters only
	attr_writer   :name, :height, :weight    # setters only
	attr_accessor :name, :height, :weight    # both getters and setters
end
```

## Inheritance
Ruby supports single inheritance and overloading
```ruby
class Animal
	def is_an_animal?; true; end
	def make_noise; "generic animal noise"; end
	def print_info
		result = self.is_an_animal? ? "AM" : "AM NOT"
		puts "I #{result} an animal and I say '#{self.make_noise}'"
	end
end

class Dog < Animal
	def make_noise; "woof!"; end
end
class Human < Animal
	def is_an_animal?; false; end
	def make_noise; "I think, therefore I am."; end
end
Animal.new.print_info   # I AM an animal and I say 'generic animal noise'
Dog.new.print_info      # I AM an animal and I say 'woof!'
Human.new.print_info    # I AM NOT an animal and I say 'I think, therefore I am.'
```