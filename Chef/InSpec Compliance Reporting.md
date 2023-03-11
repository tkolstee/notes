## CLI Usage

```
inspec exec /path/to/single_test.rb
inspec exec /path/to/profile
inspec exec git@github.com:dev-sed/linux-baseline.git
inspec exec https://webserver/linux-baseline.tar.gz
inspec exec supermarket://username/linux-baseline

inspec exec -t ssh://username@example.org --sudo -i /path/to/ssh-key /path/to/single_test.rb
```


## Profiles

- 📁  `examples/profile`
	- 📄`README.md`
	- 📁 ` controls`
		- 📄`example.rb`
		- 📄`control_etc.rb`
	- 📁 `libraries`
		- 📄`extension.rb`
	- 📁`files`
		- 📄`extras.conf`
	- 📄`inspec.yml`




---
# Sources
[Introduction to Test-kitchen and InSpec](https://www.youtube.com/watch?v=T66PB-Kn0kE)

# See Also
[Dev-sec](https://dev-sec.io) - premade configs and remediations
[InSpec Docs](https://docs.chef.io/inspec)
[InSpec Downloads](https://www.chef.io/downloads/tools/inspec)
[Preparing for Audits With Inspec (YT)](https://youtu.be/0Zk-n-UVCMA)
