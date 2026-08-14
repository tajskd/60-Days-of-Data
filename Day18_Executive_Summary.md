# Day 18 – Automating the Executive Summary

## Objective
To build a single function that generates a one-page summary of the entire business, including total sales, top region, and top product.

## The Function
```python
def executive_summary():
    total_sales = df["Sales"].sum()
    total_orders = df["Order ID"].nunique()
    total_customers = df["Customer ID"].nunique()
    region_sales = df.groupby("Region")["Sales"].sum().sort_values(ascending=False)
    top_region = region_sales.index[0]
    top_region_sales = region_sales.iloc[0]
    product_sales = df.groupby("Product Name")["Sales"].sum().sort_values(ascending=False)
    top_product = product_sales.index[0]
    top_product_sales = product_sales.iloc[0]
    
    print("EXECUTIVE SUMMARY")
    print(f"Total Sales: ${total_sales:,.2f}")
    print(f"Total Orders: {total_orders:,}")
    print(f"Total Customers: {total_customers:,}")
    print(f"Top Region: {top_region} (${top_region_sales:,.2f})")
    print(f"Top Product: {top_product} (${top_product_sales:,.2f})")


**Results**
==================================================
         EXECUTIVE SUMMARY – SUPERSTORE
==================================================
Total Sales:          $2,261,536.78
Total Orders:         4,922
Total Customers:      793
--------------------------------------------------
Top Region:           West ($710,219.68)
Top Product:          Canon imageCLASS 2200 Advanced Copier ($61,599.82)
--------------------------------------------------
RECOMMENDATION:
1. Focus marketing efforts on the West region, as it generates the highest revenue.
2. Consider investigating why the South region underperforms.
3. Leverage the success of premium products (like copiers) in B2B campaigns.
==================================================

