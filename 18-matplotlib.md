<img src="images/matplotlib.png" />

# What is Matplotlib?

**Matplotlib** is a powerful Python library for creating visualizations and plots. It lets you draw line charts, scatter plots, bar charts, histograms, and more, with full control over appearance and layout.

---

## Creating a Simple Line Graph

```python
import numpy as np
import matplotlib.pyplot as plt

x = np.arange(0, 10)
y = 2 * x + 1

plt.plot(x, y)
plt.title('Hours vs Production')
plt.xlabel('Hours')
plt.ylabel('Production')
plt.xlim(0, 12)
plt.ylim(0, 20)
plt.legend(['Production'])
plt.grid(True)
plt.savefig('line_chart1.jpg')
plt.show()
```

**Features:**
- `title`, `xlabel`, `ylabel` for labeling
- `xlim`, `ylim` for axis limits
- `legend` for labeling lines
- `grid` for background grid
- `savefig` to save the plot as an image

---

## Customizing Graphs: Markers, Line Width, Style

```python
x = np.linspace(0, 10, 100)
y1 = np.sin(x)
y2 = np.cos(x)

fig, ax = plt.subplots(figsize=(8, 6))
ax.plot(x, y1, label='Sine Wave', color='#15d15a', lw=10, ls='--', marker='o', markersize=8)
ax.plot(x, y2, label='Cosine Wave', color='red', lw=3, linestyle='-', marker='x', markersize=8)
ax.set_title('Customized Chart', fontsize=24)
ax.set_xlabel('X-axis', fontsize=12)
ax.set_ylabel('Y-axis', fontsize=12)
ax.legend()
ax.grid(True)
plt.tight_layout()
plt.show()
```

**Features:**
- `color`, `lw` (line width), `ls` (line style), `marker`, `markersize` for customizing lines

---

## Drawing Multiple Graphs: figure, add_axes, subplots

### Using `figure` and `add_axes`

```python
fig = plt.figure(figsize=(6.4, 4.8))
graph1 = fig.add_axes([0, 0, 1, 1])
x = np.arange(0, 10)
y = 2 * x + 1
graph1.plot(x, y)
graph1.set_title('Hours vs Production')
graph1.set_xlabel('Hours')
graph1.set_ylabel('Production')

# Add a zoomed-in graph
graph2 = fig.add_axes([0.1, 0.5, 0.25, 0.3])
a = np.arange(0, 10)
b = a ** 4
graph2.plot(a, b)
graph2.set_title('Zoom In')
plt.show()
```

### Using `subplots`

```python
fig, axes = plt.subplots(nrows=1, ncols=2, figsize=(8, 4))
x = np.arange(0, 10)
y = np.arange(0, 10)
axes[0].plot(x, y)
axes[0].set_title('Linear')
axes[1].plot(x, y**2, label='Quadratic', color='red')
axes[1].set_title('Quadratic')
axes[1].legend()
axes[1].grid(True)
plt.tight_layout()
plt.show()
```

---

## Drawing Two Graphs in the Same Axis

```python
fig, ax = plt.subplots()
x = np.arange(0, 11)
y1 = x
y2 = x**2
ax.plot(x, y1, label='X vs X')
ax.plot(x, y2, label='X vs X^2')
ax.set_xlabel('X [1..10]')
ax.legend()
fig.suptitle('2 functions')
plt.show()
```

---

## Scatter Plot

```python
x = np.arange(10)
y_scatter = np.random.randn(10)
plt.scatter(x, y_scatter)
plt.title('Scatter Plot')
plt.show()
```

---

## Bar Plot

```python
bar_cat = ['A', 'B', 'C', 'D', 'E']
bar_values = np.random.randn(5) + 5
plt.bar(bar_cat, bar_values, color='orange')
plt.title('Bar Plot')
plt.show()
```

---

## Histogram

```python
y_hist = np.random.randn(1000)
plt.hist(y_hist, bins=18, color='b', alpha=0.7)
plt.title('Histogram')
plt.show()
```

---

## Grouped Bar Plot Example

```python
df = pd.read_csv("tips.csv")
tips_per_gender = df.groupby('sex')['tip'].mean().round(2)
plt.bar(tips_per_gender.index, tips_per_gender.values)
plt.title('Average Tip by Gender')
plt.show()
```

---

# Summary

Matplotlib lets you create and customize a wide variety of charts. Use features like grid, legend, axis limits, and subplots to make your visualizations clear and informative. Try combining these techniques for your own data analysis!
