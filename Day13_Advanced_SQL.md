# Day 13 – Advanced SQL: CTEs, Window Functions, and the Column Mapping Lesson

## Overview
Today was a breakthrough day. I successfully wrote advanced SQL queries using Common Table Expressions (CTEs) and Window Functions, but not without a major debugging lesson about column names.

---

## The Big Lesson: Column Names Are Everything

### The Problem
When I first tried to run my queries, I kept getting blank results and metadata errors. SQLite couldn't find columns like `Customer Name` or `Order ID`.

### The Cause
When I imported the CSV into SQLite, I didn't check the box that says **"First row contains column names"**. SQLite gave my columns generic names: `column1`, `column2`, ... `column18`.

### The Fix
I ran `PRAGMA table_info(superstore_clean);` to see the actual column names, then mapped them:

| Column # | Actual Name |
|----------|-------------|
| column1 | Row ID |
| column2 | Order ID |
| column3 | Order Date |
| column4 | Ship Date |
| column5 | Ship Mode |
| column6 | Customer ID |
| column7 | Customer Name |
| column8 | Segment |
| column9 | Country |
| column10 | City |
| column11 | State |
| column12 | Postal Code |
| column13 | Region |
| column14 | Product ID |
| column15 | Category |
| column16 | Sub-Category |
| column17 | Product Name |
| column18 | Sales |

---## Queries Written & Verified

### 1. CTE – Customer Summary (Top 10 Customers by Total Spend)

WITH customer_summary AS (
    SELECT 
        column6 AS Customer_ID,
        SUM(column18) AS Total_Spent,
        COUNT(column2) AS Order_Count
    FROM superstore_clean
    GROUP BY column6
)
SELECT * FROM customer_summary 
WHERE Total_Spent > 5000
ORDER BY Total_Spent DESC
LIMIT 10;

Results:
Customer ID	Total Spent	Order Count
SM-20320	  $24,257.63	15
TC-20980	  $19,031.85	12
RB-19360	  $15,117.34	18
TA-21385	  $14,595.62	10
KL-16645	  $13,956.72	29
SC-20095	  $13,706.67	22
AB-10105	  $13,466.95	20
HL-15040	  $12,799.91	11
SE-20110	  $11,915.63	19
CC-12370	  $11,841.10	11

### 2. Top 10 Customers by Spending (Using Column References)

SELECT 
    column7 AS Customer_Name,
    SUM(column18) AS Total_Spent
FROM superstore_clean
GROUP BY column7
ORDER BY Total_Spent DESC
LIMIT 10;

Results:
Customer Name	     Total Spent
Sean Miller	       $24,257.63
Tamara Chand	     $19,031.85
Raymond Buch	     $15,117.34
Tom Ashbrook	     $14,595.62
Ken Lonsdale	     $13,956.72
Sanjit Chand	     $13,706.67
Adrian Barton	     $13,466.95
Hunter Lopez	     $12,799.91
Sanjit Engle	     $11,915.63
Christopher Conant $11,841.10

### 3. Regional Customer Analysis (CTE + JOIN)

WITH customer_region AS (
    SELECT 
        column6 AS Customer_ID,
        column13 AS Region
    FROM superstore_clean
    GROUP BY column6, column13
),
customer_spend AS (
    SELECT 
        column6 AS Customer_ID,
        SUM(column18) AS Total_Spent
    FROM superstore_clean
    GROUP BY column6
)
SELECT 
    cr.Region,
    COUNT(DISTINCT cr.Customer_ID) AS Customer_Count,
    AVG(cs.Total_Spent) AS Avg_Customer_Spend
FROM customer_region cr
JOIN customer_spend cs ON cr.Customer_ID = cs.Customer_ID
GROUP BY cr.Region
ORDER BY Avg_Customer_Spend DESC;

Results:
Region	   Customer Count 	Avg Customer Spend
South	         509	           $2,772.15
Central      	 626	           $2,718.37
West	         681	           $2,686.23
East	         669	           $2,663.28

###4. Window Function – Ranking Customers by Spending

SELECT 
    column7 AS Customer_Name,
    SUM(column18) AS Total_Spent,
    RANK() OVER (ORDER BY SUM(column18) DESC) AS Spend_Rank
FROM superstore_clean
GROUP BY column7
LIMIT 10;

Results:
Rank	Customer Name	    Total Spent
1	    Sean Miller	       $24,257.63
2	    Tamara Chand	     $19,031.85
3   	Raymond Buch	     $15,117.34
4	    Tom Ashbrook	     $14,595.62
5	    Ken Lonsdale	     $13,956.72
6   	Sanjit Chand	     $13,706.67
7	    Adrian Barton	     $13,466.95
8	    Hunter Lopez	     $12,799.91
9	    Sanjit Engle	     $11,915.63
10	  Christopher Conant $11,841.10

###5. Running Total of Sales Over Time

SELECT 
    column3 AS Order_Date,
    SUM(column18) AS Daily_Sales,
    SUM(SUM(column18)) OVER (ORDER BY column3) AS Running_Total
FROM superstore_clean
GROUP BY column3
ORDER BY column3
LIMIT 20;

Key Business Insights
1. High-Value Customers
Sean Miller is the #1 customer with $24,257.63 in total spend.

The top 10 customers account for over $150,000 in sales.

2. Regional Customer Value
South has the highest average customer spend ($2,772.15) despite having the fewest customers (509).

West has the most customers (681) but slightly lower average spend ($2,686.23).

East has the lowest average spend ($2,663.28) – needs attention.

3. Recommendations
Focus marketing efforts on the South region – customers there spend more per capita.

Protect the West region – it's your largest customer base.

Investigate why the East region has the lowest average spend – consider upselling or retention strategies.
