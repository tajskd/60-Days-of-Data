# Day 8 – Advanced SQL (Subqueries, Window Functions, Customer Analysis)

## What I Learned

### 1. Creating a Summary Table
- Used `CREATE TABLE customer_summary AS` to build a customer-level summary.
- Aggregated Total Spent, Order Count, and Average Order Value.

### 2. Subqueries
- Used a subquery to find customers who spent above average.
- Query: `WHERE Total_Spent > (SELECT AVG(Total_Spent) FROM customer_summary)`
- Found 282 high-value customers.

### 3. Window Functions
- Used `RANK() OVER (ORDER BY Total_Spent DESC)` to rank customers.
- Top 5 customers:
  1. Sean Miller – $24,257.63
  2. Tamara Chand – $19,031.85
  3. Raymond Buch – $15,117.34
  4. Tom Ashbrook – $14,595.62
  5. Ken Lonsdale – $13,956.72

## Key Insights
- Sean Miller is the #1 customer by a wide margin.
- 282 customers are above average – a strong base.
- Window functions make ranking and running totals easy.

## Next Steps
- Day 9 – Advanced Excel (Power Query, VLOOKUP, Dashboards)
- Day 10 – Python Basics (finally!)
