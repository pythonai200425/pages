# NumPy Basics

## What is NumPy?

NumPy (Numerical Python) is a core Python library for numerical and scientific computing.
It provides a powerful object called **ndarray**, which is a fast, flexible multidimensional array, along with functions for mathematical operations, linear algebra, random number generation, and more.

---

## Installing NumPy in Jupyter

To install NumPy inside a Jupyter Notebook:

```python
%pip install numpy
```

Then import it:

```python
import numpy as np
```

---

## Working with Axes (`axis=0` vs `axis=1`)

In NumPy, operations can be applied along different **axes**:

* **axis=0** → operates down the rows (column-wise)
* **axis=1** → operates across the columns (row-wise)

Example:

```python
x = np.array([[1, 2, 3],
              [4, 5, 6]])

x.sum(axis=0)   # [5, 7, 9] (column sums)
x.sum(axis=1)   # [6, 15]   (row sums)
```

---

## Creating Arrays

```python
a = np.array([1, 2, 3]) # 1D array
[1 2 3]

b = np.array([(1.5, 2, 3), (4, 5, 6)], float) # 2D float array
[[1.5  2.  3. ]
 [4.   5.  6. ]]

c = np.array([[[1, 2, 3], [4, 5, 6]],
              [[3, 2, 1], [4, 5, 6]]], float) # 3D array
[[[1. 2. 3.]
  [4. 5. 6.]]

 [[3. 2. 1.]
  [4. 5. 6.]]]
```

---

## Initial Placeholders

```python
np.zeros((3, 4)) # 3x4 array of zeros
[[0. 0. 0. 0.]
 [0. 0. 0. 0.]
 [0. 0. 0. 0.]]

np.ones((2, 3), dtype=np.int16) # 2x3 array of ones with int16 dtype
[[1 1 1]
 [1 1 1]]

np.arange(10, 25, 5) # array with step size
[10 15 20]

np.linspace(0, 2, 5) # 5 evenly spaced samples from 0 to 2
[0.  0.5 1.  1.5 2. ]

np.full((2, 2), 7) # constant array
[[7 7]
 [7 7]]

np.eye(2) # identity matrix
[[1. 0.]
 [0. 1.]]

np.random.random((2, 2)) # random floats in [0,1)
[[0.42 0.88]
 [0.14 0.77]]   # (example values)

np.empty((2, 2)) # uninitialized array (arbitrary values)
[[1.23 4.56]
 [7.89 0.12]]   # (example values)
```

---

## Inspecting Arrays

```python
a = np.array([1, 2, 3])

a.shape      # dimensions
(3,)

len(a)       # length of first dimension
3

a.ndim       # number of dimensions
1

a.size       # total number of elements
3

a.dtype      # data type
dtype('int64')

a.dtype.name # name of data type
'int64'

a.astype(float) # convert to float (returns new array)
[1. 2. 3.]
```
