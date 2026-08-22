# Day 27 – Correlation Analysis: What Drives Sales?

## Objective
To identify which numeric factors have the strongest relationship with Sales using correlation analysis, and to interpret the business implications.

## Key Concept
**Correlation (r):** A measure of the linear relationship between two variables.
- **+1:** Perfect positive relationship (they move together).
- **0:** No relationship.
- **-1:** Perfect negative relationship (they move in opposite directions).

## Python Code & Results

```python
numeric_df = df.select_dtypes(include=['float64', 'int64'])
correlation_matrix = numeric_df.corr()
sales_correlation = correlation_matrix['Sales'].sort_values(ascending=False)
print(sales_correlation)


Correlation with Sales:

Sales: 1.00

Row ID: 0.00 (no meaningful relationship)


Business Insight
1. Strongest Correlation
The variable most strongly correlated with Sales is Quantity with a correlation of 0.20.

This suggests that higher purchase quantities drive overall sales revenue, so strategies aimed at encouraging bulk orders could boost performance.

2. The Volume vs. Profit Trap
The correlation between Sales and Profit is 0.48, which is only a weak to moderate positive relationship.

This indicates that generating high sales volume does not guarantee profitability. High gross revenue does not equal high earnings if the underlying product costs, shipping, or discounts are too steep.

3. The Discount Warning
Discounts typically show a negative correlation with Profit because as discounts increase, profit margins drop. This suggests that some "top sellers" might be unprofitable if they are heavily discounted.

Key Takeaway
Correlation does not equal causation, but it points us toward areas worth investigating. The analysis reveals that:

Volume is not a silver bullet: Bulk orders drive revenue, but may not drive profit.

Profitability requires cost control: High-priced products (like office furniture) may generate large revenue numbers while running at a net loss.

Discounts need scrutiny: Aggressive discounting may boost sales volume while eroding profit margins.

Recommendations for the Business
Monitor Profit per Product: Identify top-selling products that are actually unprofitable.

Optimize Discounting Strategy: Test whether smaller discounts can still drive volume without destroying margins.

Focus on Profitable Growth: Prioritize products and regions where revenue and profit are both strong.
