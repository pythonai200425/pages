# Pandas – Merge Tutorial

Merging is one of the most powerful tools in Pandas for combining datasets  
Here we’ll explore the five common types of merges: **inner, left, right, outer, and cross**

## Create Example Tables

```python
import pandas as pd

customers = pd.DataFrame({
    "cust_id": [1, 2, 3, 4],
    "name": ["Ana", "Ben", "Cai", "Dee"]
})

orders = pd.DataFrame({
    "order_id": [10, 11, 12, 13],
    "cust_id": [1, 2, 2, 5],
    "amount": [50, 75, 40, 99]
})

print("Customers:")
print(customers)

print("\nOrders:")
print(orders)
```

**Customers:**

```
   cust_id  name
0        1   Ana
1        2   Ben
2        3   Cai
3        4   Dee
```

**Orders:**

```
   order_id  cust_id  amount
0        10        1      50
1        11        2      75
2        12        2      40
3        13        5      99
```

## Inner Join

```python
print(pd.merge(customers, orders, on="cust_id", how="inner"))
```

Output:

```
   cust_id  name  order_id  amount
0        1   Ana        10      50
1        2   Ben        11      75
2        2   Ben        12      40
```

✅ Keeps only rows with matching `cust_id` in **both** tables

## Left Join

```python
print(pd.merge(customers, orders, on="cust_id", how="left"))
```

Output:

```
   cust_id  name  order_id  amount
0        1   Ana      10.0    50.0
1        2   Ben      11.0    75.0
2        2   Ben      12.0    40.0
3        3   Cai       NaN     NaN
4        4   Dee       NaN     NaN
```

✅ Keeps **all customers**, adds orders where available, otherwise `NaN`

## Right Join

```python
print(pd.merge(customers, orders, on="cust_id", how="right"))
```

Output:

```
   cust_id  name  order_id  amount
0        1   Ana        10      50
1        2   Ben        11      75
2        2   Ben        12      40
3        5   NaN        13      99
```

✅ Keeps **all orders**, adds customers where available, otherwise `NaN`

## Outer Join

```python
print(pd.merge(customers, orders, on="cust_id", how="outer", indicator=True))
```

Output:

```
   cust_id  name  order_id  amount     _merge
0        1   Ana      10.0    50.0       both
1        2   Ben      11.0    75.0       both
2        2   Ben      12.0    40.0       both
3        3   Cai       NaN     NaN  left_only
4        4   Dee       NaN     NaN  left_only
5        5   NaN      13.0    99.0  right_only
```

✅ Keeps **everything** from both tables, marking the source with `_merge`

## Cross Join

```python
left = pd.DataFrame({"L": ["A", "B"]})
right = pd.DataFrame({"R": [1, 2, 3]})
print(left.merge(right, how="cross"))
```

Output:

```
   L  R
0  A  1
1  A  2
2  A  3
3  B  1
4  B  2
5  B  3
```

✅ Produces the **Cartesian product** of the two tables (all combinations)

That’s the complete overview of merges in Pandas 🐼
