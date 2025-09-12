# Pandas – Exercises 🎯

Practice your new skills with these exercises. Try to solve them without looking back, and only peek if you get stuck 😉

<img src="images/pandas.jpg" />

## Setup – Create Example DataFrames

```python
import pandas as pd
import numpy as np

# DataFrame with duplicates
books = pd.DataFrame({
    "title": ["1984", "Dune", "Dune", "Hamlet", "Hamlet", "Hamlet", "Emma"],
    "author": ["Orwell", "Herbert", "Herbert", "Shakespeare", "Shakespeare", "Shakespeare", "Austen"],
    "year": [1949, 1965, 1965, 1603, 1603, 1609, 1815]
})

# DataFrame with missing values
students = pd.DataFrame({
    "first_name": ["Liam", np.nan, "Noah", "Emma", "Olivia"],
    "last_name": ["Smith", np.nan, "Johnson", "Brown", "Wilson"],
    "age": [20, np.nan, 22, 19, 21],
    "major": ["Math", np.nan, "CS", "History", "Biology"],
    "gpa": [3.5, np.nan, np.nan, 3.7, 3.9],
    "credits": [30, np.nan, np.nan, 25, 40]
})

# Customers and orders for merging
customers = pd.DataFrame({
    "cust_id": [1, 2, 3, 4],
    "name": ["Alice", "Bob", "Clara", "David"]
})

orders = pd.DataFrame({
    "order_id": [101, 102, 103, 104],
    "cust_id": [1, 2, 2, 5],
    "amount": [250, 400, 150, 500]
})
```

## 1. Duplicates 🔁

Q1.1 Use `duplicated()` to find duplicate rows in the `books` DataFrame
Q1.2 Show only the non-duplicated rows
Q1.3 Use `drop_duplicates()` to keep only the last occurrence of each title
Q1.4 How many duplicates exist in the `author` column?

## 2. Missing Data 🕳️

Q2.1 Count missing values per column in the `students` DataFrame
Q2.2 Add a column `missing_count` with the number of NaNs per row
Q2.3 Select only rows where `gpa` is NaN but `first_name` is not null
Q2.4 Which column has the most missing values?

## 3. Filling NaN ✨

Q3.1 Fill missing values in `age` with the mean age
Q3.2 Fill missing values in `gpa` with the minimum gpa
Q3.3 Fill missing values in `credits` with the maximum credits
Q3.4 Which strategy (mean, min, max) seems most realistic here?

## 4. Dropping NaN 🚮

Q4.1 Drop all rows that contain any NaN values
Q4.2 Drop only rows where *all* values are NaN
Q4.3 Keep rows that have at least 3 non-missing values (`thresh=3`)
Q4.4 Drop columns with more than 50% missing values

## 5. Merging Tables 🔗

Use the `customers` and `orders` DataFrames.

Q5.1 Perform an **inner join** between customers and orders
Q5.2 Perform a **left join** (all customers, matching orders if they exist)
Q5.3 Perform a **right join** (all orders, matching customers if they exist)
Q5.4 Perform an **outer join** with the `_merge` indicator
Q5.5 Create two small DataFrames and do a **cross join**

**Submission email**: [pythonai200425+pandashw4@gmail.com](mailto:pythonai200425+pandashw4@gmail.com)
