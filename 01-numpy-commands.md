
<img src="images/numpy1.png" />

## Array Mathematics

```python
a = np.array([1, 2, 3])
b = np.array([4, 5, 6])

a + b   # element-wise addition
[5 7 9]

a - b   # element-wise subtraction
[-3 -3 -3]

a * b   # element-wise multiplication
[ 4 10 18]

a / b   # element-wise division
[0.25 0.4  0.5 ]

a ** 2  # power
[1 4 9]

np.sqrt(b) # square root
[2. 2.236 2.449]
```

## Comparison

```python
a = np.array([1, 2, 3])
b = np.array([1, 4, 3])

a == b
[ True False  True]

a < 2
[ True False False]

np.array_equal(a, b) # compare arrays fully
False
```

## Aggregate Functions

```python
a = np.array([1, 2, 3, 100])
B = np.array([[1, 2, 3],
              [4, 5, 6]])

a.sum()
106

a.min()
1

B.max(axis=0) # column-wise max
[4 5 6]

a.mean()
26.5

np.median(a)
2.5

np.std(a)
≈ 42.45

```

## Copying Arrays

```python
x = np.array([1, 2, 3])

y = np.copy(x) # deep copy
z = x.copy()  # same as np.copy

y[0] = 99
print(x)
[1  2  3]   
```

## Sorting Arrays

```python
a = np.array([3, 1, 2])
a.sort() # in-place sort
[1 2 3]

S = np.array([[3, 2, 1],
              [6, 5, 4]])

np.sort(S, axis=0) # sort by column
[[3 2 1]
 [6 5 4]]

np.sort(S, axis=1) # sort by row
[[1 2 3]
 [4 5 6]]
```

## Subsetting, Slicing, Indexing

```python
a = np.array([1, 2, 3, 4, 5])

a[0]   # first element
1

a[-1]  # last element
5

a[1:4] # slice
[2 3 4]

a[::-1] # reverse
[5 4 3 2 1]

B = np.array([[1, 2, 3],
              [4, 5, 6],
              [7, 8, 9]])

B[0, 0] # element at row 0, col 0
1

B[:, 1] # all rows, col 1
[2 5 8]

B[1, :] # row 1
[4 5 6]
```
