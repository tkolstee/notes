

```python
import openpyxl
```

## Create, Load, or Save a Workbook
```python
wb = openpyxl.Workbook()
wb = openpyxl.read_workbook(filename)
wb.save(filename)
```

## Sheets
```python
# Access
wb.sheetnames           # Array of sheets by name
for sheet in wb: pass   # Loop through sheets in workbook

# Create
ws = wb.create_sheet(title=None, index=None)
ws2 = wb.copy_worksheet(source)

# Load
ws = wb["Mysheet"]
ws = wb.active

# Change properties
ws.title = "New Title"
ws.sheet_properties.tabColor = "1072BA"
```

## Working with Data

### Single Cells
```python
c = ws['A1']
c.value = 'foo'
ws['A1'] = 42
ws['A2'] = datetime.datetime.now()  # Conversion happens

d = ws.cell(row=4, column=2, value=10)

# Cells are created upon access:
for x in range(1, 101):
  for y in range(1, 101):
    ws.cell(row=x, column=y)
```

### Ranges of Cells
```python
cell_range = ws['A1':'C2']

colC = ws['C']
row10 = ws[10]
col_range = ws['C:D']
row_range = ws[5:10]

# 2D Tuple of cell objects
tuple(ws.rows)
tuple(ws.cols)

# Iterators of cell objects (or values)
# min_row: int, max_row: int, min_col: int, max_col: int, values_only: bool
ws.iter_rows()
ws.iter_cols()
```




```




ws.append([1, 2, 3])       # Append row
ws['A2'] = datetime.datetime.now()   # Type conversion automatic
wb.save("sample.xlsx")
```

----
# Sources
[openpyxl - A Python library to read/write Excel 2010 xlsx/xlsm files — openpyxl 3.0.10 documentation](https://openpyxl.readthedocs.io/en/stable/)

# Alternatives

xlwings - does not work on Linux (I think it needs Excel or some .NET API).
pandas - does not read .xlsx files.