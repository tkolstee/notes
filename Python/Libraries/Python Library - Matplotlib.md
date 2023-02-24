
```toc
```

## Simple graph
```python
from matplotlib import pyplot as plt

x_values = [ x for x in range(10) ]
y_values = [ x * 2 for x in x_values ]

plt.plot(x_values, y_values)
plt.show()
```

Plot same line but with points marked at each data point:
`plt.plot(x_vals, y_vals, marker='o')`

Plot only the data points - no line
`plt.plot(x_vals, y_vals, 'o')`




