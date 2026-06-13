# Supply Chain Delivery Performance & Profitability Analysis

## Project Overview
Analysed 180,519 global supply chain orders across 5 markets
to identify where late deliveries and profit losses overlap
and quantify the financial impact on the business.

**Tools:** Excel (Power Query) · Power BI · DAX
**Domain:** Supply Chain · Logistics · E-commerce Operations

---

## Business Problem
A global supply chain company had no single view of where
delivery failures and profit losses occurred simultaneously.
The ops team needed a prioritised action list to address
the highest-impact orders first.


---

## Dataset
- 180,519 orders across 5 markets (Europe, LATAM,
  Pacific Asia, USCA, Africa)
- 4 shipping modes (Standard Class, First Class,
  Second Class, Same Day)
- Columns: delivery timing, shipping mode, profit per order,
  customer segment, product category, market, etc.
- Dataset sourced from Kaggle — [https://www.kaggle.com/datasets/saicharankomati/dataco-supply-chain-dataset]
  Raw data not included in repo due to file size (180K+ rows).
  Download from the link above and run Power Query refresh to regenerate.
---

## Data Preparation (Power Query)
Built 7 calculated columns:

| Column | Logic |
|---|---|
| Delivery_Delay_Days | Real days − Scheduled days |
| Delivery_Status_Clean | Late / On Time / Early |
| Profit_Category | Loss / Low / Medium / High Margin |
| Double_Loss_Flag | CRITICAL if late + loss, HIGH RISK if late + low margin |
| Profit_at_Risk | Benefit value for flagged orders only |
| Shipping_Efficiency_Score | 1 − (delay / scheduled days) |
| Order_Risk_Score | Composite 0–2 score across risk dimensions |

**Data quality issues identified and resolved:**
- Order_Item_Profit_Ratio mislabelled — values were absolute
  dollar amounts (-$4,774 to +$911) not ratios. Treated as
  order-level profit in dollar terms.
- Initial Profit_Category thresholds pushed 70% of orders into
  one bucket. Recalibrated around mean profit of $21.97 using
  $0 / $20 / $100 breakpoints for balanced distribution.

---

## Key Findings

### Finding 1 — Delivery failure is a shipping mode problem
- 54.8% of all orders carry late delivery risk
- First Class and Second Class both exceed 50% late rate
- Standard Class handles 60% of all orders at near-zero delay
- All 5 markets show identical ~10-11% critical order rate —
  confirming this is NOT a regional problem

### Finding 2 — 1 in 10 orders is a double loss
- 19,421 orders (10.8%) are CRITICAL — late AND loss-making
- These orders represent -$2.03M in profit at risk
- 18,553 orders score maximum risk on composite score

### Finding 3 — Sports categories drive disproportionate losses
- Tennis & Racquet and Golf Apparel top the loss-making list
- As Seen on TV and Fitness Accessories follow
- Pattern suggests aggressive discounting eliminating margins

### Finding 4 — Europe and LATAM highest risk by volume
- Europe: 5,458 critical orders, -$0.7M profit loss
- LATAM: 5,477 critical orders, -$0.6M profit loss
- Combined = 65% of total profit at risk

---

## Recommendations

1. **Route high-value orders to Standard Class**
   First and Second Class exceed 50% late rate. Standard Class
   operates at near-zero delay with 60% of volume. Switch orders
   with profit above $50 to Standard Class automatically.

2. **Set minimum margin floor for Sports categories**
   Increase price floor by 15-20% or cap discounts at 10%
   for Tennis, Golf, and As Seen on TV categories.
   Projected recovery: $400K–$600K annually.

3. **Weekly critical order review — Europe and LATAM**
   Use Page 2 dashboard filtered to these markets weekly.
   Escalate top 50 risk-score orders to carrier for priority
   handling. Focus on First Class orders in these markets first.

---

## Dashboard
Built a 2-page Power BI dashboard:

**Page 1 — Supply Chain Overview**
- 5 KPI cards: Total Orders, Late Rate %, Critical Orders,
  Profit at Risk, Loss Orders
- Donut chart: delivery status distribution
- Bar chart: late rate by shipping mode with 50% threshold line
- Combo chart: market volume vs critical orders
- Loss categories bar: top 10 loss-making categories

**Page 2 — Risk Action List**
- Dynamic KPI cards: critical order count + profit at risk
- Action table: filtered to CRITICAL + HIGH RISK orders only,
  sorted by risk score descending, with conditional formatting
- Bar chart: profit at risk by market
- Stacked bar: risk score distribution by shipping mode
- Slicers: Market + Shipping Mode for ops team filtering

---

## Skills Demonstrated
- Power Query: data cleaning, type casting, 7 custom columns,
  M language formulas, nested if/else logic
- Excel: IFS formulas, combo charts, conditional formatting
  heatmap, PivotTables with slicers, reference lines
- Power BI: DAX measures, CALCULATE, DIVIDE, visual-level
  filters, conditional formatting, dual-axis combo charts,
  cross-page slicer design
- Analytics: data quality identification and resolution,
  composite risk scoring, business recommendation framing

---

## Project Outcomes
Identified 19,421 critical risk orders representing $2.03M
in profit losses — enabled ops team to prioritise action
using a risk-sorted dashboard filtered by market and
shipping mode.
