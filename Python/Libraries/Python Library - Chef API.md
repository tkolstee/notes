

## Installing
`pip install pychef`

## Using the Knife API
```python
import chef
api = chef.autoconfigure()
x = chef.Search('node', f'fqdn:www.*')
node = chef.Node('www.example.org')
```

---
# Resources
[[Chef API|Python Chef API]]

