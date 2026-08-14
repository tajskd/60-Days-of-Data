# Day 19 – Deep Dive Analysis: Why Does the South Underperform?

## Objective
To investigate the root causes of the South region's underperformance and compare its profile against the top-performing West region.

## The Deep Dive Function
I built a reusable function called `deep_dive_region()` that generates a diagnostic report for any region, including:
- Basic metrics (total sales, average order value, order volume).
- Customer segment breakdown.
- Top 5 products.
- Monthly sales trend.

## Deep Dive Results: The South Region

| Metric | Value |
| :--- | :--- |
| **Total Sales** | $389,151.46 |
| **Average Order Value (AOV)** | $243.52 |
| **Total Orders** | 810 |
| **Total Customers** | 509 |

### Customer Segment Breakdown
- **Consumer:** $194,702.21 (50% of sales)
- **Corporate:** $120,546.87 (31% of sales)
- **Home Office:** $73,902.37 (19% of sales)

### Top 5 Products in the South
1. Cisco TelePresence System EX90 Videoconferencing Unit ($22,638.48)
2. HP Designjet T520 Inkjet Large Format Printer ($11,374.94)
3. GBC DocuBind TL300 Electric Binding System ($8,342.01)
4. Cubify CubeX 3D Printer Triple Head Print ($7,999.98)
5. Fellowes PB500 Electric Punch Plastic Comb Binding Machine ($7,625.94)

### Monthly Sales Trend (First 5 months of 2015)
- January: $9,296.84
- February: $2,028.99 (Dip)
- **March: $32,911.12 (Massive Spike)**
- April: $12,069.25
- May: $5,779.24

---

## Comparative Analysis: South vs. West

| Metric| South | West | Difference |
| :--- | :--- | :--- | :--- |
| Total Sales | $389,151.46 | $710,219.68 | **West is 82% higher** |
| Total Orders| 810 | 1,587 | **West has 96% more orders** |
| Average Order Value | $243.52 | $226.18 | **South has a 7.7% higher AOV** |
| Total Customers | 509 | 681 | **West has 34% more customers** |

## The Big Insight (The "So What?")

The South does **not** have a "low-value" problem. In fact, its average order value is higher than the West's ($243.52 vs. $226.18). 

**The real problem is volume.** The South has 34% fewer customers and 96% fewer orders than the West. This means:
- The South is not attracting enough buyers.
- The South is not converting enough browsers into buyers.

This is likely a combination of:
1.  **Marketing:** Insufficient brand awareness or targeted campaigns in the South.
2.  **Sales Coverage:** A lack of sales reps or local presence.
3.  **Product Availability:** Certain products may not be marketed or stocked as heavily.

## Recommendations for Leadership

1.  **Investigate Sales Coverage:** Do we have a dedicated sales team in the South? If not, this is the most urgent gap to fill.
2.  **Launch a Targeted Campaign:** Since the South has a higher AOV, a marketing campaign focused on high-ticket B2B products (like the Cisco TelePresence system) could be highly effective.
3.  **Analyze Competitor Presence:** Are competitors more established in the South? A competitive analysis could reveal why we are losing market share.
4.  **Analyze the March Spike:** March 2015 showed a massive sales spike ($32,911). Investigate what marketing campaign or sales event drove this, and replicate it.

## Next Steps
- **Day 20:** Combine all functions into a single, final "Analytics Toolkit" dashboard.
