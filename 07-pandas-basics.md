<img src="images/pandas.png" />

## What is Pandas?

**Pandas** is a Python library for working with structured data.
It provides two main data structures:

* **Series** → 1D labeled array (like a column in Excel)
* **DataFrame** → 2D labeled table (like an Excel sheet)

Pandas is built on top of **NumPy** and is widely used for data analysis, cleaning, and manipulation.

## Creating Pandas Series with Lists

A **Series** can be created directly from a Python list:

```python
import pandas as pd

pd_series = pd.Series([10, 100, 15, 35, 35])
print(pd_series)
```

Output:

```
0     10
1    100
2     15
3     35
4     35
dtype: int64
```

Notice that Pandas automatically assigns an **index (0,1,2,3,4)**.

## Pandas Series vs NumPy Array

```python
import numpy as np

pd_series = pd.Series([10, 100, 15, 35, 35])
np_array = np.array([10, 100, 15, 35, 35])

print(pd_series)
print(np_array)
```

* A **Series** has an **index** (labels) + values.
* A **NumPy array** has only values (no labels).

## Index of Pandas Series

```python
pd_series = pd.Series([1776, 1867, 1821], index=["USA", "CANADA", "MEXICO"])
print(pd_series)
```

Output:

```
USA       1776
CANADA    1867
MEXICO    1821
dtype: int64
```

You can access by:

```python
print(pd_series["USA"])   # 1776
print(pd_series.index)    # Index(['USA', 'CANADA', 'MEXICO'], dtype='object')
print(pd_series.values)   # array([1776, 1867, 1821])
```

## Creating Pandas Series with Dictionary

A dictionary automatically maps keys → index, values → data.

```python
pd_series = pd.Series({"USA": 1776, "CANADA": 1867, "MEXICO": 1823})
print(pd_series)
```

## loc (Label-based Indexing)

```python
print(pd_series.loc["CANADA"])   # 1867
```

`loc` uses the **label** (index name).

## iloc (Position-based Indexing)

```python
print(pd_series.iloc[0])  # 1776 (first element)
```

`iloc` uses the **integer position**.

## Index and Values

```python
print(pd_series.index)
print(pd_series.values)
```

## What is a DataFrame?

A **DataFrame** is a 2D labeled table (rows + columns).
Think of it like an Excel spreadsheet inside Python.

## Creating a DataFrame

```python
import numpy as np

np.random.seed(100)
my_data = np.random.randint(0, 101, (4, 3))
row_index = ['CA', 'NY', 'AZ', 'TX']
col_names = ['Jan', 'Feb', 'Mar']

# Create DataFrame
df = pd.DataFrame(my_data, index=row_index, columns=col_names)
print(df)
```

Output:

```
    Jan  Feb  Mar
CA    8   24   67
NY   87   79   48
AZ   10   94   52
TX   98   53   66
```

## loc and iloc in DataFrames

```python
print(df.loc['AZ'])   # row by label
print(df['Jan'])      # column by label

print(df.iloc[0])     # first row
print(df.iloc[:2])    # first 2 rows
```

## Getting Index in Range

```python
print(df.loc['NY':'AZ'])
```

## Getting Columns

```python
print(df[['Jan', 'Feb']])  # multiple columns
print(df['Jan'])           # single column
```
