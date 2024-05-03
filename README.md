# PRODGY_DS_02

# Task: Exploratory Data Analysis with Pandas and Matplotlib

## Description
This task involves conducting exploratory data analysis (EDA) on a dataset using Pandas and Matplotlib. The dataset is loaded from an Excel file named "data.xlsx". The analysis includes:
- Displaying the first few rows of the dataset.
- Checking for missing values and handling them.
- Calculating descriptive statistics.
- Exploring relationships between variables, such as product quantities and total sales.

## Requirements
- Python 3.x
- pandas
- matplotlib

## Installation
1. Install Python if you haven't already. You can download it from [here](https://www.python.org/downloads/).
2. Install pandas using pip:
3. Install matplotlib using pip:


## Usage
1. Make sure you have the `data.xlsx` file in the same directory as your Python script.
2. Run the provided Python script `exploratory_data_analysis.py`.
3. View the outputs generated during the exploratory data analysis.

## Files
- `exploratory_data_analysis.py`: Python script for conducting exploratory data analysis.

## Example
```python
import pandas as pd
import matplotlib.pyplot as plt

# Load the data from the Excel file
data = pd.read_excel("data.xlsx")

# Store the first few rows of the dataset in a DataFrame
data_head_df = data.head()

# Display the DataFrame
print("First few rows of the dataset:")
print(data_head_df)

# Check for missing values
missing_values = data.isnull().sum()

# Store the missing values in a DataFrame
missing_values_df = pd.DataFrame({'Missing Values': missing_values})

# Display the DataFrame
print("\nMissing values in the dataset:")
print(missing_values_df)

# Handle missing values (for demonstration purposes, let's assume we drop rows with any missing values)
data.dropna(inplace=True)

# Calculate descriptive statistics
descriptive_stats = data.describe()

# Convert descriptive statistics to a DataFrame
descriptive_stats_df = descriptive_stats.transpose()

# Display the DataFrame
print("\nDescriptive statistics:")
print(descriptive_stats_df)

# Explore relationships between variables
# Visualize the distribution of product quantities
plt.figure(figsize=(8, 6))
plt.hist(data['PROD_QTY'], bins=20, color='skyblue', edgecolor='black')
plt.title('Distribution of Product Quantities')
plt.xlabel('Product Quantity')
plt.ylabel('Frequency')
plt.grid(True)
plt.show()

# Explore the relationship between product quantity and total sales
plt.figure(figsize=(8, 6))
plt.scatter(data['PROD_QTY'], data['TOT_SALES'], color='orange', alpha=0.5)
plt.title('Product Quantity vs Total Sales')
plt.xlabel('Product Quantity')
plt.ylabel('Total Sales')
plt.grid(True)
plt.show()

# Calculate average total sales per store
average_sales_per_store = data.groupby('STORE_NBR')['TOT_SALES'].mean()

# Store the average sales per store in a DataFrame
average_sales_per_store_df = pd.DataFrame({'Store Number': average_sales_per_store.index, 'Average Total Sales': average_sales_per_store.values})

# Display the DataFrame
print("\nAverage total sales per store:")
print(average_sales_per_store_df)
