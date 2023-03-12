
```python
import matplotlib.pyplot as plt

plt.scatter(x_vals, y_vals, s=sizes, c=colors)

plt.plot(x_vals, y_vals, colors=ar, styles=ar)

plt.bar(labels, values)

plt.xticks(locations, labels)

plt.legend(return_values_from_plt_bar, labels)

plt.hist(x, bins=30)

plt.imshow(my_2d_map) # heatmap
plt.colorbar()         

linspace(start, end, steps)  # Evenly spaced numbers
plt.show()
```

Can call `plot` multiple times to generate multiple lines
`plot()` styles values can be `-` (line), `--` (dashed line), `:` (dotted line)
specify alpha=0.2 to overlay multiple plots

----
# Sources
[matplotlib.pyplot — Matplotlib 3.5.3 documentation](https://matplotlib.org/3.5.3/api/_as_gen/matplotlib.pyplot.html)
[[The Statistics and Calculus with Python Workshop]]
