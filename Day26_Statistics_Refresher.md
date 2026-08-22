# Day 26 – Statistics Refresher: Descriptive Stats

## Objective
To review and apply foundational statistics concepts to the Superstore dataset, and to interpret what the numbers mean for the business.

## Key Concepts
- **Mean:** The arithmetic average (sensitive to outliers).
- **Median:** The middle value when data is ordered (robust to outliers).
- **Mode:** The most frequent value.
- **Standard Deviation:** A measure of how spread out the data is.
- **Correlation vs. Causation:** A crucial reminder that correlation does not imply causation.

## Python Code & Results

```python
# Calculate descriptive statistics for Sales
mean_sales = df["Sales"].mean()
median_sales = df["Sales"].median()
mode_sales = df["Sales"].mode()[0]  # The [0] gets the first mode if there are multiple
std_sales = df["Sales"].std()

print(f"Mean Sales: ${mean_sales:.2f}")
print(f"Median Sales: ${median_sales:.2f}")
print(f"Mode Sales: ${mode_sales:.2f}")
print(f"Standard Deviation: ${std_sales:.2f}")


Results:

Mean Sales: $230.77

Median Sales: $54.49

Mode Sales: $12.96

Standard Deviation: $626.65

Business Insight
Why Mean > Median
The mean ($230.77) is significantly higher than the median ($54.49) because a small number of high-value transactions (outliers), such as bulk corporate or premium technology orders, pull the overall average upward. This is a classic indicator of a right-skewed distribution.

What This Tells Us About the Data
The vast majority of orders consist of low-to-moderate dollar amounts (under $55), while high-value purchases occur much less frequently. The mode of $12.96 confirms that the most common transaction is a small, low-ticket item.

Why This Matters to the Business
Relying solely on the mean overstates typical customer spending. Business decisions regarding inventory, pricing, and marketing strategies should use the median to reflect everyday purchasing behavior, while managing premium orders as a separate, high-value segment.

Key Takeaway
Understanding the difference between mean and median is critical for accurate decision-making. It prevents the business from overestimating typical customer behavior and allows for better targeting of both everyday consumers and premium corporate clients
