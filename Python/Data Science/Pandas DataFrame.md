Represents table data: 2D data with row and column labels

```python
import pandas as pd
```

## Instantiating

### From Dictionary
Keys are column names, values are arrays of column data in order.
Arrays must be same length
```python
>>> import pandas as pd
>>> df = pd.DataFrame({
...   'name': [ 'Alice', 'Brad', 'Cindy' ],
...   'birth_month': [ 'May', 'Jan', 'Aug'],
...   'birth_year': [ 1937, 2002, 1993 ]
... })
>>> df
    name birth_month  birth_year
0  Alice         May        1937
1   Brad         Jan        2002
2  Cindy         Aug        1993
```

`__str__` method provides tabular formatting, and Jupyter notebook formats DataFrames as an actual table.

### From Nested Array
Column names are given in separate array.
```python
>>> my_array = np.array([ ['a', 'b', 'c'],
...                       ['d', 'e', 'f'],
...                       ['g', 'h', 'i'] 
... ])
>>> df = pd.DataFrame(
...       my_array,
...       columns = ['colA', 'colB', 'colC']
... )
>>> df
  colA colB colC
0    a    b    c
1    d    e    f
2    g    h    i
```

### From CSV File
Column headers are read from first line by default.

```python
df = pd.read_csv(filename)
```

## Accessing Elements

`df.loc[ rowspec ]`
`df.loc[ rowspec, colspec ]`
`df[colspec]`

rowspec can be:
- list of row numbers
- `:` for all
- `start:end`, inclusive unlike with array range

colspec can be a single column or list of columns by name

```python
df.loc[1]                        # Row with index 1
df.loc[[0, 2]]                   # Rows with index 0 and 2
df.loc[[0, 2], ['colA', 'colC']] # Rows 0&2, cols A&C
df.loc[1:3, ['colC', 'colA']]    # Rows 1-3, cols C & A
df['colA']                       # Access whole column w/o loc
df[['colB', 'colA']]             # Access multiple columns
```

When returning one row or column, a `Series` object is returned.
When returning multiple rows or columns, a `DataFrame` object is returned.

## Modifying Elements
```python
# Change whole row or column. Size must match!
df.loc[0]  = [3, 6, 9]   # Change first row
df['col2'] = [1, 2, 3]   # Change whole column

df['col2'] = 0           # Change whole column to same value
df.loc[3]  = 5           # Change whole row to same value

df['new_col_name'] = [ 1, 2, 3 ]  # Create new column
df.loc[last+1] = [1, 2, 3]        # Create new row
```

## Boolean and Conditional Indexing

Boolean indexing: List out which rows/cols should be included.
```python
df.loc[[False, True, False], [False, True, True]] 
```

List conditional in loc to only print out values matching.

```python
# Print only columns whose first value > 5 
df.loc[:, df.loc[0] > 5]
```

## Methods
| Method                                          | Effect                                                     |
| ----------------------------------------------- | ---------------------------------------------------------- |
| `rename(self[, axis, ...])`                     | Change row/column labels                                   |
| `fillna(self[, method, ...])`                   | Replace empty/NA/NaN cells using a specific method call    |
| `replace(self, to_replace=None, value=None)`    | Replace cells that contain `to_replace` value with `value` |
| `drop(self[, labels, axis, ...])`               | Drop rows or columns from the DataFrame                    |
| `pd.concat(objs, axis=0, join='outer', ...)`    | Concatenate objects along specified axis                   |
| `sort_values(self, by[, axis, ascending, ...])` | Sorts by values along specified axis                       |
| `pd.read_csv()`                                 | Read DataFrame from CSV text file                          |
| `to_csv()`                                      | Write DataFrame object to file as CSV                      |


```python
df = pd.DataFrame({ 'x': range(5) })

df['x^2'] = df['x'].apply(lambda x: x ** 2)
# or just...
df['x^2'] = df['x'] ** 2

df['parity'] = df['x'].apply(
		lambda x: 'even' if x%2==0 else 'odd'
)
```

get_dummies takes a categorical column like "parity" and produces 'one hot' columns for each permutation of values
```python
>>> dummies = pd.get_dummies(df['parity'])
>>> dummies
   even  odd
0     1    0
1     0    1
2     1    0
3     0    1
4     1    0

>>> df = pd.concat([df, dummies], axis=1)
>>> df
   x  x^2 parity  even  odd
0  0    0   even     1    0
1  1    1    odd     0    1
2  2    4   even     1    0
3  3    9    odd     0    1
4  4   16   even     1    0
```

"value_counts" counts number of occurrences of each value:
```python
>>> df['parity'].value_counts()
even    3
odd     2
Name: parity, dtype: int64
```

## Group By
```python
>>> gender_group = student_df.groupby('female_flag')

>>> gender_group
<pandas.core.groupby.generic.DataFrameGroupBy object at 0x12e709cd0>

>>> gender_group['gpa'].mean()
female_flag
False 92.333333
True 93.000000
Name: gpa, dtype: float64

>>> gender_group['num_classes'].sum()
female_flag
False    10
True     10
Name: num_classes, dtype: int64
```

