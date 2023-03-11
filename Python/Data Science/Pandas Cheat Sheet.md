```python
import pandas as pd

# Instantiating
df = pd.DataFrame( { 'col1': [1, 2, 3], ... } )
df = pd.DataFrame( nested_np_array, columns=['col1', 'col2', 'col3'] )
df = pd.read_csv(filename)

df.columns    # List of column names
df.isnull()   # Boolean array in same shape, True where nulls
df['a'].sum() # Sum of column

# Accessing Elements
df.loc[rowspec]           # Rowspec:   index,  start:end, :, bool_array
df.loc[rowspec, colspec]  # Colspec:   ['colname', 'colname'], bool_array
df['colname']             # Column
df[['colA', 'colB']]      # Multiple columns

# Modifying Elements
df.loc[3] = [ 1, 2, 3 ]   # change row with index 3
df['col2'] = [ 3, 6, 9 ]  # change whole column
df.loc[1] = 0             # set all columns in row idx 1 to 0
df['colA'] = 0            # set all rows in column to 0

# Filtering Rows
df.loc[ df['population']>2000000] ]

# Methods
df.rename( columns={ 'oldname': 'newname', ... } )   # equiv (mapper, axis=1)
df.rename( index={ 'oldindex': 'newindex', ... } )   # equiv (mapper, axis=0)
df.fillna(np.nan)  # fill pd.NA values
df.drop([label_array], axis=1)   # Drop rows or cols
pd.concat(*obj, axis=1, join='outer', ignore_index=False)
df.sort_values(by, axis)  # Sort in place.
df.to_csv(filename)

# Frequency analysis
df['col'].value_counts()

# Interaction with pyplot
df.plot.hist()
df.plot.pie()
```

axis values are generally (0 or 'index') for rows, (1 or 'columns') for columns.

----
# Sources
[pandas.DataFrame.rename — pandas 1.5.2 documentation](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.rename.html)
[[The Statistics and Calculus with Python Workshop]]
