# Executive Sales Dashboard — Part 4 (Tableau)

## 1. Business Problem Summary

The leadership team of a retail business needs a single executive dashboard to monitor sales performance, profitability, customer segment behavior, category performance, shipping performance, discount impact, and return patterns — and to surface concrete business opportunities and risks rather than a disconnected set of charts.

## 2. Dataset Description

- **File:** `data/dashboard_sales_data.xlsx`, sheet `dashboard_sales_data` (4,200 orders, 4,096 unique customers, 20 columns), plus a `data_dictionary` sheet describing every field.
- **Time period:** 1 Jan 2024 – 31 Dec 2025 (24 months).
- **Key fields:** order/ship dates, customer segment (Consumer / Corporate / Home Office), region/state/city, category & sub-category, ship mode, sales, quantity, discount, profit, return flag, delivery days, customer rating, campaign channel.
- **Data quality notes:** `customer_rating` has 32 missing values and `campaign_channel` has 24 missing values out of 4,200 rows; these were left as nulls (not imputed) and excluded only from averages of those specific fields, not from the rest of the analysis.
- **Assumption:** Currency unit is not explicitly stated in the data dictionary. All monetary fields are treated as a single consistent currency (assumed INR given the scale of values, e.g. average order value ≈ ₹51,800) — this does not affect any ratio-based metric (margin %, return rate %) or relative comparison in the dashboard.

## 3. Tableau Workbook Description

`tableau/executive_dashboard.twbx` is a packaged Tableau workbook built directly on `dashboard_sales_data.xlsx`. It contains:
- One data source (the `dashboard_sales_data` sheet)
- 7 supporting worksheets (one per required view — see Section 5)
- 1 executive dashboard combining KPI cards, the 7 views, filters, and one filter action
- A Story (optional) connecting the views for a leadership walkthrough

> See `TABLEAU_BUILD_GUIDE.md` in the repo root for the exact, step-by-step build instructions, calculated field formulas, and shelf configuration used to construct this workbook.

## 4. Calculated Fields Created

| Field | Formula | Purpose |
|---|---|---|
| **Profit Margin** | `SUM([Profit]) / SUM([Sales])` | Profitability % per any slice of the data |
| **Cost** | `[Sales] - [Profit]` | Underlying cost implied by sales and profit |
| **Average Order Value** | `SUM([Sales]) / COUNTD([Order ID])` | Average revenue per order (orders used as the denominator since `order_id` is the transaction grain) |
| **Return Rate** | `SUM([Return Flag]) / COUNTD([Order ID])` | % of orders returned, for any category/segment/region slice |
| **Shipping Delay Bucket** | `IF [Delivery Days] <= 2 THEN "0-2 days (Fast)" ELSEIF [Delivery Days] <= 4 THEN "3-4 days (Standard)" ELSEIF [Delivery Days] <= 6 THEN "5-6 days (Slow)" ELSE "7+ days (Critical)" END` | Groups delivery speed into business-readable bands |
| *(Additional)* **Discount Band** | `IF [Discount] = 0 THEN "0%" ELSEIF [Discount] <= 0.1 THEN "1-10%" ELSEIF [Discount] <= 0.2 THEN "11-20%" ELSEIF [Discount] <= 0.3 THEN "21-30%" ELSE "31%+" END` | Powers the discount-vs-profit analysis |
| *(Additional)* **Loss-Making Order Flag** | `IF [Profit] < 0 THEN "Loss" ELSE "Profit" END` | Isolates the 288 orders (6.86%) that lose money |

Full explanation and business rationale for each field is also in `outputs/business_insights.md` and `TABLEAU_BUILD_GUIDE.md`.

## 5. Dashboard Components

| View | Chart type | Business question |
|---|---|---|
| Sales Trend View | Line chart (Sales & Profit by Month) | How are sales/profit trending over time? |
| Regional Performance View | Filled map + bar chart | Which regions/states drive sales and profit? |
| Category Profitability View | Sorted horizontal bar chart (Category > Sub-Category) | Which categories/sub-categories drive or drag profit? |
| Customer Segment View | Highlight table | How do Consumer/Corporate/Home Office compare? |
| Shipping Performance View | Bar charts (Delivery Days, Return Rate by Ship Mode) | Which ship modes are slow, and does that affect returns? |
| Discount vs. Profit View | Scatter plot (Discount × Profit Margin, colored by Category) | How does discounting affect profitability? |
| Return Analysis View | Bar chart (Return Rate by Category/Segment/Region) | Where are returns concentrated? |
| KPI Cards | Single-value cards | Total Sales, Total Profit, Overall Profit Margin, Overall Return Rate |

## 6. Filters and Interactions Used

- **Region** filter (applies to all views)
- **Category** filter (applies to all views)
- **Customer Segment** filter (applies to all views)
- **Date Range** filter on Order Date
- **Filter action:** Clicking a bar in the Category Profitability view filters the Return Analysis view and the Discount vs. Profit view to that category, so leadership can drill from "this category looks weak" straight into "is it a discount problem or a return problem."

## 7. Key Business Insights

- Sales grew 4.27% YoY but profit grew only 2.19% — margin is compressing.
- Technology drives 84.2% of profit from 70.9% of sales at a 17.6% margin — the clear profit engine.
- Furniture sits at a 5.8% margin (vs. 15.35% company average), driven by Bookcases and Tables, which also have the highest discounts and return rates.
- Discounts above 21% account for 87% of all loss-making orders; above 31% the average order is sold at a loss.
- East region has the slowest delivery (4.28 days) and the highest return rate (4.91%) — a logistics issue, not a demand issue.
- Home Office is the highest-revenue segment but also the highest-return segment (5.67%); Corporate has the best margin (13.31%).

## 8. Dashboard Story Summary

 In short: the business is healthy and growing on the surface, but margin is being quietly compressed by uncontrolled discounting concentrated in Furniture (especially Bookcases and Tables), and a fulfillment gap in the East region is driving both slower delivery and more returns there. Technology is the clear opportunity to lean into further, given its consistent above-average margin across all sub-categories.

## 9. Assumptions and Limitations

- Currency unit assumed consistent throughout (see Section 2); does not affect any percentage-based metric.
- "Profit" reflects order-level gross economics only — it does not include return-handling cost, marketing spend by channel, or inventory holding cost, so true category/segment P&L may differ from what is shown.
- Return reason is not captured in the data (only a binary return flag), so root causes behind Furniture's high return rate are inferred from correlated patterns (discount level, sub-category), not directly observed.
- The dataset spans two calendar years only, which limits confidence in long-term seasonality conclusions.
- `customer_rating` (32 nulls) and `campaign_channel` (24 nulls) have minor missing data, excluded from averages of those fields only.

## 10. Screenshots Included

| File | Shows |
|---|---|
| `screenshots/full_dashboard.png` | Complete executive dashboard (all views, KPIs, filters) |
| `screenshots/sales_trend_view.png` | Sales trend line chart |
| `screenshots/regional_performance_view.png` | Regional/state-level map and bar chart |
| `screenshots/category_profitability_view.png` | Category/sub-category profitability bar chart |
| `screenshots/filter_interaction_view.png` | Dashboard with a filter/action applied, showing the interaction in effect |


