
```python
import seaborn as sns

# Joint plot - scatter plot with hists for x, y
sns.jointplot(x='Column 1', y='Column 2', data=df)
sns.catplot(x=col, y=col, hue=category, kind='bar', data=df)

```