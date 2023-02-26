

## Configparser module
```python
import configparser
config = configparser.ConfigParser()
```

### Reading Config Files
```python
config.read(filename)
```

`config.sections()` is an array containing the section names
`config['sectionname']` is a dict of name/value pairs representing the values in the section.
Keys are case-insensitive and stored in lowercase.

#### Data Types
Values are stored and returned as strings.
`config.getboolean(section, key)` parses yes/no, on/off, true/false, and 1/0 pairs
`config.getint(section, key)` and `config.getfloat(section, key)` convert to int and float respectively

#### Fallback values
Using the `get` method, as with a dictionary, you can supply an additional argument to fallback if the key is not found.

### Writing Config Files
```python
with open('filename.ini', 'w') as configfile:
  config.write(configfile)
```

----
# Source
[configparser — Configuration file parser — Python 3.10.6 documentation](https://docs.python.org/3/library/configparser.html)

# Further Expansion
Configparser also provides the ability to interpolate values and customize the parser's behavior. See source above for more information.

