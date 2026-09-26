# Data Model

## 1. Overview

The Power BI solution uses a relational data model to connect sales, customer, product, delivery, inventory, marketing, and feedback data.

The model was designed to support:

- Consistent filtering
- Cross-table analysis
- Time-based reporting
- Reusable DAX measures
- Interactive dashboard exploration

---

## 2. Main Tables

The final model contains the following tables:

### Fact / Transaction Tables

- `Orders`
- `OrderItems`
- `Delivery`
- `Inventory`
- `Marketing`
- `Feedback`

### Dimension / Reference Tables

- `Customers`
- `Products`
- `DateTable`

---

## 3. Relationship Structure

The major relationships in the model are:

```text
                         DateTable
                       /    |    |    \
                      /     |    |     \
                     ↓      ↓    ↓      ↓
                 Orders  Feedback Inventory Marketing
                   |
          ┌────────┼──────────┐
          ↓        ↓          ↓
     OrderItems  Delivery   Feedback
          |
          ↓
       Products
          |
          ↓
      Inventory

Customers
    |
    ├────────→ Orders
    |
    └────────→ Feedback

Products
    |
    ├────────→ OrderItems
    |
    └────────→ Inventory
```
4. Relationship Details
DateTable → Orders
DateTable[Date]
        1
        |
        *
Orders[Order Date]
Purpose:
- Order trends
- Monthly analysis
- Year filtering
- Revenue trends
- Order trends
DateTable → Feedback
DateTable[Date]
        1
        |
        *
Feedback[Feedback Date]
Purpose:
- Feedback trends
- Rating analysis over time
DateTable → Inventory
DateTable[Date]
        1
        |
        *
Inventory[Inventory Date]
Purpose:
- Inventory analysis over time
DateTable → Marketing
DateTable[Date]
        1
        |
        *
Marketing[Marketing Date]
Purpose:
- Marketing spend trends
- Marketing revenue trends
- Funnel analysis over time
Customers → Orders
Customers[customer_id]
        1
        |
        *
Orders[customer_id]
Purpose:
- Customer order analysis
- Orders per customer
- Repeat customer analysis
Orders → OrderItems
Orders[order_id]
        1
        |
        *
OrderItems[order_id]
Purpose:
- Connecting order-level transactions with product-level details
Products → OrderItems
Products[product_id]
        1
        |
        *
OrderItems[product_id]
Purpose:
- Product sales analysis
- Category revenue analysis
- Unit analysis
Orders → Delivery
Orders[order_id]
        1
        |
        *
Delivery[order_id]
Purpose:
- Connecting orders with delivery performance
Customers → Feedback
Customers[customer_id]
        1
        |
        *
Feedback[customer_id]
Purpose:
- Customer experience analysis
Products → Inventory
Products[product_id]
        1
        |
        *
Inventory[product_id]
Purpose:
- Product-level inventory analysis
- Category-level inventory analysis
5. Relationship Design
The relationships primarily use a one-to-many (1:*) structure.
The dimension/reference side contains unique identifiers, while the related transaction tables can contain multiple records.
Examples:
Customer
   1
   ↓
Many Orders
and:
Product
   1
   ↓
Many OrderItems
This structure allows filters from dimension tables to propagate to related transaction tables.
6. Filter Direction
Relationships were configured primarily with single-direction filtering.
This helps maintain a predictable filter flow and reduces the possibility of ambiguous filtering paths.
The model was intentionally designed to avoid unnecessary bidirectional relationships.
7. Feedback and Orders Relationship
An additional relationship exists between:
Orders[order_id]
        |
        *
Feedback[order_id]
This relationship was kept inactive in the final model to avoid creating an ambiguous active filter path between Orders, Customers, and Feedback.
The active relationship between:
Customers → Feedback
is used for the primary customer feedback analysis.
8. Centralized DateTable
A dedicated DateTable acts as the central time dimension.
It contains:
```
Date
Year
Month Number
Month
Year Month
Quarter
YearMonthKey
```
The YearMonthKey is used to maintain chronological ordering of the Year Month field.

```
YearMonthKey =
YEAR([Date]) * 100 + MONTH([Date])
```
For example:
January 2024  → 202401
February 2024 → 202402
March 2024    → 202403
This prevents alphabetical sorting of month labels.
9. Model Design Benefits
The relational model provides several benefits:
Consistent Time Analysis
The DateTable provides a common time dimension across multiple business areas.
Reusable Measures
DAX measures can be reused across multiple dashboard pages.
Interactive Filtering
Users can select categories, products, dates, delivery statuses, and other dimensions to explore the data.
Reduced Ambiguity
Single-direction relationships help maintain predictable filter propagation.
Scalable Structure
Additional measures and visualizations can be added without redesigning the entire dashboard model.
10. Data Model Summary
```
The final Power BI model connects:
Customers
    ↓
Orders
    ↓
OrderItems
    ↓
Products
    ↓
Inventory

Orders
    ↓
Delivery

Customers
    ↓
Feedback

DateTable
    ↓
Orders
    ↓
Feedback
    ↓
Inventory
    ↓
Marketing
```
This model provides the foundation for the five-page analytical dashboard.
11. Modeling Objective
The primary modeling objective was to create a reliable and understandable structure that supports business analysis while minimizing unnecessary complexity.
The final model enables analysis across:
- Sales
- Customers
- Products
- Delivery
- Inventory
- Marketing
- Customer Experience
- Time
