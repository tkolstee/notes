
```python
import yaml

with open('foo.yml', 'r') as f:
	data = yaml.load(f)

for key, value in data.items():
	print(key + ' : ' + str(value))
```

For multiple YAML documents in same file (separated by `---`):

```python
import yaml

with open('foo.yml', 'r') as f:
	dictionary = yaml.load_all(f)

for doc in dictionary:
	print("------ New Document")
	for key, value in doc.items():
		print(key + ' : ' + str(value))
```

