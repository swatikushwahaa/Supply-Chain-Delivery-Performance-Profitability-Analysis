## Supply Chain Delivery Performance & Profitability Analysis

## Project Overview

Analysed 180,519 global supply chain orders across 5 markets to identify where delivery failures and profit losses overlap and quantify the financial impact on business operations.

**Tools:** Excel (Power Query), Power BI, DAX

**Domain:** Supply Chain, Logistics, E-Commerce Operations

---

## Business Problem

The company had no single view showing where operational inefficiencies and profitability issues occurred together.

While delivery delays were being monitored separately and financial performance was tracked independently, there was no way to identify:

* Which shipping methods were driving delivery failures
* Which markets generated the highest operational risk
* Which product categories consistently lost money
* Which specific orders required immediate action
* Which orders should operations teams prioritise first?


## Key Business Questions Answered

### 1. Which shipping modes are responsible for the highest delivery delays?

#### Analysis

Compared late delivery percentages across all shipping modes.

#### Insight

* More than 54% of all orders experienced late delivery.
* First Class and Second Class both exceeded 50% late delivery rate.
* Standard Class processed approximately 60% of all orders while maintaining near-zero average delay.

#### Recommendation

Route high-margin and high-value orders through Standard Class whenever operationally feasible and review carrier performance associated with First Class and Second Class shipping.

---

### 2. How many orders are simultaneously late and unprofitable?

#### Analysis

Created a Double Loss Flag to identify orders that were both delayed and loss-making.

#### Insight

* 19,421 orders were classified as CRITICAL.
* These represented 10.8% of all orders.
* Total profit at risk exceeded $2.03 million.
* 18,553 orders reached the highest composite risk score.

#### Recommendation

Establish a weekly operational review process focused on critical orders and implement early escalation procedures before shipment.

### 3. Which markets contribute the most operational and financial risk?

#### Analysis

Measured critical order counts and profit-at-risk values by market.

#### Insight

| Market | Critical Orders |
| ------ | --------------- |
| Europe | 5,458           |
| LATAM  | 5,477           |

Europe and LATAM together accounted for approximately 65% of total profit at risk.

#### Recommendation

Prioritise operational improvement initiatives in Europe and LATAM and investigate regional carrier and fulfilment performance.

### 4. Which product categories generate the largest losses?

#### Analysis

Evaluated profitability across all product categories.

#### Insight

Top loss-generating categories included:

* Tennis & Racquet
* Golf Apparel
* As Seen on TV
* Fitness Accessories

These categories consistently produced negative profit outcomes despite sales volume.

#### Recommendation

Introduce category-level margin controls, reduce aggressive discounting, and establish minimum profitability thresholds.

Estimated recovery opportunity: $400K–$600K annually.

### 5. Which orders should operations teams prioritise first?

#### Analysis

Developed a composite Order Risk Score using delivery delay, profitability, and critical risk indicators.

#### Insight

The dashboard identified and ranked the highest-risk orders requiring immediate intervention.

This transformed thousands of operational records into a prioritised action list for decision-makers.

#### Recommendation

Review the top 50 highest-risk orders weekly and allocate resources based on risk score rather than order volume.

---
### Key Findings summary

#### Finding 1 : Delivery failure is a shipping mode problem
- 54.8% of all orders carry late delivery risk
- First Class and Second Class both exceed 50% late rate
- Standard Class handles 60% of all orders at near-zero delay
- All 5 markets show identical ~10-11% critical order rate —
  confirming this is NOT a regional problem

#### Finding 2 : 1 in 10 orders is a double loss
- 19,421 orders (10.8%) are CRITICA - late AND loss-making
- These orders represent -$2.03M in profit at risk
- 18,553 orders score maximum risk on composite score

#### Finding 3 : Europe and LATAM highest risk by volume
- Europe: 5,458 critical orders, -$0.7M profit loss
- LATAM: 5,477 critical orders, -$0.6M profit loss
- Combined = 65% of total profit at risk
  
#### Finding 4 : Sports categories drive disproportionate losses
- Tennis & Racquet and Golf Apparel top the loss-making list
- As Seen on TV and Fitness Accessories follow
- Pattern suggests aggressive discounting eliminating margins
  
#### Finding 5: Order volume is not always aligned with delivery performance
- Some regions with moderate order counts experience higher delay percentages than larger markets.
- Operational efficiency varies significantly across regions.
- Improvement efforts should focus on highest-risk orders rather than only high-volume markets.

### Recommendations

1. **Route high-value orders to Standard Class**
   First and Second Class exceed 50% late rate. Standard Class operates at near-zero delay with 60% of volume. Switch orders with profit above $50 to Standard Class automatically.

2. **Set minimum margin floor for Sports categories**
   Increase price floor by 15-20% or cap discounts at 10% for Tennis, Golf, and As Seen on TV categories. Projected recovery: $400K–$600K annually.

3. **Weekly critical order review — Europe and LATAM**
   Use Page 2 dashboard filtered to these markets weekly and Escalate top 50 risk-score orders to carrier for priority handling. Focus on First Class orders
   these markets first.

4. **Evaluated profitability across all product categories**
   Introduce category-level margin controls, reduce aggressive discounting, and establish minimum profitability thresholds. Estimated recovery opportunity: $400K
   -$600K annually.
   
5. **Highest-risk orders requiring immediate intervention**
   Review the top 50 highest-risk orders weekly and allocate resources based on risk score rather than order volume.
--- 
## Dashboard Solution

### Executive Overview Dashboard

Provides a high-level operational summary including:


- 5 KPI cards: Total Orders, Late Rate %, Critical Orders, Profit at Risk, Loss Orders
- Donut chart: delivery status distribution
- Bar chart: late rate by shipping mode
- Combo chart: market volume vs critical orders
- Loss categories bar: top 10 loss-making categories
  <img width="1296" height="737" alt="Page1 Overview" src="https://github.com/user-attachments/assets/c273c702-1aa4-4fdc-bcc2-a03ffbc046d0" />

### Risk Action Dashboard

Designed for operational teams to identify and act on high-risk orders.
Features include:
- Dynamic KPI cards: critical order count + profit at risk
- Action table: filtered to Critical + High Risk orders only,
  sorted by risk score descending, with conditional formatting
- Bar chart: profit at risk by market
- Stacked bar: risk score distribution by shipping mode
- Slicers: Interactive Market and Shipping Mode Filters
<img width="1312" height="741" alt="Page2 ActionList" src="https://github.com/user-attachments/assets/2a008303-945f-4438-84ad-356b98eb65f0" />

---


### Dataset
- 180,519 orders across 5 markets (Europe, LATAM,
  Pacific Asia, USCA, Africa)
- 4 shipping modes (Standard Class, First Class,
  Second Class, Same Day)
- Columns: delivery timing, shipping mode, profit per order,
  customer segment, product category, market, etc.
- Dataset sourced from Kaggle : [https://www.kaggle.com/datasets/saicharankomati/dataco-supply-chain-dataset]
  Raw data not included in repo due to file size (180K+ rows).
  Download from the link above and run Power Query refresh to regenerate.

## Data Preparation

Built seven custom business metrics using Power Query:

| Column                    | Purpose                          |
| ------------------------- | -------------------------------- |
| Delivery_Delay_Days       | Measures delivery performance    |
| Delivery_Status_Clean     | Classifies delivery outcomes     |
| Profit_Category           | Segments order profitability     |
| Double_Loss_Flag          | Identifies critical orders       |
| Profit_at_Risk            | Quantifies financial exposure    |
| Shipping_Efficiency_Score | Evaluates shipping effectiveness |
| Order_Risk_Score          | Prioritises operational action   |

### Data Quality Investigation

A significant data quality issue was discovered during analysis.

The field named **Order_Item_Profit_Ratio** contained absolute profit values ranging from -$4,774 to +$911 rather than ratios.

The metric was reclassified as order-level profit and used accordingly throughout the analysis.

---

## Business Impact

### Key Results

* 180,519 Orders Analysed
* 19,421 Critical Orders Identified
* $2.03M Profit at Risk Quantified
* 18,553 Maximum-Risk Orders Prioritised
* 65% of Profit Risk Concentrated in Europe and LATAM

The final dashboard transformed raw operational data into an actionable risk-management tool, enabling teams to identify where delivery failures and profitability losses overlap and focus interventions on the highest-impact areas.

### Project Outcomes
Identified 19,421 critical risk orders representing $2.03M
in profit losses, enabled ops team to prioritise action
using a risk-sorted dashboard filtered by market and
shipping mode.

### Skills Demonstrated
- Power Query: data cleaning, type casting, 7 custom columns,
  M language formulas, nested if/else logic
- Excel: IFS formulas, combo charts, conditional formatting
  heatmap, PivotTables with slicers, reference lines
- Power BI: DAX measures, CALCULATE, DIVIDE, visual-level
  filters, conditional formatting, dual-axis combo charts,
  cross-page slicer design
- Analytics: data quality identification and resolution,
  composite risk scoring, business recommendation framing
