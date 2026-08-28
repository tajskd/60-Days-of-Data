# Day 34 – SQL Practice: Query Optimization and Indexing

## Objective
To understand how indexes improve query performance and to practice writing optimized SQL queries.

## Key Concepts
- **Index:** A database structure that speeds up data retrieval on specific columns.
- **Full Table Scan:** When the database must read every row to find matches.
- **B-Tree Structure:** The underlying data structure used by most indexes, enabling fast lookups.
- **Leading Wildcard:** Using `LIKE '%text'` prevents index usage.

## Experiments & Results

### 1. Without Index (Full Table Scan)
- **Query:** `SELECT * FROM sales_sample WHERE customer_id = 257;`
- **Result:** ~1–2 seconds (requires scanning all 100,000 rows).
- **Why:** SQLite must check every row to find matches.

### 2. With Index
- **Index Created:** `CREATE INDEX idx_customer_id ON sales_sample(customer_id);`
- **Query:** `SELECT * FROM sales_sample WHERE customer_id = 257;`
- **Result:** Near instant (0 ms).
- **Why:** The index uses a B-Tree structure to jump directly to the target rows.

### 3. Applying to Superstore Data
- **Index Created:** `CREATE INDEX idx_customer_id_superstore ON superstore_clean(column6);`
- **Query:** `SELECT * FROM superstore_clean WHERE column6 = 'SM-20320';`
- **Result:**
2267	CA-2018-149146	12/10/2018
2574	CA-2018-145128	9/7/2018
2697	CA-2015-145317	18/03/2015
2698	CA-2015-145317	18/03/2015
2699	CA-2015-145317	18/03/2015
2700	CA-2015-145317	18/03/2015
2701	CA-2015-145317	18/03/2015
2702	CA-2015-145317	18/03/2015
2703	CA-2015-145317	18/03/2015
7854	CA-2016-144890	25/12/2016
9188	US-2016-130512	21/08/2016
9189	US-2016-130512	21/08/2016
9190	US-2016-130512	21/08/2016
9191	US-2016-130512	21/08/2016
9192	US-2016-130512	21/08/2016

## Key Insight: Why Indexes Work Well for IDs vs. Long Text

**Short Unique IDs (e.g., Customer ID):**
- Compact and easy to sort.
- The database creates a lightweight, highly efficient B-Tree lookup map that fits easily in memory.
- Results in instant lookups and fast JOIN operations.

**Long Text Columns (e.g., Product Name):**
- Indexing long text strings creates massive index files that consume significant RAM and storage.
- Every `INSERT` or `UPDATE` requires re-sorting and updating large text indexes, heavily degrading performance.
- Text queries frequently use leading wildcards (`LIKE '%Chair%'`), which completely invalidates index usage anyway.

## Key Takeaway
Indexes are powerful tools, but they are not a silver bullet. They should be used selectively on columns that are:
1. Frequently used in `WHERE` clauses.
2. Used for `JOIN` operations.
3. Short and highly selective (few duplicate values).

## Next Steps
- Day 35: Review of SQL Window Functions
