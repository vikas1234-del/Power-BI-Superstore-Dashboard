# Power-BI-Superstore-Dashboard

# powerbi-superstore-dashboard

1. Sample Superstore — Power BI Dashboard
Interactive BI dashboard that analyzes sales, profit, and customer performance using the classic “Sample Superstore” dataset. Built with Power BI Desktop to demonstrate data modeling, DAX, and storytelling with visuals.

<img width="1913" height="1014" alt="Screenshot 2025-08-30 180509" src="https://github.com/user-attachments/assets/06747ec2-2b89-47dc-b9aa-362b4c5d8bdf" />


3. Table of Contents
Overview
Key Insights & KPIs
Dashboard Pages
Data Source
How to Use
Project Structure
Data Model & DAX
Performance Notes
Roadmap
Contributing
License
Contact
Acknowledgements

4. Overview
This repository contains a Power BI report (sample superstore dashboard.pbix) that answers:
Which segments/categories drive the most revenue and profit?
How do sales and profits trend over time and across regions?
Which products and customers contribute to losses or high returns?
What top opportunities exist to improve margins?
Use this as a portfolio piece or a starter template for retail analytics.

5. Key Insights & KPIs
Total Sales, Total Profit, Profit Margin %
YoY Growth for Sales & Profit
Top/Bottom Products by Profit
Regional/State Performance
Order & Ship Performance (lead time)

6. Dashboard Pages
Executive Summary – Core KPIs, YoY deltas, quick highlights
Sales & Profit Trends – Monthly trends, seasonality, drill-through
Category & Product – Category/Sub-Category breakdown, top/bottom items
Customer & Segment – Customer ranking, cohort/segment analysis
Geo Performance – Map by Region/State with tooltips
Shipping & Returns – Ship modes, delivery delays, return hotspots (if available)
Tip: Use slicers for Date, Region, Segment, Category.

7. Data Source
Dataset: Sample Superstore (Orders, Returns, People)
Typical fields: Order Date, Ship Date, Sales, Quantity, Discount, Profit, Customer, Segment, Category, Sub-Category, State, Region, Ship Mode.
If you’re using the default Power BI sample, no extra configuration is needed.
If you’re using a CSV version, place files in data/ and update Power Query paths.

8. How to Use
1 Requirements
Power BI Desktop (latest)

2 Open
Clone this repo and open sample superstore dashboard.pbix in Power BI Desktop.

3 Refresh
If using local CSVs, update file paths in Transform data → Data source settings.

4 Publish (Optional)
Publish to Power BI Service for sharing; configure scheduled refresh if needed.

8. Project Structure
├── sample superstore dashboard.pbix
├── data/                     # (optional) CSVs if you use local data
├── assets/
│   ├── cover.png             # banner image
│   ├── screenshot-1.png
│   └── screenshot-2.png
├── docs/
│   └── model-diagram.png     # star schema image (optional)
└── README.md

9. Data Model & DAX

Model: Star schema with a Date table related to Orders (1:*).
Common Measures (examples):

Total Sales = SUM(Orders[Sales])

Total Profit = SUM(Orders[Profit])

Profit Margin % = DIVIDE([Total Profit], [Total Sales])

Sales YoY % = 
VAR Curr = [Total Sales]
VAR Prev = CALCULATE([Total Sales], DATEADD('Date'[Date], -1, YEAR))
RETURN DIVIDE(Curr - Prev, Prev)

Order to Ship Days =
AVERAGEX(
    Orders,
    DATEDIFF(Orders[Order Date], Orders[Ship Date], DAY)
)


You can replace with your own formulas—these are starter examples.

10. Performance Notes
Use a proper Date table (continuous dates).
Prefer Import mode for fast interactions; limit columns to what you need.
Disable Auto date/time in Options for larger models.
Reduce visuals per page (< 8) and use measure branching for reusable logic.
Aggregate high-cardinality fields when possible.

11. Contact
Vikas Kshirsagar
Email: kshirsagarvikas153@gmail.com
LinkedIn: https://www.linkedin.com/in/vikas-kshirsagar-91a418312


12.Acknowledgements
Dataset inspired by Sample Superstore
Icons/illustrations from Flaticon/Lucide (if used)
Thanks to the Power BI community for patterns and guidance

13. Badges (optional)
![Made with Power BI](https://img.shields.io/badge/Made%20with-Power%20BI-yellow)
![Status](https://img.shields.io/badge/status-active-success)
