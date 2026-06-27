# Business Insights — Executive Sales Dashboard

Analysis period: **January 2024 – December 2025** (4,200 orders, 4,096 unique customers)
Overall: Sales ₹21.70 Cr | Profit ₹3.33 Cr | Profit Margin 15.35% | Return Rate 4.55%

---

## 1. Sales Trend

**Observation:** Sales are stable with mild seasonal dips rather than a strong growth or decline trend.

**Data evidence:** Monthly sales fluctuate between ~₹63 lakh (Aug 2024, the lowest month) and ~₹1.09 Cr (Aug 2025, one of the highest), with no sustained upward or downward run longer than 2–3 months. Year-over-year, total sales grew from ₹10.62 Cr (2024) to ₹11.08 Cr (2025) — **+4.27%**. However, profit grew only from ₹1.65 Cr to ₹1.68 Cr — **+2.19%** — meaning profit is growing slower than sales.

**Business interpretation:** Revenue is healthy and modestly growing, but the gap between sales growth (+4.27%) and profit growth (+2.19%) signals **margin compression** — the business is selling more but keeping proportionally less of each rupee. This is consistent with rising average discounting or a sales mix shift toward lower-margin categories (see Insight 3).

**Recommended action:** Leadership should set a margin-growth target alongside the revenue target, not just track top-line sales. Follow-up question: *Is the margin decline driven more by discounting behavior or by category mix shift toward Furniture?*

---

## 2. Regional Performance

**Observation:** South region leads on both sales and profit, while East region is the weakest performer on delivery speed and return rate despite reasonable margins.

**Data evidence:** South generates ₹6.47 Cr in sales and ₹1.00 Cr in profit (the highest of all four regions), with a 13.19% margin. East, despite a respectable 13.25% margin, has the **fewest orders (897)**, the **longest average delivery time (4.28 days** vs. 3.4–3.5 days elsewhere), and the **highest return rate (4.91%)**.

**Business interpretation:** East's longer delivery times and elevated returns suggest a **logistics/fulfillment bottleneck** specific to that region — possibly fewer warehouses or carrier coverage — rather than a demand or pricing problem, since margins there are not actually the lowest.

**Recommended action:** Investigate East region's logistics network and carrier mix. Follow-up question: *Would adding a regional distribution point or upgrading East's default ship mode reduce both delivery time and the return rate?*

---

## 3. Category / Sub-Category Profitability

**Observation:** Technology drives almost all profit; Furniture drives meaningful sales but barely breaks even relative to its volume, and two sub-categories are actively dragging margin down.

**Data evidence:** Technology contributes 70.9% of sales (₹15.39 Cr) but 84.2% of profit (₹2.80 Cr) at a **17.6% margin**. Furniture contributes 23.8% of sales (₹5.16 Cr) but only 10.7% of profit (₹0.36 Cr) at a **5.8% margin** — the lowest of the three categories, and well below the company average of 15.35%. Within Furniture, **Bookcases (4.06% margin)** and **Tables (4.82% margin)** are the two weakest sub-categories company-wide, and they also carry the highest average discounts (15–16%) and the highest return rates (8.4% and 6.2% respectively).

**Business interpretation:** Furniture — and Bookcases/Tables specifically — looks like a **volume category propped up by heavy discounting**, which simultaneously erodes margin and appears linked to higher returns (possibly because heavily discounted/clearance items attract more buyer's-remorse or quality-mismatch returns).

**Recommended action:** Run a discount-cap test on Bookcases and Tables (e.g., capping discounts at 15%) and monitor whether margin recovers without a proportional sales drop. Follow-up question: *Are Bookcases/Tables being discounted to clear specific slow-moving SKUs, or is the discount applied broadly across the sub-category?*

---

## 4. Customer Segment Behavior

**Observation:** Home Office is the largest segment by sales but also the lowest-margin and highest-return segment; Corporate is smaller but the most profitable per rupee of sales.

**Data evidence:** Home Office: ₹7.45 Cr sales, 12.83% margin, 5.67% return rate (highest of the three segments). Corporate: ₹7.06 Cr sales, **13.31% margin (highest)**, 4.00% return rate. Consumer: ₹7.19 Cr sales, 13.24% margin, lowest return rate (3.91%) and highest average order value (₹53,053).

**Business interpretation:** Home Office customers are valuable in volume but **less efficient to serve** — lower margin and more returns — while Corporate customers are the most reliably profitable segment despite generating slightly less revenue.

**Recommended action:** Consider segment-specific account management: tighter discount guardrails for Home Office, and account-growth investment in Corporate given its superior margin profile. Follow-up question: *Is Home Office's higher return rate concentrated in specific categories (e.g., Furniture), or spread evenly across the catalog?*

---

## 5. Discount Impact

**Observation:** Profit margin falls in an almost straight line as discount increases, and orders discounted above 31% are, on average, sold at a loss.

**Data evidence:** Average margin by discount band: 0% discount → 18.98% margin; 1–10% → 15.85%; 11–20% → 12.45%; 21–30% → 6.82%; **31%+ → −4.40% margin**, with total profit on that band actually **negative (−₹1.02 lakh)** across 64 orders. The correlation between discount and profit margin is **−0.60**, a strong negative relationship. Of the 288 loss-making orders in the dataset (6.86% of all orders), **250 (87%)** occur at a discount of 21% or higher.

**Business interpretation:** Discounting beyond ~20% is where profitability becomes structurally unsafe, and beyond ~30% it consistently produces losses. This is not a marginal effect — it is the single strongest driver of profit variation in the dataset.

**Recommended action:** Introduce an approval gate for discounts above 20%, and treat 30%+ discounts as exception-only. Follow-up question: *What business reason (clearance, competitive match, bulk deal) justifies the 64 orders discounted above 31%?*

---

## 6. Shipping / Delivery Performance

**Observation:** Same Day shipping has both the fastest delivery and the lowest return rate, while First Class — despite being faster than Standard — paradoxically has the highest return rate.

**Data evidence:** Same Day: 0.40-day average delivery, 2.49% return rate (lowest). Standard Class (58% of all orders): 4.71-day average delivery. First Class: 1.77-day average delivery but a **5.08% return rate — the highest of any shipping mode**, even above slower Standard Class (4.60%). Orders with 7+ day delivery ("Critical" delay bucket) have the **lowest average customer rating (3.89)** of any delivery bucket, even though their return rate (4.43%) isn't the highest.

**Business interpretation:** Delivery speed alone does not predict customer satisfaction — First Class customers, who pay a premium for faster shipping, appear to hold a higher expectation bar, and returns rise when that expectation isn't met by the product itself. Separately, very slow deliveries (7+ days) erode satisfaction (lower ratings) even when they don't always result in a formal return — a leading indicator of dissatisfaction worth watching before it shows up as lost repeat business.

**Recommended action:** Investigate quality/fit issues specifically among First Class orders rather than assuming returns there are a shipping problem. Follow-up question: *Is the First Class return rate concentrated in specific categories, or general across the catalog?*

---

## 7. Return Pattern

**Observation:** Returns are not evenly distributed — they cluster heavily in Furniture, in the Home Office segment, and in the East region.

**Data evidence:** Return rate by category: Furniture 7.67% (highest, more than double the company average), Office Supplies 3.65%, Technology 3.03% (lowest). Return rate by segment: Home Office 5.67% (highest), Corporate 4.00%, Consumer 3.91%. Return rate by region: East 4.91% (highest), South 4.55%, North 4.45%, West 4.34%. Overall, 191 of 4,200 orders (4.55%) were returned.

**Business interpretation:** The pattern points toward **Furniture quality/fit issues sold to Home Office buyers**, compounded by East's logistics challenges (Insight 2), as the primary return drivers — rather than returns being a broad, catalog-wide problem.

**Recommended action:** Prioritize a root-cause review (quality, sizing/fit information, packaging) for Furniture items sold to the Home Office segment, since that intersection likely represents the highest concentration of returns. Follow-up question: *What % of Furniture returns are linked to high-discount orders (21%+ band), reinforcing the Insight 5 finding?*

---

## 8. Business Risk / Opportunity

**Observation:** The dashboard surfaces one clear risk (margin erosion via uncontrolled discounting in Furniture) and one clear opportunity (doubling down on Technology, the highest-margin, fastest-growing-profit category).

**Data evidence — Risk:** Furniture's 5.8% margin, 16.2% average discount, and 7.67% return rate combine into a category that consumes discount budget and logistics/return-handling cost without proportional profit return. **Data evidence — Opportunity:** Technology delivers 84.2% of company profit from 70.9% of sales at a 17.6% margin — the best margin of any category — and its sub-categories (Phones, Accessories, Copiers, Machines) are all clustered tightly around 17–18% margin with comparatively low return rates (~3%), indicating consistent, repeatable profitability rather than a single outlier product.

**Business interpretation:** The business currently earns most of its profit from Technology while Furniture's economics look fragile under its current discount practice. Continued un-managed discounting in Furniture is a margin risk; reallocating marketing/inventory investment toward Technology is a credible growth lever.

**Recommended action:** Leadership should (a) cap or tier discount approval for Furniture, and (b) evaluate increasing inventory depth, marketing spend, or campaign-channel investment behind Technology sub-categories. Follow-up question: *If Furniture's discount were capped at 15% (matching its best-performing sub-categories' current average), what would the modeled margin recovery be?*

