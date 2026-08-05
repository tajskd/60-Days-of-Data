# Day 12 – Advanced Python: Merging, Joining, and Handling Missing Data

## Overview
Today I learned how to combine multiple tables in Python, simulating real-world scenarios where data comes from different sources.

## Tasks Completed

### 1. Created Two Tables
- **Table 1:** Customer Summary (Customer ID, Total Spent, Order Count)
- **Table 2:** Customer Region (Customer ID, Region)

### 2. Merged Tables
- Used `pd.merge()` to combine tables on Customer ID.
- Created a unified view: Customer ID, Total Spent, Order Count, Region.

### 3. Checked for Missing Data
- Used `isnull().sum()` to identify any missing values.
- No missing data found in this dataset.

### 4. Aggregated by Region
- Grouped merged data by Region to calculate total sales.
- Verified West as the top region.

## Code Snippets

### Merge
```python
customer_full = pd.merge(customer_summary, customer_region, on="Customer ID", how="left")
