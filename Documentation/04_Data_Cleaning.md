# Data Cleaning & Transformation

## 1. Overview

Before building the Power BI data model and dashboard, the source datasets were prepared and validated using Power Query.

The objective of the data preparation stage was to create clean, consistent, and analysis-ready tables while preserving the original business information.

---

## 2. Data Preparation Workflow

The overall workflow was:

```text
Raw CSV Files
      ↓
Import into Power BI
      ↓
Power Query
      ↓
Data Type Validation
      ↓
Column Standardization
      ↓
Date Field Preparation
      ↓
Data Quality Checks
      ↓
Close & Apply
      ↓
Data Modeling

```
3. Table Standardization
The imported datasets were renamed to clear business-friendly table names:
Original Dataset	Power BI Table
blinkit_orders	Orders
blinkit_order_items	OrderItems
blinkit_products	Products
blinkit_customers	Customers
blinkit_customer_feedback	Feedback
blinkit_delivery_performance	Delivery
blinkit_inventory	Inventory
blinkit_marketing_performance	Marketing


Clear table names make DAX formulas, relationships, and model navigation easier to manage.
4. Data Type Validation
Data types were reviewed before creating relationships and calculations.
The main fields validated included:
- Order IDs
- Customer IDs
- Product IDs
- Dates
- Revenue values
- Quantities
- Ratings
- Delivery variance
- Inventory quantities
- Marketing metrics
Date fields were particularly important because multiple tables contained date information.
5. Date Field Preparation
Dedicated date columns were prepared for the relevant business tables.
Orders
```
Order Date =
DATE(
    YEAR(Orders[order_date]),
    MONTH(Orders[order_date]),
    DAY(Orders[order_date])
)
Feedback
Feedback Date =
DATE(
    YEAR(Feedback[feedback_date]),
    MONTH(Feedback[feedback_date]),
    DAY(Feedback[feedback_date])
)
Inventory
Inventory Date =
DATE(
    YEAR(Inventory[date]),
    MONTH(Inventory[date]),
    DAY(Inventory[date])
)
Marketing
Marketing Date =
DATE(
    YEAR(Marketing[date]),
    MONTH(Marketing[date]),
    DAY(Marketing[date])
)
```
These fields were used to establish relationships with the centralized DateTable.
6. DateTable Preparation
A dedicated DateTable was created to provide consistent time intelligence across the dashboard.
The DateTable includes:
- Date
- Year
- Month Number
- Month
- Year Month
- Quarter
- YearMonthKey
The YearMonthKey was created to ensure chronological sorting of Year Month values.
```
YearMonthKey =
YEAR([Date]) * 100 + MONTH([Date])
```
The Year Month column was then sorted using YearMonthKey.
7. Data Quality Checks
The source data was reviewed for common data quality issues.
The checks included:
Duplicate identifiers
Primary business identifiers such as:
- order_id
- product_id
were checked for uniqueness where appropriate.
Missing values
Important fields were reviewed for missing or blank values.
Invalid data types
Numerical, date, and categorical fields were checked to ensure they were suitable for analysis.
Category validation
Category fields were reviewed to identify unexpected blank or unmatched categories.
8. Delivery Data Handling
The delivery variance field was reviewed carefully.
delivery_time_minutes represents the difference between promised and actual delivery time.
Therefore, negative values were retained because they represent early deliveries.

```
Negative → Early
0        → On Time
Positive → Late
```
Negative values were not removed as errors.
This preserves the operational meaning of the source data.
9. Delayed Delivery Reasons
The reason_if_delayed field was also reviewed.
Blank values in this field can occur for orders that were not delayed and therefore do not necessarily represent missing data errors.
The field was therefore not treated as universally invalid simply because some records were blank.
10. Product and Category Validation
Product-related tables were reviewed to ensure that product identifiers could be connected between:

```
Products
   ↓
OrderItems
   ↓
Orders
```
and:
```
Products
   ↓
Inventory
```
Unmatched or blank category results were reviewed during the final dashboard cleanup.
11. Alternate Inventory Dataset
An alternate inventory file:
```
blinkit_inventoryNew.csv
```
was intentionally excluded from the final model.
The primary inventory dataset was retained for the dashboard.

12. Final Data Preparation Result
After completing the preparation process, the data was ready for:
- Relationship modeling
- DAX calculations
- KPI creation
- Interactive visualization
- Dashboard development
The cleaned tables were loaded into the Power BI model using Close & Apply.

13. Data Preparation Principles
The preparation process followed these principles:
- Preserve valid source information
- Avoid deleting meaningful records unnecessarily
- Validate data before modeling
- Standardize table and field usage
- Separate data preparation from analytical calculations
- Maintain consistent date handling across business areas

