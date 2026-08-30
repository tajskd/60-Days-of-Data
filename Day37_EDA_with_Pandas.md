# Day 37 – Python Practice: Exploratory Data Analysis (EDA) with Pandas

## Objective
To perform a full exploratory data analysis on the cleaned Superstore dataset using Pandas and Matplotlib.

## Steps Completed
1. Loaded and inspected the cleaned data (`superstore_cleaned_manual.csv`).
2. Generated summary statistics for numeric columns.
3. Explored categorical columns (Order ID, Region, Category, etc.).
4. Visualized the distribution of Sales (histogram and boxplot).
5. Analyzed Sales by Category (bar chart) and Region (pie chart).
6. Identified the top 5 products by total sales.
7. Synthesized findings into a 3-sentence business summary.

---

## Key Findings

### 1. Summary Statistics (Numeric)
| Metric | Row ID | Sales |
| :--- | :--- | :--- |
| Mean | 4,900.50 | $230.96 |
| Std Dev | 2,829.16 | $626.59 |
| Min | 1.00 | $0.44 |
| 25th Percentile | 2,450.75 | $17.31 |
| Median | 4,900.50 | $54.90 |
| 75th Percentile | 7,350.25 | $211.96 |
| Max | 9,800.00 | $22,638.48 |

**Key Takeaway:** The median sales ($54.90) is significantly lower than the mean ($230.96), indicating a right-skewed distribution driven by a few large orders.

---

### 2. Categorical Insights
- **Top Categories:** Office Supplies (5,909 orders), Furniture (2,078), Technology (1,813).
- **Top Regions:** West (3,140 orders), East (2,785), Central (2,277), South (1,598).
- **Top City:** New York City (891 orders).
- **Top State:** California (1,946 orders).

---

### 3. Visual Insights
- **Sales Distribution:** The histogram shows that the majority of sales are under $500, with a long tail of high-value orders.
- **Sales by Category:** Technology is the top revenue category.
- **Sales by Region:** West leads with 31.6%, followed by East (29.5%), Central (21.8%), and South (17.1%).

---

### 4. Top 5 Products by Sales
| Rank | Product Name | Total Sales |
| :--- | :--- | :--- |
| 1 | Canon imageCLASS 2200 Advanced Copier | $61,599.82 |
| 2 | Fellowes PB500 Electric Punch Plastic Comb Binding Machine | $27,453.38 |
| 3 | Cisco TelePresence System EX90 Videoconferencing Unit | $22,638.48 |
| 4 | HON 5400 Series Task Chairs for Big and Tall | $21,870.58 |
| 5 | GBC DocuBind TL300 Electric Binding System | $19,823.48 |

---

## Business Summary
1. The total sales across all categories is **$2,263,398.50**, with **Technology** being the top-performing category at **$836,154.03** (followed by Furniture at $741,999.80 and Office Supplies at $685,244.67).
2. The **West region** generates the highest sales, accounting for **31.6%** of total sales (followed by East at 29.5%, Central at 21.8%, and South at 17.1%).
3. The top product is the **Canon imageCLASS 2200 Advanced Copier**, generating **$61,599.82** in sales, which is **2.24 times higher** than the second-ranked product (Fellowes PB500 Electric Punch at $27,453.38).

---

## Code Snippets

### Summary Statistics
```python
df.describe()

**Sales by Category (Bar Chart)**

python
category_sales = df.groupby("Category")["Sales"].sum().sort_values(ascending=False)
category_sales.plot(kind='bar')

**Top 5 Products**

python
df.groupby("Product Name")["Sales"].sum().sort_values(ascending=False).head(5)

**Key Takeaway**

EDA is the foundation of any data analysis project. It helps you understand the structure of your data, identify outliers, and uncover initial insights that drive further analysis.

**Next Steps**

Day 38: Python Practice – Advanced Pandas: Merging and Joining
