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

## Where to Do This Activity

This laboratory activity should be written, executed, and documented in a **Jupyter Notebook (`.ipynb`)**. You can set up and run your environment using any of the following options:

### 1. Local Setup (Recommended)
- **Anaconda Navigator**: Open Anaconda Navigator and launch **Jupyter Notebook** or **JupyterLab**.
- **VS Code**: Install the Python and Jupyter extensions in Visual Studio Code, then create a new file named `Experiment_4.ipynb`.

### 2. Cloud-Based Platform
- **Google Colab**: Go to [colab.research.google.com](https://colab.research.google.com/), create a new notebook, and upload the `cars.csv` file into the session storage before executing your code.

---

## Laboratory Setup & Prerequisites

Before running the code in your Jupyter Notebook, ensure you have the required environment set up:

- **Python Version**: `3.x`
- **Required Libraries**: `pandas`
- **File Structure**: Keep `cars.csv` in the same directory as your Jupyter Notebook file (`.ipynb`).

```bash
# Installation (if Pandas is not installed locally)
pip install pandas
```
### Detailed Discussion & Code Implementation

Import Pandas and load the dataset into a DataFrame called `cars`:

```
import pandas as pd

`# Load the dataset`
cars = pd.read_csv('cars.csv')
```

## Part A: Positional and Label-Based Slicing

Discussion

Positional slicing using .iloc allows access to elements by their zero-based integer index. When selecting "rows 6 through 10, where the first data row is row 1", we are targeting 1-based row numbers 6 to 10. In 0-based Python indexing, these correspond to indices 5 through 9. Using Python's slice notation [start:stop], the range 5:10 includes indices 5, 6, 7, 8, and 9.

Label-based selection retrieves columns explicitly by name, ensuring the selected data maintains a precise, deterministic structure regardless of underlying column positions.

```
`# a. Display shape and column names`
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
```
## Part B: Model Lookup

Discussion

Hard-coding row numbers (e.g., assuming "Toyota Corolla" is at row 20) makes data pipelines fragile and prone to breaking when datasets are updated, re-ordered, or appended. Boolean indexing evaluates a conditional logic statement against a DataFrame column, returning a boolean mask (True/False).

By passing this mask into the DataFrame using .loc[], Pandas dynamically filters and extracts only matching rows alongside the desired column labels.

```
# a. Complete row for Toyota Corolla using Boolean indexing
toyota = cars.loc[cars['Model'] == 'Toyota Corolla']

# b. Selected columns for Pontiac Firebird using Boolean indexing
pontiac = cars.loc[cars['Model'] == 'Pontiac Firebird', ['Model', 'mpg', 'hp', 'wt']]

# Display results
print("--- Toyota Corolla ---")
display(toyota)

print("\n--- Pontiac Firebird ---")
display(pontiac)
```

## Part C: Multi-Model Subsetting

Discussion

To filter a DataFrame across multiple categorical values without writing long chain operations with | (OR operators), Pandas provides the .isin() method. It evaluates whether each element in a column matches any value within a given list. Combining .isin() with .loc[] allows simultaneous dynamic row filtering and explicit column selection.

```
# Define target models and columns
target_models = ['Datsun 710', 'Lotus Europa', 'Ferrari Dino']
target_cols = ['Model', 'mpg', 'cyl', 'hp', 'gear']

# Filter rows by model values and select required columns
selected_cars = cars.loc[cars['Model'].isin(target_models), target_cols]

# Display selected DataFrame and its dimensions
display(selected_cars)
print("Shape of selected_cars:", selected_cars.shape)

# Required assertion check
assert selected_cars.shape == (3, 5), "Error: Shape must be exactly 3 rows and 5 columns."
print("Validation Successful: Shape is exactly (3, 5).")
```
