<img src="images/pandas.png" />

# Pandas DataFrames Basics

## Reading a CSV File

Pandas makes it very easy to read data from a CSV file using `read_csv`.

```python
import pandas as pd

# Read a CSV file
penguins = pd.read_csv("penguins.csv")
```

## Exploring Columns, Head, Tail, Describe, and Info

After loading a DataFrame, you can quickly explore it:

```python
# Show the first 5 rows
print(penguins.head())

# Show the last 5 rows
print(penguins.tail())

# Get column names
print(penguins.columns)

# Summary statistics for numeric columns
print(penguins.describe())

# Get DataFrame info (rows, columns, dtypes, memory)
print(penguins.info())
```

You can also look at percentiles inside `describe()`:

```python
print(penguins.describe(percentiles=[0.25, 0.5, 0.75]))
```

## Adding a New Column

You can add a new column to a DataFrame using calculations on existing ones:

```python
# Example: ratio of culmen length to culmen depth
penguins['culmen_ratio'] = 100 * penguins['culmen_length_mm'] / penguins['culmen_depth_mm']

print(penguins[['culmen_length_mm', 'culmen_depth_mm', 'culmen_ratio']].head())
```

## Using `drop` and `inplace`

Some operations allow modification of the DataFrame **in place** without creating a copy.

```python
# Drop row index 0
penguins.drop(0, axis=0, inplace=True)

# Drop column 'culmen_depth_mm'
penguins.drop('culmen_depth_mm', axis=1)

# Reset index in place
penguins.reset_index(drop=True, inplace=True)
```

If you don’t pass `inplace=True`, Pandas will return a new DataFrame instead of modifying the original.

## Using `loc` in DataFrame

The `.loc` accessor is label-based indexing:

```python
# Get row with index 0
print(penguins.loc[0])

# Get multiple rows by labels
print(penguins.loc[0:3])

# Get a specific value (row 0, column 'species')
print(penguins.loc[0, 'species'])

# Get rows and columns together
print(penguins.loc[0:2, ['species', 'island']])
```

## `set_index` and `reset_index`

You can set one of the columns as the index for better labeling, and reset it back when needed.

```python
# Set 'species' as the index
penguins.set_index('species', inplace=True)
print(penguins.head())

# Reset index back to default integers
penguins.reset_index(inplace=True)
print(penguins.head())
```
