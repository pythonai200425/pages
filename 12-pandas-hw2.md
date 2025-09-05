# Pandas Lesson 2 – Exercises 🎯

Practice your new skills with these exercises. Try to solve them without looking back, and only peek if you get stuck 😉

## 1. Conditions 🔍

Create this DataFrame:

```python
import pandas as pd

df = pd.DataFrame({
    'name': ['Alice', 'Bob', 'Charlie', 'Diana'],
    'age': [22, 35, 19, 40],
    'city': ['Paris', 'London', 'Berlin', 'Paris']
})
print(df)
```

### Tasks

1. Print all rows where `age` is greater than 30
2. Print all rows where `city` is either `"Paris"` or `"London"`
3. Print all rows where `age` is **between 20 and 25**

## 2. Apply on Column 📊

Create this DataFrame:

```python
df = pd.DataFrame({
    'salary': [2500, 4000, 6000, 7500]
})
print(df)
```

### Tasks

1. Create a new column called `salary_tax` that is `10%` of salary
2. Create another column with the **annual_salary** (multiple by 12)

## 3. Apply on Rows 📝

Create this DataFrame:

```python
df = pd.DataFrame({
    'name': ['Alice', 'Bob', 'Charlie'],
    'math': [80, 55, 90],
    'english': [70, 65, 85],
    'science': [60, 75, 95]
})
print(df)
```

### Tasks

1. Use `apply(axis=1)` to calculate the **total score** for each student
2. Add a new column that says `"Pass"` if the average score is above 60, otherwise `"Fail"`

## 4. Add / Replace Row using `.loc` / `.iloc` ➕

Create this DataFrame:

```python
df = pd.DataFrame({
    'name': ['Alice', 'Bob'],
    'age': [25, 30]
})
print(df)
```

### Tasks

1. Add a new row with `.loc` for a student named `Charlie` who is `28` years old
2. Replace the second row’s values (Bob) with `Bobby`, age `32` using `.iloc`

## 5. Update a Cell using `.at` / `.iat` ✏️

Create this DataFrame:

```python
df = pd.DataFrame({
    'name': ['Alice', 'Bob', 'Charlie'],
    'age': [22, 35, 28]
})
print(df)
```

### Tasks

1. Use `.at` to change the student’s name from `Alice` to `Alicia`
2. Use `.iat` to change `Bob`’s age from `35` to `36`

## 6. Concatenation 🔗

Create these DataFrames:

```python
df1 = pd.DataFrame({
    'A': [1, 2, 3],
    'B': [4, 5, 6]
})

df2 = pd.DataFrame({
    'A': [7, 8, 9],
    'B': [10, 11, 12]
})

print("df1:")
print(df1)
print("df2:")
print(df2)
```

### Tasks

1. Concatenate them by **rows** and print the result, ignore_index=True
2. Concatenate them by **columns** and print the result

## 7. More Conditions 🔍

Create this DataFrame:

```python
df = pd.DataFrame({
    'name': ['Book', 'Pen', 'Laptop', 'Phone'],
    'price': [50, 10, 120, 80],
    'quantity': [5, 2, 10, 7]
})
print(df)
```

### Tasks

1. Print products where `price` is greater than 100
2. Print products where `quantity` is either 5 or 10
3. Print products where `price` is between 50 and 80

## 8. Drop Row / Column 🗑️

Create this DataFrame:

```python
df = pd.DataFrame({
    'id': [1, 2, 3],
    'name': ['Alice', 'Bob', 'Charlie'],
    'department': ['HR', 'IT', 'Finance']
})
print(df)
```

### Tasks

1. Drop the first row
2. Drop the `department` column

**Submission email**: [pythonai200425+pandashw2@gmail.com](mailto:pythonai200425+pandashw2@gmail.com)