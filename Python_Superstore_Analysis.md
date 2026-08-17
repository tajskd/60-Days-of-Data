# Superstore Sales Analysis – Python Portfolio Project

## Project Overview
This project analyzes sales data from a Superstore to uncover key business insights, identify top-performing products and regions, and provide data-driven recommendations.

**Tools Used:** Python (Pandas, NumPy, Matplotlib, Seaborn), Jupyter Notebook

**Dataset:** 9,800 rows, 18 columns (Sales, Profit, Category, Region, etc.)

---

## Key Findings

### 1. Sales Performance
- **Total Sales:** $2,261,536.78
- **Total Orders:** 4,922
- **Total Customers:** 793

### 2. Top Product
The **Canon imageCLASS 2200 Advanced Copier** is the highest-grossing product, generating **$61,599.82** in sales—more than double the second-ranked product.

### 3. Regional Performance
| Region | Total Sales | Avg Order Value | Customers | Top Product |
| :--- | :--- | :--- | :--- | :--- |
| West | $710,219.68 | $226.18 | 681 | Canon imageCLASS |
| East | $669,518.73 | $240.40 | 669 | Canon imageCLASS |
| Central | $492,646.91 | $216.36 | 626 | Canon imageCLASS |
| South | $389,151.46 | $243.52 | 509 | Cisco TelePresence |

**Key Insight:** The **South** has the lowest total sales, but the **highest average order value**. This suggests the South does not have a "low-value" problem—it has a **customer acquisition** problem.

### 4. Customer Segmentation
**Multi-Region Customers:**
- **765 customers** (10% of total) shop in more than one region.
- These customers have a **66.8% higher average order value** ($231.93 vs $139.03).

**Recommendation:** Create a VIP segment for multi-region customers and offer cross-regional incentives.

### 5. Monthly Sales Trend
Sales peak significantly in **Q4 (November and December)**, with a sharp dip in January.

**Recommendation:** Increase inventory and marketing spend in Q4 to capitalize on the seasonal surge.

---

## Visualizations
- **Sales by Category** (Bar Chart): Technology is the highest-grossing category.
- **Sales by Region** (Pie Chart): West dominates with 31.4%.
- **Top 5 Sub-Categories** (Horizontal Bar Chart): Phones and Chairs are the top performers.
- **Monthly Sales Trend** (Line Chart): Clear Q4 spike.

---

## Recommendations
1. **Focus on B2B Premium Products:** The Canon copier proves that high-ticket items drive revenue—prioritize marketing to corporate clients.
2. **Target the South Region:** Launch a marketing campaign to increase customer acquisition, as the South has high-value buyers.
3. **Q4 Preparation:** Plan inventory and staffing around the November–December peak.
4. **VIP Program:** Develop a loyalty program for multi-region customers to encourage repeat business.

---

## Code Snippets

### Regional Comparison Function
```python
def compare_regions():
    results = []
    for region in df["Region"].unique():
        region_df = df[df["Region"] == region]
        results.append({
            "Region": region,
            "Total Sales": region_df["Sales"].sum(),
            "Avg Order Value": region_df["Sales"].mean(),
            "Customers": region_df["Customer ID"].nunique()
        })
    return pd.DataFrame(results).sort_values("Total Sales", ascending=False)




**Customer Segmentation Analysis
**
mmulti_region_customers = customer_full.groupby("Customer ID").filter(lambda x: x["Region"].nunique() > 1)
multi_region_avg = multi_region_customers["Sales"].mean()
single_region_avg = df[~df["Customer ID"].isin(multi_region_customers["Customer ID"])]["Sales"].mean()
print(f"Multi-region avg order: ${multi_region_avg:.2f}")
print(f"Single-region avg order: ${single_region_avg:.2f}")
