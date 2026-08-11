# Day 15 – Top Products Analysis with Pandas

## Objective
To identify the top 5 products by total sales and analyze their performance metrics.

## Approach
1. **Grouped** the data by `Product Name` and summed the `Sales` column.
2. **Sorted** the results in descending order and selected the top 5 products.
3. **Filtered** the original dataset to isolate only those 5 products.
4. **Calculated** key metrics: average order value, total quantity (if available), and average discount (if available).
5. **Interpreted** the results to provide a business insight.

## Code Snippet
```python
# Step 1: Group and sum sales by product
product_sales = df.groupby("Product Name")["Sales"].sum()

# Step 2: Find the top 5 products
top_5_products = (
    df.groupby("Product Name")["Sales"]
    .sum()
    .sort_values(ascending=False)
    .head(5)
)

# Step 3: Filter the data for these products
top_5_df = df[df["Product Name"].isin(top_5_products.index)]

# Step 4: Calculate metrics
avg_order_value = top_5_df["Sales"].mean()


Results
Top 5 Products by Total Sales
Product Name	                                                               Total Sales
Canon imageCLASS 2200 Advanced Copier                                       	$61,599.82
Fellowes PB500 Electric Punch Plastic Comb Binding Machine	                  $27,453.38
Cisco TelePresence System EX90 Videoconferencing Unit	                        $22,638.48
HON 5400 Series Task Chairs for Big and Tall	                                $21,870.58
GBC DocuBind TL300 Electric Binding System                                   	$19,823.48

Key Metrics for Top 5 Products
Average Order Value: $4,382.45
Note: The dataset did not contain 'Quantity' or 'Discount' columns, so these metrics were not calculated.

Business Insight
The top product is the Canon imageCLASS 2200 Advanced Copier, which generated $61,599.82 in sales, far exceeding the other products.
This product has an average order value of $4,382.45, which is significantly higher than the overall average ($230.77), suggesting it is a premium item.
Its success is likely due to being a high-value, high-ticket office equipment piece targeted at corporate clients, meaning that low sales volume still yields massive revenue. It is a 'cash cow' product for the company.

