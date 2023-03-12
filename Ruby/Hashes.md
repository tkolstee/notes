
```ruby
number_hash = { "PI" => 3.14, "Golden" => 1.618, "e" => 2.718 }

puts number_hash["PI"]
number_hash["One"] = 1

hash_with_def = Hash.new("No Such Key")

h1.update(h2)   # Destructive merge (h2 overrides h1) - modifies h1
h1.merge(h2)    # Returns new hash (h2 overrides h1)

h1.each do |key, value|
	puts "#{key} = #{value}"
end

h1.has_key?('xyz')
h1.has_value?('xyz')
h1.empty?
h1.size

h1.delete(key)
```