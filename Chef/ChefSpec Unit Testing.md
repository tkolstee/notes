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

---
# See Also
[Writing Great Unit Tests With ChefSpec - YouTube](https://www.youtube.com/watch?v=8phURCe9diE)

