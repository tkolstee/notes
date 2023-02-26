```python
import json
```

## Convert data structure to JSON:
```python
mydoc = json.dumps(obj)
```

| Argument         | Type                     | Use                                    |
| ---------------- | ------------------------ | -------------------------------------- |
| (2nd positional) | io object                | Output location                        |
| sort_keys        | Boolean                  | sort keys when dumping                 |
| separators       | Tuple, e.g. `(',', ':')` | Define separators (compact)            |
| indent           | numeric                  | Number of spaces for each indent level |

## Convert JSON to data structure:
```python
result_1 = json.loads(json_string)
result_2 = json.load(io_object)
```


----
# Source
[json — JSON encoder and decoder — Python 3.11.0 documentation](https://docs.python.org/3/library/json.html)

