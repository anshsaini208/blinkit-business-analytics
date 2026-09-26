# 🛒 Blinkit Business Performance & Operations Analytics

> Interactive Power BI dashboard analyzing sales, customers, delivery operations, inventory, marketing performance, and customer experience.

---

## 📊 Dashboard Preview

### Executive Overview

![Executive Overview](https://github.com/anshsaini208/blinkit-business-analytics/blob/main/Screenshots/executive-overview.png)

### Sales & Customer Analytics

![Sales & Customer Analytics](https://github.com/anshsaini208/blinkit-business-analytics/blob/main/Screenshots/sales-customer-analytics.png)

### Delivery & Operations Analytics

![Delivery & Operations](https://github.com/anshsaini208/blinkit-business-analytics/blob/main/Screenshots/delivery-operations.png)

### Inventory & Product Analytics

![Inventory & Product Analytics](https://github.com/anshsaini208/blinkit-business-analytics/blob/main/Screenshots/inventory-product-analytics.png)

### Marketing & Customer Experience

![Marketing & Customer Experience](https://github.com/anshsaini208/blinkit-business-analytics/blob/main/Screenshots/marketing-customer-experience.png)

---

# 🎯 Project Overview

This project is an interactive Business Intelligence solution developed using **Microsoft Power BI** to analyze the performance of a Blinkit-style quick-commerce business.

The dashboard integrates multiple business datasets into a unified analytical model and provides interactive analysis across:

- Sales & Revenue
- Customer Behavior
- Product Performance
- Delivery Operations
- Inventory
- Marketing
- Customer Experience

The solution demonstrates practical skills in **Power BI, Power Query, DAX, data modeling, KPI development, and business-oriented data visualization**.

---

# 💼 Business Problem

Quick-commerce businesses generate data across multiple operational areas.

Analyzing these datasets independently makes it difficult to obtain a unified view of business performance.

This project addresses that challenge by integrating multiple datasets into a centralized Power BI model and providing an interactive dashboard for business analysis.

### Key Business Questions

- What is the overall revenue and order performance?
- What is the average order value?
- Which product categories contribute to revenue?
- What is the customer repeat-purchase behavior?
- How effectively are orders being delivered?
- How much inventory is received and damaged?
- How is marketing spend performing?
- What does customer feedback look like?

---

# 📌 Dashboard Pages

| Page | Focus |
|---|---|
| **Executive Overview** | Overall business performance |
| **Sales & Customer Analytics** | Sales trends, products & customer behavior |
| **Delivery & Operations** | Delivery performance & variance |
| **Inventory & Product Analytics** | Stock, damage & product performance |
| **Marketing & Customer Experience** | Marketing metrics & customer feedback |

---

# 📈 Key Metrics

| Metric | Current Dashboard Value |
|---|---:|
| Total Revenue | ₹11.01M |
| Total Orders | 5K |
| Average Order Value | ₹2.20K |
| Total Customers | 2K |
| Average Rating | 3.34 |
| On-Time Delivery | 69.4% |
| Delayed Orders | 30.6% |
| Average Delivery Variance | 4.44 min |
| Average Delivery Distance | 2.72 km |
| Total Stock | 148K |
| Damaged Stock | 80K |
| Damage Rate | 54.41% |
| Net Stock | 67K |
| Marketing Spend | ₹16.32M |
| Marketing Revenue | ₹32.19M |
| ROAS | 1.97 |
| Marketing CTR | 10.09% |
| Marketing Conversion Rate | 10.02% |

> Metrics shown above represent the current dashboard state and may change when filters are applied.

---

# 🧩 Data Model

The project combines the following business tables:

```text
Orders
OrderItems
Products
Customers
Feedback
Delivery
```
Main analytical relationships
```
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
A centralized DateTable is used for consistent time-based analysis.
🧮 DAX
Key DAX calculations include:
- Total Revenue
- Total Orders
- AOV
- Total Customers
- Total Units
- Product Revenue
- On-Time Delivery %
- Delayed Orders %
- Average Delivery Variance
- Damage Rate
- Net Stock
- ROAS
- Marketing CTR
- Marketing Conversion Rate
- Average Rating
- Dynamic Product Ranking
A dynamic Top 10 Products analysis allows users to switch between:
Total Units
       ↕
Product Revenue
🛠️ Technology Stack
Business Intelligence
- Microsoft Power BI
Data Preparation
- Power Query
Analytics
- DAX
- Data Modeling
- KPI Analysis
- Exploratory Data Analysis
Version Control
- Git
- GitHub
📂 Repository Structure
```
blinkit-business-analytics/
│
├── Dashboard/
│   └── Blinkit_Business_Analytics.pbix
│
├── Documentation/
│   ├── 01_Project_Overview.md
│   ├── 02_Business_Problem.md
│   ├── 03_Dataset_Description.md
│   ├── 04_Data_Cleaning.md
│   ├── 05_Data_Model.md
│   ├── 06_DAX_Measures.md
│   ├── 07_Dashboard_Pages.md
│   ├── 08_Key_Insights.md
│   └── 09_Future_Enhancements.md
│
├── Screenshots/
│   ├── 01-executive-overview.png
│   ├── 02-sales-customer-analytics.png
│   ├── 03-delivery-operations.png
│   ├── 04-inventory-product-analytics.png
│   └── 05-marketing-customer-experience.png
│
├── Dataset/
└── README.md

```
🔍 Key Analytical Observations
Sales
The dashboard reports approximately ₹11.01M in revenue across 5K orders, with an AOV of approximately ₹2.20K.
Customers
The current dashboard reports approximately 2.30 orders per customer, with the customer purchase analysis showing a substantial proportion of repeat customers.
Delivery
The dashboard reports 69.4% on-time delivery and 30.6% delayed orders, with an average delivery variance of 4.44 minutes.
Inventory
The dashboard reports approximately 148K stock received, 80K damaged stock, and 67K net stock.
Marketing
Marketing performance currently shows:
- ₹16.32M spend
- ₹32.19M marketing revenue
- 1.97 ROAS
- 10.09% CTR
- 10.02% conversion rate
Customer Experience
The dashboard reports an average customer rating of approximately 3.34/5 and provides rating-distribution and feedback-trend analysis.
These are descriptive observations from the dashboard. They should not be interpreted as causal conclusions without additional analysis.

📚 Documentation
Detailed project documentation is available here:
- [Project Overview](https://github.com/anshsaini208/blinkit-business-analytics/blob/main/Documentation/project_Overview.md)
- [Business Problem](https://github.com/anshsaini208/blinkit-business-analytics/blob/main/Documentation/02_Business_Problem.md)
- [Dataset Description](https://github.com/anshsaini208/blinkit-business-analytics/blob/main/Documentation/03_Dataset_Description.md)
- [Data Cleaning & Transformation](https://github.com/anshsaini208/blinkit-business-analytics/blob/main/Documentation/04_Data_Cleaning.md)
- [Data Model](
https://github.com/anshsaini208/blinkit-business-analytics/blob/main/Documentation/05_Data_Model.md)
- [DAX Measures](https://github.com/anshsaini208/blinkit-business-analytics/blob/main/Documentation/06_DAX_Measures.md)
- [Dashboard Pages](https://github.com/anshsaini208/blinkit-business-analytics/blob/main/Documentation/07_Dashboard_Pages.md)
- [Key Insights](https://github.com/anshsaini208/blinkit-business-analytics/blob/main/Documentation/08_Key_Insights.md)
- [Future Enhancements](https://github.com/anshsaini208/blinkit-business-analytics/blob/main/Documentation/09_Future_Enhancements.md)
🚀 Future Enhancements
Potential extensions include:
- Demand forecasting
- Inventory optimization
- Delivery delay prediction
- Customer segmentation
- Customer churn analysis
- Advanced marketing attribution
- Automated data refresh
- Real-time operational monitoring
- Anomaly detection
These are proposed future enhancements and are not part of the current implementation.
👨‍💻 Author
Ansh Saini
B.Tech — Computer Science / Artificial Intelligence & Machine Learning
COER University
Skills Demonstrated
Power BI DAX Power Query Data Modeling Data Analysis Data Visualization SQL Python
⭐ Project Highlights
- Built a 5-page interactive Power BI dashboard
- Integrated multiple business datasets
- Created a structured relational data model
- Developed reusable DAX measures
- Implemented interactive cross-filtering
- Built dynamic Top 10 product analysis
- Analyzed sales, customers, delivery, inventory, marketing, and customer experience
- Created detailed technical documentation
📌 Disclaimer
This project is intended for educational and portfolio purposes.
The dashboard presents descriptive analysis based on the available dataset. Business interpretations should be validated with additional operational context before being used for real-world decision-making.

Inventory
Marketing
DateTable
