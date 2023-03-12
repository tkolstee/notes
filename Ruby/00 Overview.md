Ruby is entirely object-oriented. Even values (numbers, booleans) are objects and have methods.
Variables are dynamically typed
Statements end with newline (encouraged) or semicolon (discouraged).
Parentheses are often optional and omitted.

Classes are singly-inhereited. Modules are used for multiple inheritance.
Object properties are only accessible from outside through accessor methods.

By convention mutating methods are suffixed with `!`, and Boolean-returning with `?`

## Identifiers
alphanumeric characters and underscores
- cannot begin with digits
- cannot be a reserved keyword

Conventions
- snake_case for variables, functions, filenames
- pascalCase for classes and modules
- SCREAMING_SNAKE_CASE for constants

## Keywords
Reserved words

> [!Note]- List of keywords
> ```
> __ENCODING__, __LINE__, __FILE__,
> BEGIN, END, alias, and, begin, break,
> case, class, def, defined?, do, else,
> elsif, end, ensure, false, for, if,
> in, module, next, nil, not, or,
> redo, rescue, retry, return, self, super,
> then, true, undef, unless, until, when,
> while, yield
> ```

---
# See Also
[Rdoc](https://docs.ruby-lang.org/en/2.2.0/keywords_rdoc.html)
[Ruby Style Guide](https://github.com/rubocop/ruby-style-guide)
[Ruby Programming | YouTube](https://www.youtube.com/watch?v=Dji9ALCgfpM&list=WL&index=7)
[Understanding Ruby Load, Require, Gems, Bundler, and rails autoloading from the Bottom Up | Medium](https://medium.com/@connorstack/understanding-ruby-load-require-gems-bundler-and-rails-autoloading-from-the-bottom-up-3b422902ca0)
[Ruby modules: Include vs Prepend vs Extend | Medium](https://medium.com/@leo_hetsch/ruby-modules-include-vs-prepend-vs-extend-f09837a5b073)
[RSpec: Behaviour Driven Development for Ruby](https://rspec.info/)


