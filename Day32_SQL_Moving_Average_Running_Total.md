# Day 32 – SQL Practice: Moving Averages and Running Totals

## Objective
To practice writing SQL queries that calculate a 7-day moving average and a running total of sales.

## Key Concepts
- **Running Total:** The cumulative sum of a metric over time.
- **Moving Average:** The average of a metric over a specific number of previous periods (e.g., 7 days). It smooths out short-term fluctuations and highlights longer-term trends.

## SQL Query
```sql
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


**Results (First 20 Rows)**
Order Date	       Daily Total	          Running Total	      7-Day Moving Average
1/1/2018           	$1,286.76	             $1,286.76	         $1,286.76
1/10/2015	              $4.71	             $1,291.47	           $645.74
1/10/2016         	$1,018.99	             $2,310.46	           $770.15
1/10/2017	            $586.57	             $2,897.03	           $724.26
1/10/2018	          $2,552.81	             $5,449.84	         $1,089.97
1/11/2015	          $4,087.06	             $9,536.90	         $1,589.48
1/11/2016	          $3,103.94	            $12,640.83	         $1,805.83
1/11/2017	            $319.90            	$12,960.74	         $1,667.71
1/11/2018          	$2,921.43           	$15,882.17	         $2,084.38
1/12/2015         	$5,370.61	            $21,252.78           $2,706.05
1/12/2016	          $6,876.53	            $28,129.31	         $3,604.61
1/12/2017	          $5,823.72	            $33,953.03	         $4,071.88
1/12/2018          	$4,304.65	            $38,257.68	         $4,102.97
1/2/2015	            $468.90	            $38,726.58	         $3,726.53
1/2/2017	            $161.97	            $38,888.55	         $3,703.97
1/3/2015	          $2,203.15	            $41,091.70	         $3,601.36
1/3/2016	            $355.46           	$41,447.15	         $2,884.91
1/3/2017	          $6,285.81	            $47,732.96	         $2,800.52
1/4/2015            	$102.80	            $47,835.76	         $1,983.25
1/4/2017	            $843.99	            $48,679.75	         $1,488.87

**Analysis**
1. Running Total on the First Day
Answer: $1,286.76 (On Day 1, the running total equals the exact daily total because there are no previous days to add yet).

2. Comparison: Moving Average vs. Daily Totals
Answer: It is significantly smoother than the daily totals. While daily sales jump wildly (e.g., swinging from $4.71 on 1/10/2015 to $5,370.61 on 1/12/2015), the 7-day moving average levels out these extremes and shows a steady progression without sharp spikes.

3. Overall Sales Trend
Answer: It reveals that overall sales momentum grew significantly across this initial period, rising steadily from around $1,286 up to over $4,100 before leveling off slightly.

**Business Insight**
"While daily revenue fluctuates wildly from day to day, the 7-day moving average smooths out these extreme spikes to show a strong upward momentum in sales over the first two weeks."

Key Takeaway
Moving averages are essential for identifying trends in noisy data. They help business leaders understand whether performance is genuinely improving or if short-term fluctuations are misleading.

Next Steps
Day 33: SQL Practice – Subqueries and Correlated Subqueries

