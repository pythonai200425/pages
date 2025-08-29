
<img src="images/numpy1.png" />

## Random Numbers

```python
np.random.seed(42)  # set seed for reproducibility

np.random.randint(0, 101, (2, 5)) # random integers between 0 and 100
[[51 92 14 71 60]
 [20 82 86 74 74]]
```

**Explanation:**
The **seed** makes random results reproducible. Without a seed, every run generates different random numbers. By setting a fixed seed (e.g., 42), you always get the same sequence — very useful for debugging, teaching, or comparing experiments.

## Filtering Arrays

```python
a = np.array([10, 20, 30, 40, 50])

np.mean(a)
30.0

a > np.mean(a)  # elements greater than mean
[False False False True True]

a[a > np.mean(a)]  # filter elements greater than mean
[40 50]
```

## Conditions with &, |, \~

```python
a = np.array([1, 2, 3, 4, 5, 6])

# Elements greater than 2 and even
a[(a > 2) & (a % 2 == 0)]
[4 6]

# Elements less than 3 or greater than 5
a[(a < 3) | (a > 5)]
[1 2 6]

# Negation (~): elements not greater than 3
a[~(a > 3)]
[1 2 3]
```

## Argmin and Argmax

```python
a = np.array([15, 3, 27, 8])

np.argmin(a) # index of minimum
1

np.argmax(a) # index of maximum
2

B = np.array([[5, 9, 1],
              [7, 3, 8]])

np.argmin(B) # index in flattened array (row-major)
2  # corresponds to element 1

np.argmax(B) # index in flattened array (row-major)
1  # corresponds to element 9

# To get indices in 2D form:
np.unravel_index(np.argmin(B), B.shape)
(0, 2)

np.unravel_index(np.argmax(B), B.shape)
(0, 1)
```
