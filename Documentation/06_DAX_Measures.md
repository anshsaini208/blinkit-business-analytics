# DAX Measures

## 1. Overview

DAX (Data Analysis Expressions) was used to create reusable measures and calculated columns for the Power BI dashboard.

The measures were designed to support:

- Sales KPIs
- Customer analytics
- Delivery analysis
- Inventory analysis
- Marketing performance
- Product analysis
- Customer feedback

---

# 2. Sales Measures

## Total Revenue

Calculates total revenue from the Orders table.

```DAX
Total Revenue =
SUM(Orders[order_total])
```
Total Orders
Counts distinct orders.
Total Orders =
DISTINCTCOUNT(Orders[order_id])
Average Order Value (AOV)
Calculates the average revenue generated per order.
AOV =
DIVIDE(
    [Total Revenue],
    [Total Orders]
)
Total Customers
Counts distinct customers who placed orders.
Total Customers =
DISTINCTCOUNT(Orders[customer_id])
Total Units
Calculates the total quantity of products sold.
Total Units =
SUM(OrderItems[quantity])
Product Revenue
Calculates revenue at the product-item level using quantity and unit price.
Product Revenue =
SUMX(
    OrderItems,
    OrderItems[quantity] * OrderItems[unit_price]
)
Average Orders per Customer
Calculates the average number of orders per customer.
Average Orders per Customer =
DIVIDE(
    [Total Orders],
    [Total Customers]
)
3. Customer Measures
Customer Order Count
A calculated column used to determine the number of orders associated with each customer.
Customer Order Count =
CALCULATE(
    DISTINCTCOUNT(Orders[order_id])
)
Customer Purchase Type
Classifies customers according to their order activity.
Customer Purchase Type =
SWITCH(
    TRUE(),
    Customers[Customer Order Count] = 0, "No Orders",
    Customers[Customer Order Count] = 1, "One-Time Customer",
    "Repeat Customer"
)
This classification supports the Customer Purchase Behavior visual.
4. Delivery Measures
Delivery Orders
Counts distinct delivery orders.
Delivery Orders =
DISTINCTCOUNT(Delivery[order_id])
On-Time Delivery %
Calculates the percentage of delivery orders classified as "On Time".
On Time Delivery % =
DIVIDE(
    CALCULATE(
        DISTINCTCOUNT(Delivery[order_id]),
        Delivery[delivery_status] = "On Time"
    ),
    DISTINCTCOUNT(Delivery[order_id])
)
Delayed Orders
Counts orders whose delivery status is not "On Time".
Delayed Orders =
CALCULATE(
    DISTINCTCOUNT(Delivery[order_id]),
    Delivery[delivery_status] <> "On Time"
)
Delayed Order %
Calculates the percentage of total orders classified as delayed.
Delayed Order % =
DIVIDE(
    [Delayed Orders],
    [Total Orders]
)
Average Delivery Variance
Calculates the average value of the delivery variance field.
Average Delivery Variance =
AVERAGE(Delivery[Delivery time minutes])
Interpretation
Negative → Early delivery
0        → On promised time
Positive → Late delivery
Average Delivery Distance
Calculates the average delivery distance.
Average Delivery Distance =
AVERAGE(Delivery[distance km])
5. Customer Feedback Measures
Average Rating
Calculates the average customer rating.
Average Rating =
AVERAGE(Feedback[rating])
Feedback Count
Counts feedback records.
Feedback Count =
COUNTROWS(Feedback)
Average Rating Display
Formats the average rating for KPI display.
Average Rating Display =
"★ " & FORMAT([Average Rating], "0.00")
6. Inventory Measures
Total Stock
Calculates total stock received.
Total Stock =
SUM(Inventory[stock_received])
Damaged Stock
Calculates total damaged stock.
Damaged Stock =
SUM(Inventory[damaged_stock])
Damage Rate
Calculates damaged stock as a percentage of total stock.
Damage Rate =
DIVIDE(
    [Damaged Stock],
    [Total Stock]
)
Net Stock
Calculates stock remaining after subtracting damaged stock.
Current Stock =
SUM(Inventory[stock_received])
- SUM(Inventory[damaged_stock])
The measure is used in the dashboard as Net Stock.

Total Products
Counts distinct products.
Total Products =
DISTINCTCOUNT(Products[product_id])
7. Marketing Measures
Total Marketing Spend
Calculates total marketing expenditure.
Total Marketing Spend =
SUM(Marketing[spend])
Marketing Revenue
Calculates revenue generated through marketing activities.
Marketing Revenue =
SUM(Marketing[revenue_generated])
ROAS
Calculates Return on Ad Spend.
ROAS =
DIVIDE(
    [Marketing Revenue],
    [Total Marketing Spend]
)
Formula
ROAS = Marketing Revenue / Marketing Spend
Total Impressions
Total Impressions =
SUM(Marketing[impressions])
Total Clicks
Total Clicks =
SUM(Marketing[clicks])
Total Conversions
Total Conversions =
SUM(Marketing[conversions])
Marketing CTR
Calculates the percentage of impressions that resulted in clicks.
Marketing CTR =
DIVIDE(
    SUM(Marketing[clicks]),
    SUM(Marketing[impressions])
)
Marketing Conversion Rate
Calculates conversions as a percentage of clicks.
Marketing Conversion Rate =
DIVIDE(
    SUM(Marketing[conversions]),
    SUM(Marketing[clicks])
)
8. Dynamic Product Analysis
A field parameter was created to allow users to switch between product performance metrics.
The parameter contains:
Total Units
Product Revenue
The dynamic measure is:
Selected Product Metric =
SWITCH(
    SELECTEDVALUE('Top Product Metric'[Top Product Metric]),
    "Total Units", [Total Units],
    "Product Revenue", [Product Revenue],
    [Total Units]
)
This allows the Top 10 Products Performance visual to switch between:
- Product volume
- Product revenue
Product Ranking
The following measure ranks products dynamically based on the selected metric.
Product Rank =
RANKX(
    ALLSELECTED(Products[product_name]),
    [Selected Product Metric],
    ,
    DESC,
    DENSE
)
The visual is filtered to show products with:
Product Rank <= 10
This creates a dynamic Top 10 product analysis.
9. Marketing Funnel Measures
A disconnected calculated table was created for the marketing funnel.
Marketing Funnel =
DATATABLE(
    "Stage", STRING,
    "SortOrder", INTEGER,
    {
        {"Impressions", 1},
        {"Clicks", 2},
        {"Conversions", 3}
    }
)
The stages are:
Impressions
     ↓
Clicks
     ↓
Conversions
Marketing Funnel Value
Marketing Funnel Value =
SWITCH(
    SELECTEDVALUE('Marketing Funnel'[Stage]),
    "Impressions", [Total Impressions],
    "Clicks", [Total Clicks],
    "Conversions", [Total Conversions]
)
This measure allows the funnel chart to display the appropriate metric for each stage.
10. Measure Design Principles
The DAX layer follows several principles:
- Reusable measures instead of hard-coded values
- DIVIDE() for safer ratio calculations
- Distinct counts for order and customer identifiers
- Filter-aware calculations using CALCULATE()
- Dynamic analysis using SWITCH()
- Ranking using RANKX()
- Aggregations using SUM(), AVERAGE(), and COUNTROWS()
11. DAX Summary
The DAX layer provides the analytical foundation for the dashboard.
It converts raw transactional data into business metrics such as:
Revenue
Orders
AOV
Customers
Units
Delivery Performance
Delivery Variance
Inventory Health
Damage Rate
ROAS
CTR
Conversion Rate
Customer Ratings
Product Rankings
These measures are reused throughout the five dashboard pages to provide consistent calculations and interactive analysis.
