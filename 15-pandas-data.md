# Pandas – Duplicates, Missing Data

## Duplicate data – why, where, and how to find it

**Why do duplicates happen?**

* Data collected from multiple systems or forms
* Users submitting the same record twice
* Mistakes in ETL/joins (ETL=Extract, Transform, Load)

### `df.duplicated()`

* Returns a **boolean Series** marking rows that are duplicates of previous rows
* `subset` lets you check duplicates on specific column(s)
**all** duplicates)

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
* Same `subset` 
* `keep` controls which duplicate is considered the “original”: `'first'` (default), `'last'`, or `False` (mark 

```python

	id	name	 score
0	1	Alice	 90
1	2	Bob	     85
2	2	Bob	     85
3	3	Charlie	 95
4	4	David	 80 <--
5	4	David	 80 
6	4	David	 85 <--

# Keep the first occurrence per id
print(df.drop_duplicates(subset=["id"], keep="first"))

	id	name	 score
0	1	Alice 	 90
1	2	Bob 	 85
3	3	Charlie  95
4	4	David	 80 <---

# Keep the last occurrence per id
print(peopdfle.drop_duplicates(subset=["id"], keep="last"))

	id	name	 score
0	1	Alice 	 90
2	2	Bob	     85
3	3	Charlie	 95
6	4	David	 85 <---
```

## Missing data – why, where, and how to inspect it

**Why do values go missing?**

* Optional fields left blank by users
* Different source systems don’t share the same columns
* Parsing errors (bad date/number) replaced with `NaN`

**Where do you see them?**

* Surveys, sign‑up forms, imported spreadsheets
* Sensor/telemetry feeds with intermittent failures

### Understanding `NaN` in Pandas and Python

When working with **missing values** in Pandas (and NumPy), you’ll often see `NaN` (Not a Number).  

#### Important rule:  
`NaN` is **not equal** to anything, not even itself therefor we need to use ``is``

```python
import numpy as np
import pandas as pd

x = np.nan
print(x == np.nan)   # False
print(pd.isna(x))    # True
```

### `np.nan`, `pd.isna`, `DataFrame.isna`, `DataFrame.notnull`

```python
import pandas as pd
import numpy as np

data = {
    "first_name": ["Tom", np.nan, "Hugh", "Oprah", "Emma"],
    "last_name": ["Hanks", np.nan, "Jackman", "Winfrey", "Stone"],
    "age": [63.0, np.nan, 51.0, 66.0, 31.0],
    "sex": ["m", np.nan, "m", "f", "f"],
    "pre_movie_score": [8.0, np.nan, np.nan, 6.0, 7.0],
    "post_movie_score": [10.0, np.nan, np.nan, 8.0, 9.0]
}

	first_name	last_name	age	   sex	pre_movie_score	 post_movie_score
0	Tom	        Hanks	    63.0   m	8.0	             10.0
1	NaN	        NaN	        NaN	   NaN	NaN	             NaN
2	Hugh	    Jackman	    51.0   m	NaN	             NaN
3	Oprah	    Winfrey	    66.0   f	6.0	             8.0
4	Emma	    Stone	    31.0   f	7.0	             9.0

display(df.isna())

	first_name	last_name	age	sex	pre_movie_score	 post_movie_score
0	False	    False	    False	False	  False	 False
1	True	    True	    True	True	  True	 True
2	False	    False	    False	False	  True	 True
3	False	    False	    False	False	  False	 False
4	False	    False	    False	False	  False	 False

df['number_of_missing'] = df.isna().sum(axis=1)  # count per row
display(df)

	first_name	last_name	age	   sex	pre_movie_score	 post_movie_score  number_of_missing
0	Tom	        Hanks	    63.0   m	8.0	             10.0              0
1	NaN	        NaN	        NaN	   NaN	NaN	             NaN               6
2	Hugh	    Jackman	    51.0   m	NaN	             NaN               2
3	Oprah	    Winfrey	    66.0   f	6.0	             8.0               0
4	Emma	    Stone	    31.0   f	7.0	             9.0               0

display(df['pre_movie_score'].isna().sum(axis=0))  # count per column
2

```

## using nan in conditions

```python

	first_name	last_name	age	   sex	pre_movie_score	 post_movie_score
0	Tom	        Hanks	    63.0   m	8.0	             10.0
1	NaN	        NaN	        NaN	   NaN	NaN	             NaN
2	Hugh	    Jackman	    51.0   m	NaN	             NaN
3	Oprah	    Winfrey	    66.0   f	6.0	             8.0
4	Emma	    Stone	    31.0   f	7.0	             9.0

display(df[(df['pre_movie_score'].isna() & df['first_name'].notnull())])

	first_name	last_name	age	sex	pre_movie_score	post_movie_score
2	Hugh	    Jackman	    51.0   m	NaN	             NaN


```

## Filling missing values – `apply` vs `fillna`

**Filling Missing Values with Mean, Min, and Max**

When handling missing data, one common strategy is **imputation** — replacing `NaN` with a meaningful value instead of dropping the row or column  
In Pandas, we often use **mean, min, or max** of a column to fill in the blanks.

**Goal:** Replace numeric `NaN`s with the **mean of each column**

```python
	first_name	last_name	age	   sex	pre_movie_score	 post_movie_score  number_of_missing
0	Tom	        Hanks	    63.0   m	8.0	             10.0              0
1	NaN	        NaN	        NaN	   NaN	NaN	             NaN               6
2	Hugh	    Jackman	    51.0   m	NaN	             NaN               2
3	Oprah	    Winfrey	    66.0   f	6.0	             8.0               0
4	Emma	    Stone	    31.0   f	7.0	             9.0               0
```

### Using `apply`

```python
def neewval(x):
    if pd.isna(x):
        return df['pre_movie_score'].mean()
    else:
        return x

df['pre_movie_score'] = df['pre_movie_score'].apply(neewval)

# using lambda
df['pre_movie_score'] = df['pre_movie_score'].apply(lambda x: df['pre_movie_score'].mean() if pd.isna(x) else x)


	first_name	last_name	age	   sex	pre_movie_score	 post_movie_score  number_of_missing
0	Tom	        Hanks	    63.0   m	8.0	             10.0              0
1	NaN	        NaN	        NaN	   NaN	7.0	             NaN               6
2	Hugh	    Jackman	    51.0   m	7.0	             NaN               2
3	Oprah	    Winfrey	    66.0   f	6.0	             8.0               0
4	Emma	    Stone	    31.0   f	7.0	             9.0               0
```

### Using `fillna` directly (short & fast)

```python

df['pre_movie_score'] = df['pre_movie_score'].fillna(df['pre_movie_score'].mean())

	first_name	last_name	age	   sex	pre_movie_score	 post_movie_score  number_of_missing
0	Tom	        Hanks	    63.0   m	8.0	             10.0              0
1	NaN	        NaN	        NaN	   NaN	7.0	             NaN               6
2	Hugh	    Jackman	    51.0   m	7.0	             NaN               2
3	Oprah	    Winfrey	    66.0   f	6.0	             8.0               0
4	Emma	    Stone	    31.0   f	7.0	             9.0               0
```

## Dropping missing data – `dropna` and `thresh`

* `dropna()` drops rows (or columns) with missing values
* `thresh` keeps rows/columns that have **at least** this many non‑missing values

```python

	first_name	last_name	age	   sex	pre_movie_score	 post_movie_score  number_of_missing
0	Tom	        Hanks	    63.0   m	8.0	             10.0              0
1	NaN	        NaN	        NaN	   NaN	NaN	             NaN               6
2	Hugh	    Jackman	    51.0   m	NaN	             NaN               2
3	Oprah	    Winfrey	    66.0   f	6.0	             8.0               0
4	Emma	    Stone	    31.0   f	7.0	             9.0               0

df.dropna()  # drop every row which has at least 1 NaN

	first_name	last_name	age	   sex	pre_movie_score	 post_movie_score  number_of_missing
0	Tom	        Hanks	    63.0   m	8.0	             10.0              0
3	Oprah	    Winfrey	    66.0   f	6.0	             8.0               0
4	Emma	    Stone	    31.0   f	7.0	             9.0               0

df.dropna(thresh=1)  # keep only rows with at least 1 not null

	first_name	last_name	age	   sex	pre_movie_score	 post_movie_score  number_of_missing
0	Tom	        Hanks	    63.0   m	8.0	             10.0              0
2	Hugh	    Jackman	    51.0   m	NaN	             NaN               2
3	Oprah	    Winfrey	    66.0   f	6.0	             8.0               0
4	Emma	    Stone	    31.0   f	7.0	             9.0               0
```

## Cheatsheet – parameters to remember

* **`duplicated(subset=..., keep={'first','last',False})`**
* **`drop_duplicates(subset=..., keep=...)`**
* **`isna() / notnull()`**, **`isna().sum(axis=0/1)`**
* **`fillna(value=..., method=...)`**, or per‑column mapping / Series
* **`dropna(how={'any','all'}, thresh=..., axis={0,1})`**

You’re set! Copy any block into your notebook and tweak the numbers as you like. Happy pandas-ing 🐼
