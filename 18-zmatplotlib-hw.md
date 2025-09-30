# Matplotlib – Exercises 🎯

Practice your plotting skills with these hands‑on tasks. Stick to **matplotlib** (no seaborn) and save each figure as requested

## 1. Linear Model – Taxi Fare vs Distance 🚕

A city taxi charges a base fare plus a fixed rate per kilometer:

> **fare = 8 + 5 × distance_km**

**Tasks**

1. Create `x = np.arange(0, 11)` to represent 0–10 kilometers
2. Compute `y = 8 + 5 * x` for the taxi fare
3. Plot the line with: title, x/y labels, and legend
4. Limit the axes to `xlim(0, 10)` and `ylim(0, 60)`
5. Save as **taxi_fare_line.jpg** and show the plot

## 2. Visual Analysis with `tips.csv` 🍽️

```python
df = pd.read_csv("tips.csv")
```

Link to  <a hef="csv/tips.cvs">tips.csv</a>

### 2.1. Scatter: price_per_person (x) vs tip (y)

* Create a scatter plot of `price_per_person` (x-axis) vs `tip` (y-axis)
* Add title and axis labels
* **Bonus**: compute Pearson correlation and add it to the title

```python
plt.scatter(df["price_per_person"], df["tip"])
plt.title("Tip vs Price per Person")
plt.xlabel("Price per person")
plt.ylabel("Tip")
# Bonus (optional):
# r = np.corrcoef(df["price_per_person"], df["tip"])[0, 1]
# plt.title(f"Tip vs Price per Person (r={r:.2f})")
plt.savefig("tips_scatter.jpg", dpi=150, bbox_inches="tight")
plt.show()
```

### 2.2. Bar: maximum total_bill per day

* For each `day`, find the **max total_bill**
* Plot a bar chart of these maxima

```python
max_per_day = df.groupby("day")["total_bill"].max()
plt.bar(max_per_day.index.astype(str), max_per_day.values)
plt.title("Max Total Bill per Day")
plt.xlabel("Day")
plt.ylabel("Max total_bill")
plt.savefig("tips_bar_max_per_day.jpg", dpi=150, bbox_inches="tight")
plt.show()
```

### 2.3. Histogram: tips

* Plot a histogram of `tip`
* **Question**: *What is the range (bin) of the most common tip?*
  Hint: use the tuple returned by `n, bins, _ = plt.hist(...)` to identify the bin with `n.argmax()`

```python
n, bins, _ = plt.hist(df["tip"], bins=10)
plt.title("Distribution of Tips")
plt.xlabel("Tip amount")
plt.ylabel("Frequency")
plt.savefig("tips_hist_tip.jpg", dpi=150, bbox_inches="tight")
plt.show()

# Determine the most common bin range (optional)
most = n.argmax()
most_common_range = (bins[most], bins[most+1])
print("Most common tip range:", most_common_range)
```

### 2.4. Histogram: tip percentage

* Create a new column `tip_perc = 100 * tip / total_bill`
* Plot a histogram of `tip_perc`
* **Question**: *What is the range of the most common tip percentage?*

```python
df["tip_perc"] = 100 * df["tip"] / df["total_bill"]

n2, bins2, _ = plt.hist(df["tip_perc"], bins=10)
plt.title("Distribution of Tip Percentage")
plt.xlabel("Tip %")
plt.ylabel("Frequency")
plt.savefig("tips_hist_tip_perc.jpg", dpi=150, bbox_inches="tight")
plt.show()

most2 = n2.argmax()
most_common_tip_perc_range = (bins2[most2], bins2[most2+1])
print("Most common tip % range:", most_common_tip_perc_range)
```

### 2.5. Subplots: combine all four visuals

* Create a **2×2** grid using `fig, axes = plt.subplots(2, 2, figsize=(10, 7))`
* Recreate the four plots in their own axes objects:
  (1) scatter, (2) bar of max per day, (3) tip histogram, (4) tip% histogram
* Make sure each subplot has a title and labeled axes
* Adjust layout and save as **tips_overview.png**

**Submission email**: [pythonai200425+matplothw1@gmail.com](mailto:pythonai200425+matplothw1@gmail.com)