# Dataset Description

## 1. Dataset Overview

The project uses multiple interconnected datasets representing different business functions of a quick-commerce operation.

Instead of analyzing a single flat dataset, the project combines transactional, customer, product, delivery, inventory, marketing, and feedback data to create a unified analytical model in Power BI.

---

## 2. Data Sources Used

The main datasets used in the project are:

| Dataset | Business Area | Purpose |
|---|---|---|
| `blinkit_orders` | Sales | Order-level transactions and revenue |
| `blinkit_order_items` | Sales / Products | Products and quantities associated with orders |
| `blinkit_products` | Products | Product, category, pricing, and product attributes |
| `blinkit_customers` | Customers | Customer-level information |
| `blinkit_customer_feedback` | Customer Experience | Ratings and customer feedback |
| `blinkit_delivery_performance` | Delivery | Delivery status, variance, distance, and delivery details |
| `blinkit_inventory` | Inventory | Stock received and damaged stock |
| `blinkit_marketing_performance` | Marketing | Impressions, clicks, conversions, spend, and revenue |

---

## 3. Dataset Size

The project contains approximately:

| Dataset | Approx. Records |
|---|---:|
| Orders | 5,000 |
| Order Items | 5,000 |
| Products | 267 |
| Customers | 2,500 |
| Customer Feedback | 5,000 |
| Delivery Performance | 5,000 |
| Inventory | 75,000+ |
| Marketing Performance | 5,400 |

The exact number of records displayed in Power BI can depend on the final transformation and filtering context.

---

## 4. Orders Dataset

The `Orders` table represents order-level transactions.

Important fields include:

- `order_id`
- `customer_id`
- `order_date`
- `promised_delivery_time`
- `actual_delivery_time`
- `delivery_status`
- `order_total`
- `payment_method`
- `delivery_partner_id`

This table is primarily used for:

- Revenue analysis
- Order analysis
- AOV calculation
- Customer order analysis
- Time-based sales trends

---

## 5. Order Items Dataset

The `OrderItems` table contains product-level information associated with orders.

Important fields include:

- `order_id`
- `product_id`
- `quantity`
- `unit_price`

This table supports:

- Product sales analysis
- Unit volume analysis
- Product revenue calculations
- Product-level performance analysis

---

## 6. Products Dataset

The `Products` table contains product master information.

Important attributes include:

- `product_id`
- `product_name`
- `category`
- `brand`
- `price`
- `mrp`
- `margin_percentage`
- `shelf_life_days`
- `min_stock_level`

This table is used for:

- Category analysis
- Product analysis
- Revenue by category
- Inventory analysis
- Product-level comparisons

---

## 7. Customers Dataset

The `Customers` table contains customer-level information and is used to analyze customer purchasing behavior.

The dashboard uses this table to classify customers based on their order activity, including:

- One-Time Customers
- Repeat Customers

---

## 8. Customer Feedback Dataset

The `Feedback` table contains customer feedback information.

The dashboard uses this data for:

- Average customer rating
- Rating distribution
- Feedback volume trends

---

## 9. Delivery Dataset

The `Delivery` table contains operational delivery information.

Important fields include:

- `order_id`
- `delivery_status`
- `delivery_time_minutes`
- `distance km`
- `promise_time`
- `actual_time`
- `delivery_partner_id`
- `reason_if_delayed`

### Delivery Variance

In this project, `delivery_time_minutes` represents the difference between promised and actual delivery time.

Therefore:

```text
Negative value → Delivered early
Zero           → Delivered on promised time
Positive value → Delivered late
```
This field is used to analyze delivery variance and operational performance.
10. Inventory Dataset
The Inventory table contains inventory-related records.
Important fields include:
- product_id
- date
- stock_received
- damaged_stock
The dashboard calculates:
Net Stock = Stock Received − Damaged StockThis dataset supports:
- Stock analysis
- Damaged stock analysis
- Damage rate analysis
- Category-level inventory analysis
- Product-level inventory analysis
11. Marketing Dataset
The Marketing table contains marketing campaign performance data.
Important fields include:
- date
- impressions
- clicks
- conversions
- spend
- revenue_generated
These fields are used to calculate:
CTR = Clicks / Impressions

Conversion Rate = Conversions / Clicks

ROAS = Marketing Revenue / Marketing Spend
The dashboard also visualizes the marketing funnel:
Impressions
      ↓
Clicks
      ↓
Conversions
12. Date Table
A dedicated DateTable was created to support consistent time-based analysis across multiple datasets.
The DateTable includes:
- Date
- Year
- Month Number
- Month
- Year Month
- Quarter
- YearMonthKey
The DateTable is connected to the date fields of the relevant business tables and is used for monthly and yearly analysis.

13. Data Validation
Before building the dashboard, the datasets were reviewed for:
- Missing values
- Duplicate identifiers
- Data types
- Unique keys
- Date fields
- Category values
- Numerical fields
- Relationship compatibility
The data was then prepared for modeling and visualization in Power BI.

14. Excluded Dataset
An alternate inventory file named:
blinkit_inventoryNew.csv
was available in the source files but was not used in the final Power BI model.
The primary blinkit_inventory dataset was used for the inventory analysis.

15. Data Preparation Flow
Raw Datasets
     ↓
Data Quality Check
     ↓
Power Query Transformation
     ↓
Data Type Standardization
     ↓
Date Field Preparation
     ↓
Relationship Modeling
     ↓
DAX Calculations
     ↓
Power BI Dashboard
