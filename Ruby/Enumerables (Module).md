
```ruby
class Menu
	include Enumerable
	def each   # Required by Enumerable
		yield "pizza"
		yield "spaghetti"
		yield "salad"
		yield "water"
		yield "bread"
	end
end

menu_options = Menu.new
menu_options.each do |item|
	puts "Would you like #{item}?"
end
menu_options.find{ |item| item == "pizza" }
menu_options.select{ |item| item.size > 5 }
menu_options.reject{ |item| item.size > 5 }
menu_options.first
menu_options.take(2)   # first two
menu_options.drop(2)   # all but first two
menu_options.min
menu_options.max
menu_options.sort
menu_options.reverse_each { |item| puts item }
```


