# ECE2112_PA3

FLORENCE MIGUEL S. ARAGA | 2ECE-A
# EXPERIMENT 3: PYTHON DATA ANALYSIS (PANDAS)

## Objective

The objective of this laboratory activity is to demonstrate fundamental data manipulation and wrangling techniques using the **Pandas** library in Python. Specifically, this experiment aims to:

1. **Load Data**: Import a structured CSV dataset (`cars.csv`) into a Pandas DataFrame named `cars`.
2. **Apply Indexing Techniques**: Select specific subsets of rows and columns using positional-based (`.iloc`) and label-based (`.loc` / bracket notation) indexing.
3. **Filter Data via Boolean Conditions**: Query records dynamically based on conditional logic on the `Model` column rather than using hard-coded index locations.
4. **Extract Non-Destructive Subsets**: Isolate well-defined subsets of data into new DataFrames and Series without modifying the original source dataset.

---

## Laboratory Setup & Prerequisites

Before running the code in your Jupyter Notebook, ensure you have the required environment set up:

- **Python Version**: `3.x`
- **Required Libraries**: `pandas`
- **File Structure**: Keep `cars.csv` in the same directory as your Jupyter Notebook file (`.ipynb`).

```bash
# Installation (if Pandas is not installed)
pip install pandas

import pandas as pd

# Load the dataset
cars = pd.read_csv('cars.csv')

Part A: Positional and Label-Based Slicing
Discussion
Positional slicing using .iloc allows access to elements by their zero-based integer index. When selecting "rows 6 through 10, where the first data row is row 1", we are targeting 1-based row numbers 6 to 10. In 0-based Python indexing, these correspond to indices 5 through 9. Using Python's slice notation [start:stop], the range 5:10 includes indices 5, 6, 7, 8, and 9.

Label-based selection retrieves columns explicitly by name, ensuring the selected data maintains a precise, deterministic structure regardless of underlying column positions.

# a. Display shape and column names
print("Dataset Shape:", cars.shape)
print("\nColumn Names:")
print(cars.columns.tolist())

# b. Positional slicing for 1-based rows 6 to 10 using iloc
# (1-based rows 6-10 correspond to 0-based index range 5:10)
cars_6_to_10 = cars.iloc

# c. Display specified columns using label selection
selected_columns = ['Model', 'mpg', 'cyl', 'hp', 'gear']
cars_6_to_10_subset = cars_6_to_10[selected_columns]

# Display result
cars_6_to_10_subset
