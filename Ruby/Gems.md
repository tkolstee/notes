
```r
$ gem install json
$ gem list json
$ gem which json
/Users/cstack/.rvm/rubies/ruby-2.3.1/lib/ruby/2.3.0/json.rb
```
```ruby
load(abs_path_to_gem)
require('json')
```

## Requirements Files
Create a requirements file listing gems and optionally version specs:
```ruby
mymodule
my_other_module >=1.2, <2.0
```

Intall all listed gems and dependencies with:
`gem install -r requirements.txt`
