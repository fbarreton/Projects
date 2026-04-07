# Power BI Build Guide

A native `.pbix` file could not be generated directly in this environment because Power BI Desktop's binary project format requires Microsoft Power BI tooling.

Use these files to build the report in Power BI Desktop:

## Datasets
- `dataset/sales.csv`
- `dataset/leads.csv`
- `dataset/employees.csv`

## Images
- `images/dashboard_overview.png`
- `images/star_schema_data_model.png`
- `images/sales_funnel_pipeline.png`
- `images/employee_performance_dashboard_preview.png`

## Suggested model
- `sales[LeadID]` -> `leads[LeadID]`
- `sales[EmployeeID]` -> `employees[EmployeeID]`

## Suggested measures
```DAX
Total Revenue = SUM(sales[Amount])
Deals Closed = COUNTROWS(sales)
Total Leads = COUNTROWS(leads)
Conversion Rate = DIVIDE([Deals Closed], [Total Leads], 0)
Average Deal Size = DIVIDE([Total Revenue], [Deals Closed], 0)
Sales Cycle Length = AVERAGE(sales[DaysToClose])

Sales Growth % =
VAR CurrentRevenue = [Total Revenue]
VAR PreviousRevenue =
    CALCULATE(
        [Total Revenue],
        PREVIOUSMONTH('Calendar'[Date])
    )
RETURN DIVIDE(CurrentRevenue - PreviousRevenue, PreviousRevenue)
```
