# NumPy Exercises with Solutions

### 1. Make a Python list of integers \[1, 2, 3, 4, 5] and convert it to a NumPy array

```python
import numpy as np

lst = [1, 2, 3, 4, 5]
a = np.array(lst)
print(a)
[1 2 3 4 5]
```

### 2. Create a NumPy array from the list \[1, 2, 3, 4, 5, 6] and reshape it

#### Shape (2, 3)

```python
arr = np.array([1, 2, 3, 4, 5, 6])
arr.reshape(2, 3)
[[1 2 3]
 [4 5 6]]
```

#### Shape (3, 2)

```python
arr.reshape(3, 2)
[[1 2]
 [3 4]
 [5 6]]
```

### 3. Create a 3×4 array filled with zeros

```python
np.zeros((3, 4))
[[0. 0. 0. 0.]
 [0. 0. 0. 0.]
 [0. 0. 0. 0.]]
```

## 4. Create a 2×5 array filled with ones

```python
np.ones((2, 5))
[[1. 1. 1. 1. 1.]
 [1. 1. 1. 1. 1.]]
```

### 5. Create a 4×4 array with random floats between 0 and 1

```python
np.random.random((4, 4))
[[0.12 0.85 0.66 0.41]
 [0.73 0.99 0.35 0.57]
 [0.88 0.01 0.27 0.61]
 [0.42 0.33 0.15 0.95]]   # values will vary
```

### 6. Create a 3×3 array with random integers between 10 and 100

```python
np.random.randint(10, 101, (3, 3))
[[45 78 55]
 [92 64 33]
 [27 88 99]]   # values will vary
```

### 7. Set NumPy’s random seed to 42 and generate the 3×3 random integer array again

```python
np.random.seed(42)
np.random.randint(10, 101, (3, 3))
[[52 93 15]
 [72 61 21]
 [83 87 75]]
```

#### 7.1. Take the 3×3 array from above and reshape it into a 1×9 array

```python
arr = np.array([[52, 93, 15],
                [72, 61, 21],
                [83, 87, 75]])

arr.reshape(1, 9)
[[52 93 15 72 61 21 83 87 75]]
```

### 8. Create a 1D array of numbers from 0 to 20 with step size 2

```python
np.arange(0, 21, 2)
[ 0  2  4  6  8 10 12 14 16 18 20]
```

### 9. Create an array of 10 equally spaced numbers between 0 and 1

```python
np.linspace(0, 1, 10)
[0.   0.11 0.22 0.33 0.44 0.56 0.67 0.78 0.89 1.  ]
```
