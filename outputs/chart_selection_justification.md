# Chart Selection Justification


---

## 1. Sales Trend View — Line Chart

- **Question answered:** How are sales and profit changing over time, month by month?
- **Why this chart type:** A line chart is the standard, most readable way to show a continuous measure (Sales) across a continuous time dimension (Order Date by Month). Trend, direction, and inflection points are immediately visible in a way a bar chart cannot match for 24 consecutive months.
- **Encoding:** X-axis = Order Date (month); Y-axis = SUM(Sales); a second line (or dual-axis) = SUM(Profit) to show the sales-vs-profit gap; color distinguishes the two measures.
- **Design principle applied:** Consistent color usage — Sales and Profit use the same two colors throughout the entire dashboard, so the eye doesn't have to re-learn the legend on every sheet.
- **Mistake avoided:** Did not truncate the Y-axis at a non-zero baseline, which would visually exaggerate small month-to-month fluctuations and mislead leadership into thinking volatility is larger than it is.

## 2. Regional Performance View — Filled Map 

- **Question answered:** Which regions/states are driving sales and profit, and where is performance lagging?
- **Why this chart type:** A filled map gives an intuitive geographic read for a geographic field (State).
- **Encoding:** Map: State (geographic role) for location, SUM(Profit) for color (diverging color scale, since profit can be relatively low or high but not negative at state level here).
- **Design principle applied:** Useful filters — Region and State filters let leadership drill from a national view into a single region without rebuilding the chart.
- **Mistake avoided:** Did not use map color to encode Sales and size to encode Profit simultaneously (a common "double-encoding" mistake) — only one measure is color-coded at a time, keeping the read unambiguous.

## 3. Category Profitability View — Bar Chart (with Profit Margin label)

- **Question answered:** Which categories and sub-categories drive profit, and which ones underperform relative to their sales volume?
- **Why this chart type:** A horizontal bar chart sorted by Profit is the clearest way to compare a moderate number of discrete categories (3 categories, 13 sub-categories) — better than a pie chart, which cannot show 13 slices legibly or support accurate ranking comparison.
- **Encoding:** Rows = Category > Sub-Category (hierarchy); Length = SUM(Profit); Color = Profit Margin (calculated field) on a diverging scale so low-margin sub-categories (Bookcases, Tables) visually stand out in a different color from high-margin ones; Label = Profit Margin %.
- **Design principle applied:** Appropriate sorting — bars are sorted descending by Profit, not alphabetically, so the worst performers are immediately visible at the bottom without the viewer having to scan the whole list.
- **Mistake avoided:** Avoided a pie or donut chart for category share, since pie charts make it hard to compare more than 3–4 slices accurately — a bar chart with a clear length encoding was used instead.

## 4. Customer Segment View — Highlight Table 

- **Question answered:** How do Consumer, Corporate, and Home Office segments compare on sales, margin, average order value, and return rate?
- **Why this chart type:** A highlight table (color-coded grid) is well suited to comparing a small number of categories (3 segments) across several measures at once side-by-side, which a single bar chart cannot do without becoming cluttered.
- **Encoding:** Rows = Customer Segment; Columns = Sales, Profit Margin, Average Order Value, Return Rate; Color = value intensity per column (sequential scale per measure).
- **Design principle applied:** Clear hierarchy and minimal clutter — only the four measures that matter for segment comparison are shown, not every field in the dataset.
- **Mistake avoided:** Did not use a single combined "score" or index that blends sales, margin, and returns into one number — that would obscure the trade-off (e.g., Home Office is high-volume but high-return) that leadership specifically needs to see.

## 5. Shipping Performance View — Bar Chart (Delivery Days) 

- **Question answered:** Which shipping modes are slow ?
- **Why this chart type:** Bar charts are the right choice for comparing a small set of discrete categories (4 ship modes) on a single measure each — simpler and more precise than a combo chart for this specific comparison.
- **Encoding:** Rows = Ship Mode; Length = AVG(Delivery Days) in one bar chart and Return Rate (calculated field) in a companion chart; Color = Ship Mode, kept consistent with other sheets.
- **Design principle applied:** Readable titles and labels — each bar is directly labeled with its value (e.g., "4.71 days") so the viewer doesn't have to estimate from the axis.
- **Mistake avoided:** Did not assume "faster shipping = fewer returns" and hide the First Class result — the chart preserves the counter-intuitive data point rather than smoothing it away.

## 6. Discount vs. Profit View — Scatter Plot

- **Question answered:** How does discount level relate to profit margin, and at what point does discounting become unprofitable?
- **Why this chart type:** A scatter plot is the correct chart for showing the relationship between two continuous measures (Discount and Profit Margin) at the order level — a bar chart would require pre-bucketing and lose the underlying relationship/correlation visible in a scatter.
- **Encoding:** X-axis = Discount; Y-axis = Profit Margin (calculated field); Color = Category (so Furniture's cluster of high-discount, negative-margin points is visible against other categories); a reference line at Profit Margin = 0 marks the break-even point.
- **Design principle applied:** Avoidance of misleading scales — both axes start at a true zero/minimum so the negative-margin region is shown honestly rather than clipped off.
- **Mistake avoided:** Did not use a trend line without showing the underlying scatter points — trend lines alone can hide that the loss-making points cluster specifically in one category, which is the actionable insight here.

## 7. Return Analysis View — Bar Chart (Return Rate by Category/Segment/Region)

- **Question answered:** Where are returns concentrated — by category, customer segment, or region?
- **Why this chart type:** A bar chart ranked by Return Rate (calculated field) across each dimension is the clearest way to show which slice of the business has a disproportionate return problem, since the comparison is simple magnitude-by-category.
- **Encoding:** Rows = Category (or Segment/Region, selectable via a parameter/filter); Length = Return Rate; Color = same Return Rate value on a sequential scale, reinforcing the bar length rather than introducing a second encoding.
- **Design principle applied:** Focus on business interpretation — the chart includes a reference line at the company-wide average return rate (4.55%) so viewers can immediately see which categories sit above or below the norm, rather than just reading raw numbers.
- **Mistake avoided:** Did not show total *count* of returns (which would just mirror sales volume) instead of *return rate* — rate, not count, is what reveals Furniture as disproportionately problematic despite not having the most orders.

## 8. KPI Cards (Total Sales, Total Profit, Overall Profit Margin, Overall Return Rate)

- **Question answered:** What is the headline performance at a glance, before drilling into any single chart?
- **Why this chart type:** Single-value "BAN" (Big Ass Number) cards are the standard executive-dashboard pattern for headline KPIs — leadership should not have to read a chart to know the topline numbers.
- **Encoding:** Each card = one aggregated measure (SUM(Sales), SUM(Profit), Profit Margin, Return Rate); no color encoding beyond a simple conditional color (e.g., green/red) if the KPI is above/below a target threshold.
- **Design principle applied:** Clear labels and readable titles — each KPI card states the metric name, the value, and (where applicable) the comparison period, so it is self-explanatory without needing the rest of the dashboard for context.
- **Mistake avoided:** Did not show more than 4 KPI cards on the main view — beyond that, KPI cards stop being "headline" numbers and start adding clutter that competes with the supporting charts below them.

