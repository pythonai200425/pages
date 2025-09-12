# Pandas Lesson 4 – Duplicates, Missing Data, and Joins (Easy Tutorial)

Welcome! This friendly tutorial mirrors the style of your previous lesson and walks through **duplicates**, **missing data**, and **merging DataFrames** in Pandas. Every section explains the *why/where* and shows a small, runnable example you can paste into a notebook.

> Tip: Run the cells in order. All examples are self‑contained and short.

## Duplicate data – why, where, and how to find it

**Why do duplicates happen?**

* Data collected from multiple systems or forms
* Users submitting the same record twice
* Mistakes in ETL/joins (ETL=Extract, Transform, Load)

### `df.duplicated()`

* Returns a **boolean Series** marking rows that are duplicates of previous rows
* `subset` lets you check duplicates on specific column(s)
* `keep` controls which duplicate is considered the “original”: `'first'` (default), `'last'`, or `False` (mark **all** duplicates)

```python
data = {
    "id": [1, 2, 2, 3, 4, 4, 4],
    "name": ["Alice", "Bob", "Bob", "Charlie", "David", "David", "David"],
    "score": [90, 85, 85, 95, 80, 80, 85]
}

df = pd.DataFrame(data)
df[['id', 'name']].value_counts()
df.value_counts()
display(df)

	id	name	score
0	1	Alice	90
1	2	Bob	85
2	2	Bob	85
3	3	Charlie	95
4	4	David	80
5	4	David	80
6	4	David	85

display(df.duplicated())

0    False  Alice   90
1    False  Bob     85
2     True  Bob     85
3    False  Charlie 95
4    False  David   80
5     True  David   80
6    False  David   85
dtype: bool


print(df[df.duplicated()])   # the duplicated rows

    id    name   score
2   2     Bob    85
5   4     David  80

print(df[~df.duplicated()])  # the non-duplicated rows

    id   name     score
0   1    Alice    90
1   2    Bob      85
3   3    Charlie  95
4   4    David    80
6   4    David    85


df[df.duplicated(subset=['id'])]
    id	name	score
2	2	Bob	    85
5	4	David	80
6	4	David	85
```

### `drop_duplicates()`

* Removes duplicate rows
* Same `subset` and `keep` arguments

```python
# Keep the first occurrence per id
print(people.drop_duplicates(subset=["id"], keep="first"))

# Keep the last occurrence per id
print(people.drop_duplicates(subset=["id"], keep="last"))

# Drop all duplicates (keep none)
print(people.drop_duplicates())  # entire-row duplicates only
```

---

## Missing data – why, where, and how to inspect it

**Why do values go missing?**

* Optional fields left blank by users
* Different source systems don’t share the same columns
* Parsing errors (bad date/number) replaced with `NaN`

**Where do you see them?**

* Surveys, sign‑up forms, imported spreadsheets
* Sensor/telemetry feeds with intermittent failures

### `np.nan`, `pd.isna`, `DataFrame.isna`, `DataFrame.notnull`

```python
sales = pd.DataFrame({
    "order_id": [101, 102, 103, 104],
    "city":     ["NYC", "LA", np.nan, "NYC"],
    "amount":   [120.0, np.nan, 80.0, np.nan]
})

print(np.nan)                      # the special missing value marker
print(pd.isna(sales["city"]))     # column-wise missing flags
print(sales.isna())                # DataFrame-wide missing flags
print(sales.notnull())             # the inverse
```

### Counting missing values with `.isna().sum(axis=0/1)`

* `axis=0` → count per **column** (most common)
* `axis=1` → count per **row** (useful to drop rows with too many missing fields)

```python
# Per-column missing counts (axis=0)
print(sales.isna().sum(axis=0))

# Per-row missing counts (axis=1)
print(sales.isna().sum(axis=1))
```

---

## Filling missing values – `apply` vs `fillna`

**Goal:** Replace numeric `NaN`s with the **mean of each column**

### 3.1 Using `apply`

```python
nums = sales.select_dtypes(include=["number"])  # numeric columns only
means = nums.mean(numeric_only=True)

# Use apply to fill each numeric column with its mean
sales_apply = sales.copy()
sales_apply[nums.columns] = sales_apply[nums.columns].apply(
    lambda col: col.fillna(col.mean())
)
print(sales_apply)
```

### 3.2 Using `fillna` directly (short & fast)

```python
sales_fill = sales.copy()
sales_fill = sales_fill.fillna(value={
    "amount": sales["amount"].mean(),
    # city is non-numeric — choose a strategy (mode, placeholder, or leave NaN)
    # "city": sales["city"].mode().iat[0]
})
print(sales_fill)

# Even shorter for all numeric columns at once:
sales_auto = sales.copy()
sales_auto[nums.columns] = sales_auto[nums.columns].fillna(nums.mean())
print(sales_auto)
```

> When to use which?
>
> * **`fillna`** with a mapping/Series is the simplest and vectorized.
> * **`apply`** is handy for custom per-column logic beyond simple means.

## Dropping missing data – `dropna` and `thresh`

* `dropna()` drops rows (or columns) with missing values
* `thresh` keeps rows/columns that have **at least** this many non‑missing values

```python
# Drop rows where ANY value is missing
print(sales.dropna())

# Drop rows where ALL values are missing
print(sales.dropna(how="all"))

# Keep rows with at least 2 non-missing values
print(sales.dropna(thresh=2))

# Drop columns with too many missing values (axis=1)
print(sales.dropna(axis=1, thresh=3))
```

> Practical tips:
>
> * Use `thresh` when you can tolerate a few NaNs per row but not too many
> * Prefer **imputation** (filling) before dropping when data is precious

## Filtering duplicates via boolean indexing – `df[df.duplicated(...)]`

Sometimes you want to **see** the duplicates before removing them.

```python
# All duplicate rows by entire-row equality
dups_all = people[people.duplicated()]
print(dups_all)

# Duplicates by a subset of columns
dups_by_id = people[people.duplicated(subset=["id"], keep=False)]  # mark all
print(dups_by_id.sort_values("id"))
```

## Cheatsheet – parameters to remember

* **`duplicated(subset=..., keep={'first','last',False})`**
* **`drop_duplicates(subset=..., keep=...)`**
* **`isna() / notnull()`**, **`isna().sum(axis=0/1)`**
* **`fillna(value=..., method=...)`**, or per‑column mapping / Series
* **`dropna(how={'any','all'}, thresh=..., axis={0,1})`**

You’re set! Copy any block into your notebook and tweak the numbers as you like. Happy pandas-ing 🐼
