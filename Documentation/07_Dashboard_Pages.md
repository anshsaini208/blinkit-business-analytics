# Dashboard Pages

## 1. Overview

The final Power BI dashboard is organized into five analytical pages.

Each page focuses on a specific business area while maintaining a consistent visual design and interactive filtering experience.

---

# 2. Page 1 — Executive Overview

## Purpose

The Executive Overview provides a high-level summary of business performance.

It is designed to help users quickly understand the overall state of the business before moving into detailed analysis.

## Key Performance Indicators

The page includes:

- Total Revenue
- Total Orders
- Average Order Value (AOV)
- Total Customers
- Average Rating

## Visualizations

### Revenue & Orders Trend

Displays monthly revenue and order trends using:

- Year Month
- Total Revenue
- Total Orders

This provides a combined view of sales value and order activity over time.

### Revenue by Category

Shows product revenue across different product categories.

This helps compare category-level contribution to overall product revenue.

### Delivery Status Distribution

Shows the distribution of delivery orders across delivery statuses.

The main statuses include:

- On Time
- Slightly Delayed
- Significantly Delayed

## Interactive Controls

- Year slicer
- Cross-filtering between visuals

---

# 3. Page 2 — Sales & Customer Analytics

## Purpose

This page focuses on sales trends, product performance, order values, and customer purchasing behavior.

## Key Performance Indicators

- Average Orders per Customer
- Total Orders
- AOV
- Total Customers
- Total Units

## Visualizations

### Monthly Order Trend

Shows the number of orders across months.

### Revenue by Category

Compares product revenue across categories.

### Top 10 Products Performance

Displays the top-performing products.

A dynamic metric selector allows users to switch between:

- Total Units
- Product Revenue

This allows product performance to be evaluated from both volume and revenue perspectives.

### Order Value Distribution

Displays the distribution of orders across different order-value ranges.

### Customer Purchase Behavior

Classifies customers based on order activity into categories such as:

- One-Time Customer
- Repeat Customer

---

# 4. Page 3 — Delivery & Operations Analytics

## Purpose

This page analyzes delivery performance and operational delivery characteristics.

## Key Performance Indicators

- On-Time Delivery %
- Delayed Order %
- Delayed Orders
- Average Delivery Variance
- Average Delivery Distance

## Visualizations

### Delivery Status Distribution

Shows the distribution of orders across delivery statuses.

### Delivery Variance Distribution

Shows the distribution of delivery variance values.

The variance represents the difference between promised and actual delivery time.

```text
Negative → Early
0        → On Time
Positive → Late
```
Average Variance by Delivery Status
Compares average delivery variance across delivery-status categories.
Delivery Variance Across Distance
Analyzes average delivery variance across distance ranges.
This provides an additional operational view of delivery performance.
5. Page 4 — Inventory & Product Analytics
Purpose
This page focuses on inventory levels, damaged stock, product revenue, and category-level inventory performance.
Key Performance Indicators
- Total Stock Received
- Damaged Stock
- Damage Rate
- Net Stock
- Total Products
Visualizations
Damage Rate by Category
Compares the calculated damage rate across product categories.
Net Stock by Product
Shows net stock at the product level.
Net Stock = Stock Received − Damaged Stock
Net Stock by Category
Compares net stock across product categories.
Product Revenue vs Net Stock
A scatter plot comparing product revenue against net stock.
The visual allows users to explore the relationship between product-level sales and inventory position.
Stock Received vs Damaged Stock
Compares total stock received and damaged stock across categories.
6. Page 5 — Marketing & Customer Experience Analytics
Purpose
This page combines marketing performance metrics with customer experience analysis.
Key Performance Indicators
- Marketing Spend
- Marketing Revenue
- ROAS
- Marketing CTR
- Marketing Conversion Rate
Visualizations
Marketing Spend vs Revenue Trend
Displays marketing spend and marketing-generated revenue over time.
Marketing Conversion Funnel
The funnel follows:
Impressions
     ↓
Clicks
     ↓
Conversions
This visual provides a high-level view of marketing activity progression.
Customer Rating Distribution
Shows the distribution of customer ratings.
Customer Feedback Trend
Displays the number of customer feedback records over time.
7. Dashboard Interactivity
The dashboard supports interactive exploration through:
- Year filtering
- Category filtering
- Product filtering
- Delivery status filtering
- Cross-filtering between visuals
- Dynamic product metric selection
Users can select elements within visuals and observe changes across related KPIs and charts.
8. Visual Design
A consistent visual theme was applied across all five pages.
Primary Theme
- Blinkit-inspired yellow
- White analytical cards
- Dark text
- Gray secondary labels
- Green for positive/on-time indicators
- Red for delayed or negative indicators
Design Principles
The dashboard emphasizes:
- Clear visual hierarchy
- Consistent KPI placement
- Minimal visual clutter
- Business-focused chart selection
- Consistent naming and formatting
- Interactive exploration
9. Dashboard Navigation
The dashboard is organized from high-level analysis to detailed business areas:
Executive Overview
        ↓
Sales & Customer Analytics
        ↓
Delivery & Operations Analytics
        ↓
Inventory & Product Analytics
        ↓
Marketing & Customer Experience
This structure allows users to begin with overall business performance and progressively explore specific operational areas.
10. Dashboard Outcome
The five-page dashboard provides a consolidated analytical environment covering:
- Business performance
- Sales
- Customers
- Products
- Delivery
- Inventory
- Marketing
- Customer experience
The dashboard combines these areas into a single interactive Power BI reporting solution.


