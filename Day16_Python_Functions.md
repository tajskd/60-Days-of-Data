# Day 16 – Building a Reusable Function for Regional Analysis

## Objective
To create a reusable Python function that generates a summary report for any given region.

## The Function
```python
def region_summary(region_name):
    """Generates a summary report for a given region."""
    region_df = df[df["Region"] == region_name]
    total_sales = region_df["Sales"].sum()
    avg_order = region_df["Sales"].mean()
    top_products = region_df.groupby("Product Name")["Sales"].sum().sort_values(ascending=False).head(3)
    num_customers = region_df["Customer ID"].nunique()
    
    print(f"=== REGION REPORT: {region_name} ===")
    print(f"Total Sales: ${total_sales:,.2f}")
    print(f"Average Order Value: ${avg_order:,.2f}")
    print(f"Number of Customers: {num_customers}")
    print("\nTop 3 Products:")
    for product, sales in top_products.items():
        print(f"  - {product}: ${sales:,.2f}")



**Why This Matters**
Efficiency: I can now generate a detailed report for any region with one line of code.
Consistency: Every report follows the exact same format.
Scalability: If I want to analyze a new region, I don't need to rewrite anything—I just call the function.

**Key Insight**
I discovered that:
The West region has the highest total sales.
The South region has the highest average order value, suggesting customers there are more likely to buy premium items.
The West also has the most customers, making it the largest market.

