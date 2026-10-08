# PR. 2 Analyzer

An Excel workbook (`PR. 2 Analyzer.xlsx`) that completes the 10 tasks listed in the **Project Instructions** sheet, using a 200-row sales dataset (Apr 2024 – Apr 2025). All analysis is built with live formulas, so it recalculates if the Dataset changes. Currency is shown in Indian rupees (₹).

## Dataset

Columns: `Customer_ID`, `Customer_Name`, `Region`, `Product_Category`, `Sales`, `Quantity`, `Discount`, `Order_Date`, `Profit`, plus a `Timestamp` column added for Task 6.

- 200 orders, 30 customers (CUST001–CUST030)
- Regions: Central, East, North, South, West
- Categories: Books, Clothing, Electronics, Furniture, Office Supplies

## Sheets and tasks

| Sheet | Task | What it contains |
|---|---|---|
| Project Instructions | – | Original brief |
| Dataset | 6 | Source data; column J `Timestamp` uses `=NOW()` |
| Top 10 Customers | 1 | Total purchase per customer (`SUMIF`), rank, and conditional formatting that highlights the top 10 in green |
| What-If Analysis | 2 | Discount input cell (blue/yellow) showing the effect on total profit, plus a 0–25% sensitivity table |
| Regression | 3 | Profit (Y) vs Sales (X) in Analysis ToolPak layout: regression statistics, ANOVA, coefficients, p-values, 95% limits |
| Descriptive Stats | 4 | ToolPak-style descriptive statistics for Sales, Quantity, Discount and Profit |
| Sales Growth | 5 | Monthly sales and month-on-month growth with ▲ (green) / ▼ (red) arrows via custom number format |
| High-Value Customers | 7 | Customers ranked with `LARGE` + `INDEX` + `MATCH`, High-Value/Standard segment, filter arrows on the header row |
| Pivot Table | 8 | Total sales by region × product category (`SUMIFS` cross-tab) |
| Dashboard | 9, 10 | KPI tiles, formula-driven insights, and bar (sales by region), line (monthly sales) and pie (category share) charts |

## Key results

- Total sales ₹195,218, total profit ₹68,287 (35.0% margin), average discount 9.7%
- Top region: West; top category: Books
- Regression: Profit ≈ −1.03 + 0.351 × Sales, R² = 0.60
- 15 of 30 customers are high-value; the top 10 account for about 47% of sales

## How to use

- **What-If:** change the blue/yellow cell (`B8`) on *What-If Analysis* to test a different discount rate.
- **High-value filter:** use the filter arrows on row 5 of *High-Value Customers* (e.g. Segment = High-Value).
- **Timestamp:** `NOW()` updates every time the workbook recalculates.

## Assumptions and notes

- **What-If model:** Sales are treated as net of each order's discount, so list price = Sales ÷ (1 − Discount). A new discount rate re-prices every order from list price while costs and quantities stay fixed, so the whole change in revenue flows into profit.
- **High-value definition:** a customer whose total purchase is at or above the average customer total (₹6,507).
- **Formula-built analysis:** the pivot table, regression and descriptive statistics are formulas, not a native PivotTable or ToolPak output. The numbers match what those tools produce.
- **Mode:** shows "N/A" where no value repeats (as in the ToolPak).
- **April 2025** contains only 7 days of data, so its −82% growth reflects a partial month, not a real drop.
- **Number format:** amounts use standard grouping (₹195,218), not lakh grouping.
