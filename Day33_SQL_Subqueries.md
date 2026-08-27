# Day 33 – SQL Practice: Subqueries and Correlated Subqueries

## Objective
To practice writing SQL queries using simple subqueries, correlated subqueries, and CTEs to answer complex business questions.

## Key Concepts (From Research & Practice)

### 1. Simple Subquery (Independent Helper)
- A query nested inside another query that can run independently.
- **How it works:** SQL runs the inner subquery once, calculates a static value (like an average), and hands the single answer to the outer query to filter results.
- **Example:** Finding all customers who spent more than the average total spend.

### 2. Correlated Subquery (Looping Helper)
- A subquery that depends on values from the outer query.
- **How it works:** SQL executes the subquery repeatedly—once for every single row evaluated by the outer query—using the current row's category/group to compute a dynamic calculation.
- **Example:** Finding products with sales above their specific category's average.

### 3. CTE (Common Table Expression – The Temporary Building Block)
- Creates a temporary named result table at the top of the query using the `WITH` keyword.
- **How it works:** SQL creates the temporary table upfront, loads the aggregated or ranked data into it, and then allows you to query off that table in the final `SELECT` statement.
- **Example:** Breaking down a complex ranking query into clear, readable steps.

---

## Queries and Results

### 1. Customers Who Spent Above the Overall Average
**Query:**
```sql
SELECT 
    column7 AS Customer_Name,
    SUM(column18) AS Total_Spent
FROM superstore_clean
GROUP BY column7
HAVING SUM(column18) > (
    SELECT AVG(Total_Spent)
    FROM (
        SELECT SUM(column18) AS Total_Spent
        FROM superstore_clean
        GROUP BY column7
    )
)
ORDER BY Total_Spent DESC;

**Result (Top 10):
**
Sean Miller: $24,257.63

Tamara Chand: $19,031.85

Raymond Buch: $15,117.39

Tom Ashbrook: $14,595.62

Ken Lonsdale: $13,956.72

Sanjit Chand: $13,706.67

Adrian Barton: $13,466.95

Hunter Lopez: $12,799.91

Sanjit Engle: $11,915.63

Christopher Conant: $11,841.10

**2. Products with Above-Average Sales in Their Category**
Query:
SELECT 
    column17 AS Product_Name,
    column15 AS Category,
    column18 AS Sales
FROM superstore_clean s1
WHERE column18 > (
    SELECT AVG(column18)
    FROM superstore_clean s2
    WHERE s2.column15 = s1.column15
)
ORDER BY Category, Sales DESC;

**Result (First 10 Rows):
**
Product Name	                                                      Category	Sales
Chromcraft Bull-Nose Wood 48" x 96" Rectangular Conference Tables 	Furniture	$991.76
Tensor Track Tree Floor Lamp                                     	  Furniture	$99.95
Bevis 36 x 72 Conference Tables                                   	Furniture	$99.59
Safco Drafting Table	                                              Furniture	$99.37
HON 5400 Series Task Chairs for Big and Tall	                      Furniture	$981.37
Dana Halogen Swing-Arm Architect Lamp	                              Furniture	$98.33
Global Ergonomic Managers Chair                                   	Furniture	$977.29
Bretford CR4500 Series Slim Rectangular Table                     	Furniture	$974.99
Electrix Halogen Magnifier Lamp                                   	Furniture	$971.50
Novimex Fabric Task Chair                                          	Furniture	$97.57

**3. Top 3 Products in Each Category (Using CTE)**
Query:
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

**Results:
**
Category	           Product Name	                                            Total Sales	Rank
Furniture	           HON 5400 Series Task Chairs for Big and Tall	              $21,870.58	1
Furniture	           Bretford Rectangular Conference Table Tops   	            $12,995.29	2
Furniture            Global Troy Executive Leather Low-Back Tilter	            $12,975.38	3
Office Supplies      Avery 4027 File Folder Labels for Dot Matrix Printers      $55,000.00	1
Office Supplies	     Fellowes PB500 Electric Punch Plastic Comb Binding Machine	$27,453.38	2
Office Supplies	     GBC DocuBind TL300 Electric Binding System                	$19,823.48	3
Technology	         Canon imageCLASS 2200 Advanced Copier	                    $61,599.82	1
Technology	         Cisco TelePresence System EX90 Videoconferencing Unit	    $22,638.48	2
Technology	         Hewlett Packard LaserJet 3310 Copier                     	$18,839.69	3

**Key Takeaways**
Simple Subqueries are best for single, static comparisons.

Correlated Subqueries are powerful for row-by-row dynamic analysis.

CTEs are essential for complex queries, especially when using Window Functions like RANK().

**Next Steps**
Day 34: SQL Practice – Query Optimization and Indexing
