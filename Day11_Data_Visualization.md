# Day 11 – Data Visualization in Python (Matplotlib & Seaborn)

## Overview
Today I transitioned from analyzing data in Python to visualizing it. I created four professional charts to replicate my Excel dashboard, uncovering key business insights.

## Environment
- **Tool:** Jupyter Notebook (via Anaconda)
- **Libraries:** Pandas, Matplotlib, Seaborn
- **Dataset:** Superstore (9,800 rows, 18 columns)

---

## Charts Created & Insights

### 1. Sales by Category (Bar Chart)
- **Visualization:** Vertical bar chart showing total sales for each category.
- **Insight:** Technology leads with $827k, followed by Furniture ($728k) and Office Supplies ($705k).
- **Action:** Double down on Technology marketing.

### 2. Sales by Region (Pie Chart)
- **Visualization:** Pie chart showing sales distribution across four regions.
- **Insight:** West dominates (31.4%), East follows (29.6%), Central (21.8%), South lags (17.2%).
- **Action:** Investigate South region underperformance.

### 3. Top 5 Sub-Categories (Horizontal Bar Chart)
- **Visualization:** Horizontal bar chart showing top 5 sub-categories by sales.
- **Insight:** Phones ($327k) and Chairs ($322k) are the top performers.
- **Action:** Prioritize inventory for Phones and Chairs.

### 4. Monthly Sales Trend (Line Chart)
- **Visualization:** Line chart showing sales over time.
- **Insight:** Sales peak in Q4 (October–December), with a major spike in November.
- **Action:** Prepare for holiday spikes with additional stock and marketing.

---

## Key Technical Takeaways

1. **`dayfirst=True`** is essential for non-US date formats.
2. **Always re-run imports** after restarting the kernel.
3. **Seaborn** is a powerful tool for creating professional charts with minimal code.
4. **Matplotlib** provides the flexibility to customize every aspect of a chart.

---

## Code Snippets

### Sales by Category (Bar Chart)
```python
category_sales = df.groupby("Category")["Sales"].sum().sort_values(ascending=False)
plt.figure(figsize=(8,5))
sns.barplot(x=category_sales.index, y=category_sales.values, palette="viridis")
plt.title("Total Sales by Category", fontsize=16)
plt.show()
