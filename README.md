# Excel_Project-sales-dashboard-project-
Excel dashboard for multi-regional electronics distributor
Data Cleaning & Preparation
Staging Table Setup
• 	Duplicate Removal: Removed exact duplicates based on all columns.
• 	Data Types Fixed: Converted dates to proper date format; ensured numeric fields (e.g., UnitPrice, Quantity) are numbers.
Missing Values:
• 	City: Imputed using “Unknown”.
• 	Salesperson: Filled using “Unknown”.
• 	Channel: Defaulted to “Unknown” if missing.
Suspicious Values:
• 	UnitPrice: Corrected negative prices using median per SKU.
DiscountPct: Capped at 30%; flagged values above for review.
Date Logic:
•	RequiredDate < OrderDate: Imputed RequiredDate as OrderDate + 7 days.
•	LeadTimeDays: Calculated as RequiredDate − OrderDate
Calculated Columns
•	GrossRevenue = UnitPrice × Quantity × (1 − DiscountPct)
•	CostOfGoods = UnitCost × Quantity
•	GrossProfit = GrossRevenue − CostOfGoods
•	MarginPct = IF(GrossRevenue=0, 0, GrossProfit / GrossRevenue)
Standardized Dimensions
•	Month: Extracted as MMM-YYYY from OrderDate
•	Quarter: Derived as Qn-YYYY
•	Region Hierarchy: Region → Country → City
•	PriceBand: Classified SKUs into Low/Medium/High using revenue quantiles

Analysis Tasks
Cohort Analysis
•	Identified first sale month per Country
•	Tracked monthly revenue from cohort start
ABC Analysis
•	Classified SKUs into A (top 80%), B (next 15%), C (last 5%) by GrossRevenue within each ProductCategory
Salesperson Productivity
•	Calculated Revenue/Order, Orders/Month, and GrossProfit/Order
•	Highlighted top and bottom 3 performers
Channel Mix & Cannibalization
•	Compared revenue share by Channel across Regions
•	Identified Online cannibalizing Retail in East and Southern Africa
Service Level Proxy
•	Calculated % of orders with LeadTimeDays ≤ 7 by Country and Category
Price Compliance
•	Flagged orders with DiscountPct > 20%
•	Listed outlier Salespersons and Regions
Scenario Modeling
What-If Control Panel
•	Global Discount Cap: 0%–25%
•	UnitCost Inflation: 0%–15%
•	Quantity Uplift: 0%–20%
Revenue and Profit recalculated dynamically using Excel formulas. Comparison to baseline shown in ControlPanel table.


Interactive Dashboard
Features
•	Slicers: Region, Country, Channel, ProductCategory, Month, Salesperson
•	KPIs: Total Revenue, Gross Profit, Margin %, Avg Order Value, On-Time %
•	Visuals:
o	Revenue by Month (Line Chart)
o	Profit by Region and Channel (Stacked Column)
o	Top 10 SKUs by Revenue (Bar Chart)
•	Dynamic Title: Updates based on slicer selections using TEXTJOIN formula
Dashboard Insights
•	America saw highest revenue growth in April-2024 via Online channel
•	America maintained strong margins on Distributor Channel overtime
•	Online channels outperformed Retail across all regions
•	Top SKUs dominated by Accessories.
•	Gross Profit peaked in July-2023 due to strategic discounts
•	Margins dipped in Feb-2025 due to cost inflation sensitivity

