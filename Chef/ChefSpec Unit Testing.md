
## Testing Recipes
```ruby
describe 'httpd::default' do
	context '' do
		let(:chef_run) do
			runner = ChefSpec::ServerRunner.new
			runner.converge(described_recipe)
		end
		it 'converges' do
			expect {chef_run}.to_not raise_error
		end
		it 'includes the install recipe' do
			expect(chef_run).to include_recipe('httpd::install')
		end
	end
end

```

## Testing Ohai Plugins

### Mocking shell_out

**Ohai plugin file**
```ruby
x = shell_out('cmd')
```

**Spec file:**
```ruby
def mock_shell_out(exitstatus, stdout, stderr)
	shell_out = double('mixlib_shell_out')
	allow(shell_out).to receive(:exitstatus).and_return(exitstatus)
	allow(shell_out).to receive(:stdout).and_return(stdout)
	allow(shell_out).to receive(:stderr).and_return(stderr)
	shell_out
end

# ...

allow(plugin).to receive(:shell_out).with(/cmd/).and_return(mock_shell_out(0, 'stdout', 'stderr'))
```




---
# See Also
[Writing Great Unit Tests With ChefSpec - YouTube](https://www.youtube.com/watch?v=8phURCe9diE)

