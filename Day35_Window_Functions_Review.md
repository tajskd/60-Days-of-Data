# Day 35 – SQL Practice: Review of Window Functions

## Objective
To consolidate knowledge of Window Functions by answering business questions with `RANK()`, running totals, and moving averages.

## Key Concepts
- **`RANK()`:** Assigns a rank to each row within a partition.
- **`PARTITION BY`:** Divides the result set into groups to apply the window function separately.
- **`ORDER BY` (in OVER clause):** Defines the order for the window function.
- **`ROWS BETWEEN`:** Specifies a sliding window for functions like moving averages.

---

## Queries and Results

### 1. Top 10 Customers by Total Sales
**Query:**
```sql
SELECT 
    column7 AS Customer_Name,
    SUM(column18) AS Total_Spent,
    RANK() OVER (ORDER BY SUM(column18) DESC) AS Sales_Rank
FROM superstore_clean
GROUP BY column7
ORDER BY Sales_Rank
LIMIT 10;

**Results:**

Rank  Customer Name	       Total Sales
1	      Sean Miller  	     $24,257.63
2	      Tamara Chand	     $19,031.85
3	      Raymond Buch	     $15,117.34
4	      Tom Ashbrook	     $14,595.62
5	      Ken Lonsdale	     $13,956.72
6	      Sanjit Chand	     $13,706.67
7	      Adrian Barton	     $13,466.95
8	      Hunter Lopez	     $12,799.91
9	      Sanjit Engle	     $11,915.63
10	    Christopher Conant $11,841.10

**2. Top 3 Products in Each Category**
Query:

sql
WITH product_ranking AS (
    SELECT 
        column15 AS Category,
        column17 AS Product_Name,
        SUM(column18) AS Total_Sales,
        RANK() OVER (PARTITION BY column15 ORDER BY SUM(column18) DESC) AS rank_in_category
    FROM superstore_clean
    GROUP BY column15, column17
)
SELECT 
    Category,
    Product_Name,
    Total_Sales,
    rank_in_category
FROM product_ranking
WHERE rank_in_category <= 3
ORDER BY Category, rank_in_category;


**Results:**

Category	              Product Name	                                        Total Sales	 Rank
Furniture   	     HON 5400 Series Task Chairs for Big and Tall	               $21,870.58	  1
Furniture	         Bretford Rectangular Conference Table Tops	                 $12,995.29	  2
Furniture	         Global Troy Executive Leather Low-Back Tilter    	         $12,975.38	  3
Office Supplies	   Avery 4027 File Folder Labels for Dot Matrix Printers       $55,000.00	  1
Office Supplies	   Fellowes PB500 Electric Punch Plastic Comb Binding Machine  $27,453.38	  2
Office Supplies	   GBC DocuBind TL300 Electric Binding System	                 $19,823.48	  3
Technology	       Canon imageCLASS 2200 Advanced Copier	                     $61,599.82	  1
Technology	       Cisco TelePresence System EX90 Videoconferencing Unit	     $22,638.48	  2
Technology	       Hewlett Packard LaserJet 3310 Copier	                       $18,839.69  	3

**3. Running Total and 7-Day Moving Average**
Query:

sql
WITH daily_sales AS (
    SELECT 
        column3 AS Order_Date,
        SUM(column18) AS Daily_Total
    FROM superstore_clean
    GROUP BY column3
)
SELECT 
    Order_Date,
    Daily_Total,
    SUM(Daily_Total) OVER (ORDER BY Order_Date) AS Running_Total,
    AVG(Daily_Total) OVER (ORDER BY Order_Date ROWS BETWEEN 6 PRECEDING AND CURRENT ROW) AS Seven_Day_MA
FROM daily_sales
ORDER BY Order_Date
LIMIT 20;


**Results (First 20 Rows):**

Order Date	Daily Total	   Running Total	    7-Day Moving Average
1/1/2018	   $1,286.76	       $1,286.76	            $1,286.76
1/10/2015	       $4.71	       $1,291.47	              $645.74
1/10/2016  	 $1,018.99	       $2,310.46	              $770.15
1/10/2017	     $586.57	       $2,897.03	              $724.26
1/10/2018	   $2,552.81	       $5,449.84	            $1,089.97
1/11/2015	   $4,087.06	       $9,536.90	            $1,589.48
1/11/2016	   $3,103.94	      $12,640.83	            $1,805.83
1/11/2017	     $319.90	      $12,960.74	            $1,667.71
1/11/2018	   $2,921.43	      $15,882.17	            $2,084.38
1/12/2015	   $5,370.61	      $21,252.78	            $2,706.05
1/12/2016	   $6,876.53	      $28,129.31	            $3,604.61
1/12/2017	   $5,823.72	      $33,953.03	            $4,071.88
1/12/2018	   $4,304.65	      $38,257.68	            $4,102.97
1/2/2015	     $468.90	      $38,726.58	            $3,726.53
1/2/2017	     $161.97	      $38,888.55	            $3,703.97
1/3/2015	   $2,203.15	      $41,091.70	            $3,601.36
1/3/2016	     $355.46	      $41,447.15	            $2,884.91
1/3/2017	   $6,285.81	      $47,732.96	            $2,800.52
1/4/2015	     $102.80	      $47,835.76	            $1,983.25
1/4/2017	     $843.99	      $48,679.75	            $1,488.87

**Business Insight**

"The 7-day moving average shows a gradual increase in sales over the first 20 days of the data, indicating a positive trend for the business."

**Key Takeaway**

Window Functions are essential for time-series analysis, ranking, and complex aggregations. They allow for efficient, readable SQL without the need for self-joins or subqueries.


**Next Steps**

Day 36: Python Practice – Data Cleaning with Pandas

