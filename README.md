# ECE2112_PA3
EXPERIMENT 3: PYTHON DATA ANALYSIS (PANDAS)

FLORENCE MIGUEL S. ARAGA | 2ECE-A
# Pandas Data Wrangling: Subsetting, Indexing, and Filtering

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
