# Day 36 – Python Practice: Data Cleaning with Pandas

## Objective
To practice identifying and fixing common data quality issues using Pandas.

## Tasks Completed
1. **Created a messy version** of the Superstore dataset (`superstore_messy.csv`) with:
   - 20 null values in `Sales`.
   - 10 null values in `Customer Name`.
   - 5 duplicate rows.
   - Abbreviated state names (`CA`, `NY`, `TX`).
   - Lowercase category names (`furniture`, `office supplies`, `technology`).

2. **Loaded and explored** the messy data:
   - Identified 20 missing values in `Sales`, 10 in `Customer Name`, and 11 in `Postal Code`.
   - Confirmed 5 duplicate rows.

3. **Cleaned the messy data**:
   - Removed all duplicate rows (`drop_duplicates()`).
   - Filled missing `Sales` with the column mean.
   - Filled missing `Customer Name` with `"Unknown"`.
   - Standardized `Category` to title case (`str.title()`).
   - Mapped state abbreviations back to full names using a dictionary.

4. **Verified the cleaning**:
   - **Missing Values:** 0 (all handled).
   - **Duplicates:** 0.
   - **Unique States:** 49 unique states (full names).
   - **Unique Categories:** `Furniture`, `Office Supplies`, `Technology`.

5. **Saved** the cleaned dataset as `superstore_cleaned_manual.csv`.

## Code Snippets

### Handling Missing Values
```python
messy_df["Sales"] = messy_df["Sales"].fillna(messy_df["Sales"].mean())
messy_df["Customer Name"] = messy_df["Customer Name"].fillna("Unknown")


**Fixing Inconsistent Formatting**

messy_df["Category"] = messy_df["Category"].str.title()
state_mapping = {"CA": "California", "NY": "New York", "TX": "Texas"}
messy_df["State"] = messy_df["State"].replace(state_mapping)


**Key Learnings**

Missing Values: Always check for nulls and decide on a strategy (fill, drop, or flag).

Duplicates: Use drop_duplicates() to remove exact duplicate rows.

Formatting: Standardize text using .str.lower(), .str.upper(), or .str.title().

Mapping: Use dictionaries to replace inconsistent values (e.g., state abbreviations).


**Verification Output**

=== After Cleaning ===
Missing Values: 0
Duplicates: 0
Unique States: [49 unique state names]
Unique Categories: ['Furniture', 'Office Supplies', 'Technology']

**Next Steps**
Day 37: Python Practice – Exploratory Data Analysis (EDA) with Pandas
