# Day 14 – Dashboard Automation (Power Query & Refreshable Excel)

## What I Built
I created a fully automated, refreshable Excel dashboard. This means when new data comes in, I can update all my charts with one click.

## How It Works

### 1. Data Sheet
- Created a dedicated `Data` sheet with raw data.
- Formatted as a Table (`CTRL + T`) so it expands automatically when new rows are added.

### 2. PivotTables Sheet
- Built 4 PivotTables:
  - Sales by Category
  - Sales by Region
  - Top 5 Sub-Categories
  - Monthly Sales Trend

### 3. Dashboard Sheet
- Inserted 4 PivotCharts linked to the PivotTables.
- Charts update automatically when PivotTables refresh.

### 4. Refresh Routine
When I get new data:
1. Paste new data into the `Data` sheet (overwriting old data).
2. Right-click each PivotTable > Refresh.
3. Dashboard charts update instantly.

## Key Takeaway
Automation is the mark of a Senior Analyst. This dashboard saves hours of manual work every time new data arrives.

## File
- `Superstore_Dashboard_FINAL.xlsx` (contains Data, PivotTables, and Dashboard sheets)

## Next Steps
- Apply for Junior Data Analyst roles
- Continue building portfolio projects
