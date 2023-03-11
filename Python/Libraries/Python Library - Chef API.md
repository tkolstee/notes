

## Installing
`pip install pychef`

## Using the Knife API
```python
import chef

api = chef.autoconfigure()

srch = chef.Search('node', 'chef_environment:FOO')
for result in srch:
  print(f"NODE: {result['name']})


node = chef.Node('myhostname.example.com')
node['chef_environment'] = "BAR"
node.save()
```

---
# Resources
[[Chef API|Python Chef API]]

