# Day 31 – Advanced SQL Practice: CTEs and Window Functions

## Objective
To practice writing SQL queries using Common Table Expressions (CTEs) and Window Functions.

## Key Concepts
- **CTE (Common Table Expression):** A temporary named result set that you can reference within a SELECT, INSERT, UPDATE, or DELETE statement.
- **Window Function:** A function that performs a calculation across a set of rows related to the current row, without collapsing them into a single output row.

## SQL Query

```sql
WITH customer_sales AS (
    SELECT 
        column7 AS Customer_Name,
        SUM(column18) AS Total_Spent
    FROM superstore_clean
    GROUP BY column7
)
SELECT 
    Customer_Name,
    Total_Spent,
    RANK() OVER (ORDER BY Total_Spent DESC) AS Sales_Rank
FROM customer_sales
ORDER BY Sales_Rank
LIMIT 10;


Results
Rank	       Customer Name	    Total Sales
1	             Sean Miller	      $24,257.63
2	             Tamara Chand	      $19,031.85
3	             Raymond Buch	      $15,117.34
4	             Tom Ashbrook	      $14,595.62
5	             Ken Lonsdale	      $13,956.72
6	             Sanjit Chand	      $13,706.67
7              Adrian Barton	    $13,466.95
8	             Hunter Lopez	      $12,799.91
9	             Sanjit Engle    	  $11,915.63
10	           Christopher Conant $11,841.10

Key Takeaway
CTEs make complex queries easier to read and debug. Window Functions like RANK() allow for advanced analytics without needing to write complicated subqueries.

Business Insight: Sean Miller is the company's top customer by a significant margin, representing a key account for the business development team.
