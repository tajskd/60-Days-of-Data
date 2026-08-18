# Day 22 – Power BI: Regional Performance Page

## Objective
To build a dedicated page in Power BI that visualizes regional sales performance using a map and supporting charts.

## What I Built
I created a Regional Performance page that displays:
- **Map Visual:** Shows sales by state with bubble size and color saturation.
- **Bar Chart:** Total Sales by Region (West leads with $710k).
- **Column Chart:** Average Order Value by Region (South leads with $243).

## Dashboard Preview
![Regional Performance Page] (<img width="908" height="528" alt="regional_screenshot" src="https://github.com/user-attachments/assets/60dfe906-5cca-4998-a578-c2ccaf26538f" />
)

## Key Learnings
1. **Map Visual:** Used State as the location field, with Sales for size and color saturation.
2. **Multiple Visuals:** Combined map, bar chart, and column chart to tell a complete regional story.
3. **Data Aggregation:** Changed the Sales aggregation from Sum to Average for the column chart.

## Business Insight
- The **West** dominates total sales ($710k), but the **South** has the highest average order value ($243), confirming the South is a "low volume, high value" region.
- This indicates the South needs marketing to increase customer count, not to increase order value.

## Regional Performance Summary
| Region | Total Sales | Avg Order Value | Customers |
| :--- | :--- | :--- | :--- |
| West | $710,219.68 | $226.18 | 681 |
| East | $669,518.73 | $240.40 | 669 |
| Central | $492,646.91 | $216.36 | 626 |
| South | $389,151.46 | $243.52 | 509 |

## Key Takeaway
The South has the highest average order value but the lowest total sales and customer count. This suggests the South is a "low volume, high value" region—the solution is customer acquisition, not increasing order value.

## Next Steps
- Day 23: Add a Sales Trends page (line chart).
- Day 24: Add slicers for interactivity.
- Day 25: Final polish and publish to Power BI Service.
