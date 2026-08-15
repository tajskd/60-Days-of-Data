# Day 21 – Power BI: Building the Executive Dashboard

## Objective
To build the first page of a professional Power BI dashboard, featuring key performance indicators (KPIs) and a top products chart.

## What I Built
I created an Executive Summary page in Power BI that displays:
- **4 KPI Cards:** Total Sales ($2.26M), Total Orders (4,922), Total Customers (793), and Total Regions (4).
- **Top 5 Products Chart:** A bar chart showing the highest-grossing products, led by the Canon imageCLASS 2200 Advanced Copier ($61,599.82).

## Key Learnings
1. **Data Loading:** Successfully imported the `superstore_clean.csv` dataset into Power BI Desktop.
2. **Card Visuals:** Learned to create and format KPI cards, including changing aggregations to "Count (Distinct)" for Order ID and Customer ID.
3. **Bar Charts:** Built a clustered bar chart and applied a Top N filter to show only the top 5 products by sales.
4. **Layout:** Arranged visuals to create a clean, executive-friendly summary page.

## Dashboard Preview
![Executive Summary Dashboard] (Dashboard_Screenshot.png )

## Business Insight
The Canon imageCLASS 2200 Advanced Copier is the clear top performer, generating more than double the sales of the second-ranked product (Fellowes PB500). This confirms our earlier Python analysis and highlights the importance of B2B premium products.

## Next Steps
- Day 22: Add a Regional Performance page (map + bar chart).
- Day 23: Add a Sales Trends page (line chart).
- Day 24: Add slicers for interactivity.
- Day 25: Final polish and publish to Power BI Service.

## File Saved As
`Superstore Executive Dashboard.pbix` (saved to OneDrive)
