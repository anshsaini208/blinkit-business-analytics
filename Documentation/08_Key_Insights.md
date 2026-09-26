# Key Business Insights

## 1. Overview

The dashboard provides a consolidated view of sales, customer behavior, delivery operations, inventory, marketing performance, and customer experience.

The following observations are based on the metrics and visualizations available in the final Power BI dashboard.

> These are descriptive observations from the available data. They do not imply causation unless separately validated.

---

# 2. Sales & Revenue

### Revenue and Orders

The dashboard reports approximately:

- **₹11.01M Total Revenue**
- **5K Total Orders**
- **₹2.20K Average Order Value**

This provides a high-level view of the scale and average transaction value represented in the dataset.

### Category Performance

Revenue varies across product categories, allowing categories to be compared based on their contribution to product revenue.

The dashboard can be filtered by category to further explore category-level performance.

---

# 3. Customer Behavior

### Customer Base

The dashboard reports approximately:

- **2K customers**
- **2.30 average orders per customer**

### Repeat vs One-Time Customers

The customer purchase analysis currently shows approximately:

- **68.69% Repeat Customers**
- **31.31% One-Time Customers**

This indicates that repeat purchasing represents a substantial portion of the customer population represented in the analysis.

The dashboard allows this behavior to be explored alongside order and product metrics.

---

# 4. Delivery Performance

### On-Time Delivery

The dashboard reports:

- **69.4% On-Time Delivery**
- **30.6% Delayed Orders**

The delivery-status distribution further separates delayed orders into:

- Slightly Delayed
- Significantly Delayed

### Delivery Variance

The average delivery variance is approximately:

**4.44 minutes**

The dashboard treats delivery variance as the difference between promised and actual delivery time.

```text
```
This allows both early and late deliveries to remain visible in the analysis.
Delivery Distance
The average delivery distance is approximately:
2.72 km
The dashboard also allows delivery variance to be explored across distance ranges.
The dashboard shows these variables together, but it does not establish that distance causes delivery delays.

5. Inventory Performance
Stock Position
The dashboard reports approximately:
- 148K Total Stock Received
- 80K Damaged Stock
- 67K Net Stock
The calculated damage rate is:
54.41%
Inventory Analysis
The inventory page provides several perspectives:
- Damage Rate by Category
- Net Stock by Product
- Net Stock by Category
- Product Revenue vs Net Stock
- Stock Received vs Damaged Stock
These views allow inventory conditions to be compared across products and categories.
The high damage-rate value should be interpreted according to the exact business meaning of the source inventory fields. The dashboard reports the calculated metric but does not independently establish the operational cause of the damaged stock.

6. Marketing Performance
The dashboard reports:
- ₹16.32M Marketing Spend
- ₹32.19M Marketing Revenue
- 1.97 ROAS
- 10.09% CTR
- 10.02% Conversion Rate
Marketing Funnel
The marketing funnel tracks:
29.49M Impressions
       ↓
2.97M Clicks
       ↓
298K Conversions
This provides a high-level view of movement through the marketing funnel.
Important Interpretation
ROAS, CTR, and conversion rate are descriptive performance metrics.
The dashboard does not independently establish whether marketing activity caused the reported revenue.
7. Customer Experience
Average Rating
The dashboard reports an average customer rating of approximately:
3.34 / 5
Rating Distribution
The Customer Rating Distribution visual provides a breakdown of feedback across rating levels.
Feedback Trend
The Customer Feedback Trend provides a monthly view of feedback activity.
Together, these visuals provide both:
- Rating composition
- Feedback volume over time
8. Cross-Functional Observations
The dashboard connects several business areas that can be explored together.
For example:
Sales
  ↓
Products
  ↓
Inventory
and:
Orders
  ↓
Delivery
  ↓
Customer Feedback
and:
Marketing
  ↓
Impressions
  ↓
Clicks
  ↓
Conversions
These relationships allow users to investigate business performance from multiple perspectives rather than relying on a single KPI.
9. Areas for Further Analysis
The current dashboard identifies several areas that could be investigated further with additional analysis:
Delivery
- Investigate reasons behind delayed deliveries
- Analyze delivery performance by additional operational dimensions
- Examine delivery variance distributions in more detail
Inventory
- Investigate the operational meaning of damaged-stock records
- Identify products with high stock but comparatively lower revenue
- Analyze stock levels against minimum stock requirements
Customers
- Analyze customer lifetime value
- Identify customer churn patterns
- Segment customers using purchasing behavior
Marketing
- Compare campaign performance at a deeper level
- Analyze marketing efficiency across campaigns
- Investigate conversion behavior over time
Sales
- Analyze product-level contribution to revenue
- Study order-value patterns
- Develop demand forecasting models
10. Important Analytical Limitation
The dashboard is primarily a descriptive analytics solution.
It reports and visualizes patterns in the available data.
The following types of conclusions would require additional analysis:
- Causal relationships
- Predictive outcomes
- Forecasted business performance
- Statistical significance
- Root-cause determination
Negative → Early
0        → On Time
Positive → Late
