# 📊 Sales Performance Dashboard — Power BI Analytics Project

![Sales Dashboard Portfolio](https://github.com/fbarreton/Projects/blob/main/Sales_KPI_Dashboard_Data_Storytelling)

---

## 📌 Project Overview

This project presents a **Sales Performance Dashboard developed in Power BI** for a **civil engineering company** that operates across multiple **divisions, subdivisions, and employees**.

The objective of this project is to build a **monthly analytics dashboard** that enables leadership to monitor performance and make **data-driven decisions**.

The dashboard consolidates operational datasets into a **single analytical platform**, allowing management to track:

- Revenue growth
- Sales efficiency
- Lead conversion performance
- Employee productivity
- Division performance
- Sales cycle duration

---

## 🏗 Business Context

The company operates in the **civil engineering and infrastructure sector**, delivering projects across different operational units.

The company hierarchy follows this structure:

```text
Division
   └── Subdivision
          └── Employees
```

Each employee manages leads and closes deals related to engineering services.

Management required a **centralized reporting platform** to track performance across the organization.

---

## 🎯 Business Problem

The main business question addressed in this project:

**How can the company monitor monthly sales performance across divisions, subdivisions, and employees to identify growth opportunities and operational inefficiencies?**

Key analytical questions include:

- Is revenue increasing month over month?
- Which divisions generate the most revenue?
- Which employees close the most deals?
- How efficient is the sales funnel?
- How long does it take to close a deal?

Prior to this solution, reporting relied heavily on **manual spreadsheets**, limiting visibility and slowing decision-making.

---

## 📊 Dashboard Overview

The Power BI dashboard provides a consolidated view of the company's performance.

![Dashboard Overview](images/dashboard_readme_overview.png)

The dashboard allows users to analyze:

- Total revenue
- Monthly sales growth
- Conversion rates
- Average deal size
- Sales cycle length
- Division and employee performance

---

## 📈 Key Performance Indicators (KPIs)

The dashboard tracks five core KPIs.

### 1️⃣ Total Revenue

Total value of all closed deals.

```DAX
Total Revenue =
SUM(Sales[Amount])
```

### 2️⃣ Sales Growth %

Measures revenue change from the previous month.

```DAX
Sales Growth % =
VAR CurrentRevenue = [Total Revenue]

VAR PreviousRevenue =
CALCULATE(
    [Total Revenue],
    PREVIOUSMONTH('Calendar'[Date])
)

RETURN
DIVIDE(CurrentRevenue - PreviousRevenue, PreviousRevenue)
```

### 3️⃣ Conversion Rate

Percentage of leads that convert into deals.

```DAX
Conversion Rate =
DIVIDE([Deals Closed], [Total Leads], 0)
```

### 4️⃣ Average Deal Size

Average revenue generated per deal.

```DAX
Average Deal Size =
DIVIDE([Total Revenue], [Deals Closed], 0)
```

### 5️⃣ Sales Cycle Length

Average number of days required to close a deal.

```DAX
Sales Cycle Length =
AVERAGE(Sales[DaysToClose])
```

---

## 🗂 Data Model

The dashboard uses a **Star Schema data model** optimized for Power BI.

### Fact Table

**Sales**

| Column | Description |
|------|------|
| SaleID | Unique sale identifier |
| Date | Sale date |
| LeadID | Lead associated with sale |
| EmployeeID | Responsible employee |
| ProductID | Product/service sold |
| Amount | Revenue |
| DaysToClose | Time required to close |

### Dimension Tables

**Leads**

| Column | Description |
|------|------|
| LeadID | Unique lead |
| LeadSource | Source of lead |
| Status | Lead status |

**Employees**

| Column | Description |
|------|------|
| EmployeeID | Employee identifier |
| EmployeeName | Employee name |
| SubdivisionID | Organizational unit |

**Products**

| Column | Description |
|------|------|
| ProductID | Product identifier |
| ProductName | Engineering service |
| Category | Product category |

**Subdivisions**

| Column | Description |
|------|------|
| SubdivisionID | Unit identifier |
| DivisionID | Parent division |
| SubdivisionName | Subdivision name |

**Divisions**

| Column | Description |
|------|------|
| DivisionID | Division identifier |
| DivisionName | Division name |

**Calendar**

| Column | Description |
|------|------|
| Date | Date |
| Month | Month |
| Quarter | Quarter |
| Year | Year |

### Star Schema Diagram

The diagram below illustrates the logical star schema used to connect the fact table with the main dimensions for monthly sales analysis.

![Star Schema Data Model](images/star_schema_data_model.png)

---

## 🔄 Sales Funnel Pipeline

The sales funnel visualization helps stakeholders understand the movement from generated leads to closed deals and where conversion losses happen in the process.

Typical stages include:

- Leads
- Qualified Leads
- Proposals
- Negotiation
- Deal Won

![Sales Funnel Pipeline](images/sales_funnel_pipeline.png)

---

## 👥 Employee Performance Dashboard

This dashboard page focuses on individual and team performance, helping management compare revenue generation, conversion efficiency, and deal activity by employee, subdivision, and division.

Typical visuals include:

- Top employee ranking
- Revenue by employee
- Deals closed by employee
- Conversion rate by team
- Trend analysis by month

![Employee Performance Dashboard](images/employee_performance_dashboard_preview.png)

---

## ⚙️ Key DAX Measures

### Total Revenue

```DAX
Total Revenue = SUM(Sales[Amount])
```

### Total Sales

```DAX
Total Sales = COUNTROWS(Sales)
```

### Total Leads

```DAX
Total Leads = COUNTROWS(Leads)
```

### Deals Closed

```DAX
Deals Closed =
CALCULATE(
    [Total Sales],
    Sales[Amount] > 0
)
```

### Conversion Rate

```DAX
Conversion Rate =
DIVIDE([Deals Closed], [Total Leads], 0)
```

### Average Deal Size

```DAX
Average Deal Size =
DIVIDE([Total Revenue], [Deals Closed], 0)
```

### Sales Cycle Length

```DAX
Sales Cycle Length =
AVERAGE(Sales[DaysToClose])
```

---

## 🔄 Data Pipeline

The project follows a typical Business Intelligence pipeline.

```text
CSV Data Sources
       │
       ▼
Power Query (Data Cleaning)
       │
       ▼
Power BI Data Model
       │
       ▼
DAX Measures
       │
       ▼
Interactive Dashboard
```

---

## 📅 Reporting Frequency

The dashboard is designed for **monthly performance reporting**.

Each month, the system updates to allow management to:

- Track revenue growth
- Evaluate employee performance
- Compare division productivity
- Monitor pipeline efficiency

---

## 📊 Business Insights Enabled

The dashboard helps leadership identify:

**Revenue Concentration**  
A small number of divisions generate most revenue.

**Sales Cycle Bottlenecks**  
Some subdivisions have significantly longer deal cycles.

**Employee Productivity**  
Employee contribution to revenue varies widely.

**Lead Quality**  
Some lead sources generate higher conversion rates.

---

## 🧠 Skills Demonstrated

This project demonstrates expertise in:

- Power BI dashboard development
- Data modeling (Star Schema)
- DAX measure creation
- Business analytics
- Data visualization
- KPI design
- Dashboard storytelling

---

## 🚀 Future Improvements

Possible improvements include:

- Sales forecasting models
- Lead scoring algorithms
- CRM system integration
- Automated ETL pipelines
- Predictive analytics

---

## 🛠 Tools Used

```text
Power BI
DAX
Power Query
Draw.io
Excel / CSV datasets
```

---

## 📂 Repository Structure

```text
sales-performance-dashboard/

│
├── README.md
│
├── powerbi/
│   └── sales_dashboard.pbix
│
├── dataset/
│   ├── sales.csv
│   ├── leads.csv
│   ├── employees.csv
│
└── images/
    ├── dashboard_portfolio_overview.png
    ├── dashboard_readme_overview.png
    ├── star_schema_data_model.png
    ├── sales_funnel_pipeline.png
    └── employee_performance_dashboard_preview.png
```

---

## ⭐ Portfolio Note

This project demonstrates how **Business Intelligence tools such as Power BI can transform operational data into actionable insights** for organizations in the **civil engineering industry**.

The dashboard enables leadership to make **strategic decisions based on reliable performance metrics** across divisions, subdivisions, and employees.
