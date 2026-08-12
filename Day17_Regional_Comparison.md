# Day 17 – Automating Multi-Region Comparison

## Objective
To build a reusable function that compares key metrics across all regions in a single table.

## The Function
```python
def compare_regions():
    """Creates a comparison table of key metrics for all regions."""
    results = []
    for region in df["Region"].unique():
        region_df = df[df["Region"] == region]
        total_sales = region_df["Sales"].sum()
        avg_order = region_df["Sales"].mean()
        num_customers = region_df["Customer ID"].nunique()
        top_product = region_df.groupby("Product Name")["Sales"].sum().sort_values(ascending=False).head(1)
        top_product_name = top_product.index[0] if not top_product.empty else "N/A"
        results.append({"Region": region, "Total Sales": total_sales, "Avg Order Value": avg_order, "Customers": num_customers, "Top Product": top_product_name})
    
    comparison_df = pd.DataFrame(results).sort_values("Total Sales", ascending=False)
    print(comparison_df.to_string(index=False))
    return comparison_df

Results
Region	Total Sales	Avg Order Value	Customers	Top Product
West	$710,219.68	$226.18	681	Canon imageCLASS
East	$669,518.73	$240.40	669	Canon imageCLASS
Central	$492,646.91	$216.36	626	Canon imageCLASS
South	$389,151.46	$243.52	509	Cisco TelePresence

Key Insight
The West has the highest total sales and the most customers.
The South has the lowest total sales but the second-highest average order value, meaning its customers buy premium items but there are fewer of them.
The East has the highest average order value ($240.40).
