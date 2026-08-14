# Day 20 – The Complete Analytics Toolkit

## Objective
To build a single, unified function that runs the entire analytics pipeline and exports the results to a shareable text file.

## What I Built
I created a complete analytics toolkit that generates a full business report with a single command. The toolkit includes:

- `executive_summary()` – high-level business overview
- `compare_regions()` – side-by-side regional performance
- `deep_dive_region()` – detailed diagnostic for any region
- `full_analysis()` – runs all functions and exports to a `.txt` file

## The Full Pipeline Code
```python
def full_analysis():
    import sys
    from io import StringIO
    
    buffer = StringIO()
    sys.stdout = buffer
    
    print("="*50)
    print("     SUPERSTORE ANALYTICS REPORT")
    print("="*50)
    print("\n[1] EXECUTIVE SUMMARY\n")
    executive_summary()
    
    print("\n[2] REGIONAL COMPARISON\n")
    compare_regions()
    
    print("\n[3] DEEP DIVE REPORTS\n")
    for region in df["Region"].unique():
        print(f"\n--- DEEP DIVE: {region.upper()} ---")
        deep_dive_region(region)
    
    print("\n" + "="*50)
    print("END OF REPORT")
    
    sys.stdout = sys.__stdout__
    
    with open("superstore_full_report.txt", "w", encoding="utf-8") as f:
        f.write(buffer.getvalue())
    
    print("Report saved as 'superstore_full_report.txt'")




**Report Output (Sample)**
==================================================
     SUPERSTORE ANALYTICS REPORT
==================================================

[1] EXECUTIVE SUMMARY

==================================================
         EXECUTIVE SUMMARY – SUPERSTORE
==================================================
Total Sales:          $2,261,536.78
Total Orders:         4,922
Total Customers:      793
--------------------------------------------------
Top Region:           West ($710,219.68)
Top Product:          Canon imageCLASS 2200 Advanced Copier ($61,599.82)
--------------------------------------------------
RECOMMENDATION:
1. Focus marketing efforts on the West region.
2. Investigate why the South region underperforms.
3. Leverage premium products in B2B campaigns.
==================================================

[2] REGIONAL COMPARISON

=== REGIONAL COMPARISON SUMMARY ===
 Region  Total Sales  Avg Order Value  Customers                                           Top Product
   West  710219.6845       226.184613        681                 Canon imageCLASS 2200 Advanced Copier
   East  669518.7260       240.401697        669                 Canon imageCLASS 2200 Advanced Copier
Central  492646.9132       216.357889        626                 Canon imageCLASS 2200 Advanced Copier
  South  389151.4590       243.524067        509 Cisco TelePresence System EX90 Videoconferencing Unit

[3] DEEP DIVE REPORTS

--- DEEP DIVE: SOUTH ---
==================================================
     DEEP DIVE REPORT: SOUTH REGION
==================================================
Total Sales:          $389,151.46
Average Order Value:  $243.52
Total Orders:         810
Total Customers:      509
--------------------------------------------------
CUSTOMER SEGMENT BREAKDOWN:
  - Consumer: $194,702.21
  - Corporate: $120,546.87
  - Home Office: $73,902.37
--------------------------------------------------
TOP 5 PRODUCTS:
  1. Cisco TelePresence System EX90 Videoconferencing Unit: $22,638.48
  2. HP Designjet T520 Inkjet Large Format Printer - 24" Color: $11,374.94
  3. GBC DocuBind TL300 Electric Binding System: $8,342.01
  4. Cubify CubeX 3D Printer Triple Head Print: $7,999.98
  5. Fellowes PB500 Electric Punch Plastic Comb Binding Machine: $7,625.94
==================================================


**Why This Matters**

This pipeline turns raw data into a professional business report in seconds. It demonstrates my ability to:

Write reusable Python functions

Automate repetitive analysis

Generate shareable outputs for stakeholders


**Files Generated**
superstore_full_report.txt – Full business report


