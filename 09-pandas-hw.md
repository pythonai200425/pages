## Exercise: Working with DataFrames

### Step 1: Create a DataFrame
Run the following code to create a sample DataFrame:

```python
import pandas as pd

data = {
    "Name": ["Alice", "Bob", "Charlie", "Diana", "Evan"],
    "Age": [25, 30, 35, 28, 40],
    "Salary": [50000, 60000, 75000, 62000, 80000],
    "Department": ["HR", "IT", "Finance", "IT", "HR"]
}

df = pd.DataFrame(data)
print(df)
```

### Tasks

1. **Select rows and columns with `.iloc`**  
   - Get the first 3 rows and only the `Name` and `Salary` columns 

2. **Add a new calculated column**  
   - Create a column `Bonus` that is 10% of the `Salary` 

3. **Change the index**  
   - Set the `Name` column as the new index 
   - Display all rows from `Bob` to `Diana` and only `Salary` and `Department` columns
   - Then reset it back to the default numeric index

**Submission email**: [pythonai200425+pandashw@gmail.com](mailto:pythonai200425+pandashw@gmail.com)