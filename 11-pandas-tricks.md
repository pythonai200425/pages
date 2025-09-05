# Pandas – Rows, Cells, Conditions & More 🐼✨

In this lesson, we’ll go deeper into DataFrame operations – adding rows, updating cells, concatenating, applying conditions, and more. Let’s have fun with it! 🎉

## 1. Adding Rows ➕

You can add a new row using `.loc` with a new index number.

```python
import pandas as pd

df = pd.DataFrame({
    'name': ['Alice', 'Bob'],
    'age': [25, 30]
})

print("Before adding:")
print(df)

# Add row with .loc
df.loc[2] = ['Charlie', 35]

print("After adding:")
print(df)
```

## 2. Replacing Rows 🔄

You can replace an existing row using `.loc` (label-based) or `.iloc` (index-based).

```python
print("Before replacing:")
print(df)

# Replace row with .loc
df.loc[1] = ['Bobby', 32]

# Replace row with .iloc
df.iloc[0] = ['Alicia', 28]

print("After replacing:")
print(df)
```

## 3. Updating Specific Cells ✏️

There are multiple ways to update a single cell:

```python
print("Before updates:")
print(df)

# Using .loc
df.loc[0, 'age'] = 29

# Using .iloc
df.iloc[1, 1] = 33

# Using .at (fast, label-based)
df.at[2, 'name'] = 'Charles'

# Using .iat (fast, integer-based)
df.iat[2, 1] = 36

print("After updates:")
print(df)
```

## 4. `[]` vs `[[]]` 🧐

* `df['col']` → returns a **Series**
* `df[['col']]` → returns a **DataFrame**

```python
print(type(df['name']))   # Series
print(type(df[['name']])) # DataFrame
```

## 5. Selecting Columns 📑

* `df.loc[col_name]` selects by **row label** (careful!).
* `df.loc[[col_name]]` selects by multiple **row labels**.
* `df[[col1, col2]]` selects multiple **columns**.

```python
# Multiple column selection
print(df[['name', 'age']])
```

## 6. Concatenation 🔗

Concatenation lets you combine DataFrames either **vertically (rows)** or **horizontally (columns)**.

* **Concatenate rows:**

```python
## concat by rows

import pandas as pd

# First DataFrame
df1 = pd.DataFrame({
    "A": [1, 2, 3],
    "B": [4, 5, 6]
})

# Second DataFrame
df2 = pd.DataFrame({
    "A": [7, 8, 9],
    "B": [10, 11, 12]
})

# Concatenate by rows (axis=0)
result = pd.concat([df1, df2], axis=0, ignore_index=False)

print(result)
```

```
   A   B
0  1   4
1  2   5
2  3   6
0  7  10
1  8  11
2  9  12
```

**ignore previous index by using ignore_index=True**

```python
# Concatenate by rows (axis=0)
result = pd.concat([df1, df2], axis=0, ignore_index=True)
```

```
   A   B
0  1   4
1  2   5
2  3   6
3  7  10
4  8  11
5  9  12
```

* **Concatenate columns:**

```python
## concat by column

# First DataFrame
df1 = pd.DataFrame({
    "A": [1, 2, 3],
    "B": [4, 5, 6]
})

# Second DataFrame
df2 = pd.DataFrame({
    "C": ["x", "y", "z"],
    "D": ["p", "q", "r"]
})

# Concatenate by column (axis=1)
result = pd.concat([df1, df2], axis=1)

print(result)
```

```
   A  B  C  D
0  1  4  x  p
1  2  5  y  q
2  3  6  z  r
```

## 7. Conditions in DataFrames 🔍

* **Regular condition:**

```python
print(df[df['age'] > 30])
```

* **AND (&), OR (|), NOT (\~):**

```python
print(df[(df['age'] > 25) & (df['age'] < 35)])
print(df[(df['age'] < 28) | (df['name'] == 'Diana')])
print(df[~(df['age'] == 33)])
```

* **Between:**

```python
print(df[df['age'].between(28, 35)])
```

* **isin:**

```python
print(df[df['name'].isin(['Alice', 'Diana'])])
```

## 8.0 What is `lambda` in Python? 🤔

A **lambda function** is a small, anonymous function in Python. It’s used when you need a quick function without formally defining it with `def`.

```python
# Normal function
def add_one(x):
    return x + 1

# Same thing with lambda
add_one_lambda = lambda x: x + 1

print(add_one(5))        # 6
print(add_one_lambda(5)) # 6
```

Lambdas are often used inside `apply()` for quick, one-line transformations. You’ll see them in action in the next section! 🚀

## 8.1 Using `apply` 🛠️

### Why use `apply`?

The `apply` method lets you run a function on every element (or row/column) of a DataFrame. It’s super useful when:

* You need to transform values without writing loops.
* You want to use custom logic (with `def` or `lambda`).

Think of it as a **shortcut** to apply logic to your whole dataset at once.

### Examples

* **Basic apply:**

```python
# Add 1 to every age
print(df['age'].apply(lambda x: x + 1))
```

* **Last 4 characters of a string:**

```python

def last4(cc):
    return cc[-4:]

df['CC-last4'] = df['CC Number'].apply(last4)

# lambda shortcut
df['CC-last4'] = df['CC Number'].apply(lambda cc: cc[-4:])
```

* **Apply with lambda for new column:**

```python
df['age_squared'] = df['age'].apply(lambda x: x**2)
print(df)
```

### Why apply on rows?

By default, `apply` works **column by column**. But sometimes you need to use **multiple columns at once**. That’s when you add `axis=1`, meaning “apply on each row.”

```python
def get_generous(row):
    tip_perc = 100 * row['tip'] / row['total_bill']
    if tip_perc >= 25:
        return 'Generous'
    else:
        return 'Not-Generous'

df['Description'] = df.apply(get_generous, axis=1)  # axis=1 so the row will be sent        
```

Here we needed both `tip` **and** `total_bill`

```python
df['description'] = df.apply(lambda row: f"{row['name']} is {row['age']} years old", axis=1)
print(df)
```

Here we needed both `name` **and** `age`
## 9. Dropping Stuff 🗑️

* **Drop a row by index:**

```python
df = df.drop(0, axis=0)
print(df)
```

* **Drop a column:**

```python
df = df.drop('age_squared', axis=1)
print(df)
```

