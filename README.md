## Supply Chain Delivery Performance & Profitability Analysis

Supply chain orders across 5 markets - identify where delivery failures and profit losses overlap and quantify the financial impact on business operations.

### Business Problem

The company had no single view showing where operational inefficiencies and profitability issues occurred together.

While delivery delays were being monitored separately and financial performance was tracked independently, there was no way to identify:

1. Which shipping methods were driving delivery failures?
2. Which markets generated the highest operational risk?
3. Which product categories consistently lost money?
4. Which specific orders required immediate action?
5. Which customer segment creates the greatest operational workload?


**Dataset:** DataCoSupplyChainDataset ( 180,519 orders across 5 markets, 4 Shipping Modes and 3 Segments)
- Dataset sourced from Kaggle : [https://www.kaggle.com/datasets/saicharankomati/dataco-supply-chain-dataset]
  Raw data not included in repo due to file size (180K+ rows).

## Tools Used

|---|---|
| Tools | Excel (Power Query), Power BI, DAX |
| Domain |Supply Chain, Logistics, E-Commerce Operations |


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

Analysis : Evaluated profitability across all product categories.

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

### 5. Which customer segment creates the greatest operational risk for the supply chain?

#### Analysis
Evaluated Critical orders across Customer Segments.

#### Insights
Consumer Segment: ~94K orders (51.1% of total orders)
10K Critical orders
16K Loss orders
$1.4M profit at risk

#### Recommendation

Prioritize monitoring and resolution of critical Corporate orders. Focus on reducing loss orders to protect revenue and customer relationships.

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
- Consumer segment accounts for the highest number of critical orders.
- High order volume is translating into greater operational pressure.
- Critical orders require immediate attention to prevent service disruptions.

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
   
5. **High Critical orders by Segment requiring immediate intervention**
   Prioritize monitoring and resolution of critical Consumer orders.
   
---

## Dashboard Solution

 <img width="988" height="568" alt="Supply Chain Dashboard" src="https://github.com/user-attachments/assets/0310e763-860a-40c7-a8bd-a03856fbd8bb" />
 
### Executive Overview Dashboard

Provides a high-level operational summary including:
- 6 KPI cards: Total Orders, Late Rate %, Critical Orders, Profit at Risk, Loss Orders, Total Orders by Delivery Status
- Donut chart: delivery status distribution
- Bar chart: late rate by shipping mode
- Combo chart: market volume vs critical orders
- Bar chart Segment vs Critical orders
- Loss categories bar: top 10 loss-making categories


<img width="983" height="547" alt="Risk Action Page" src="https://github.com/user-attachments/assets/b61e8eb0-4bbb-4df9-8984-7a18d3c40c5e" />

### Risk Action Dashboard

Designed for operational teams to identify and act on high-risk orders.
Features include:
- Dynamic KPI cards: critical order count + profit at risk
- Action table: filtered to Critical + High Risk orders only,
  sorted by risk score descending, with conditional formatting
- Bar chart: profit at risk by market
- Stacked bar: risk score distribution by shipping mode
- Slicers: Interactive Market and Shipping Mode and Segment Filters

---

## Data Preparation in Excel

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


## Repository structure

```
Supply-Chain-Delivery-Performance-Profitability-Analysis/
├── images/
|      ├──Power BI/
│             ├── Page 1 Overview.png
│             └── Page 2 Risk Action.png
|             └── SupplyChainDashboard.pbix
|             └── readme.txt
├── README.md
```


