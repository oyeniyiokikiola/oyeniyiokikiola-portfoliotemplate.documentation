# Retail transaction sales analysis to uncover revenue trends, top-performing products, and regional/customer patterns to inform business decisions.

---

## ⚙️ Project Type Flags

- [ ] Dashboard / Data Visualization
- [ ] Data Cleaning / Wrangling
- [ ] End-to-End


---

## Table of Contents
1. [Project Overview](#1-project-overview)
2. [Objectives](#2-objectives)
3. [Project Scope & Tools](#3-project-scope--tools)
4. [Data Workflow](#4-data-workflow)
5. [Data Model & Schema](#5-data-model--schema)
6. [Analysis & Metrics](#6-analysis--metrics)
7. [Key Insights](#7-key-insights)
8. [Recommendations](#8-recommendations)
9. [Assumptions & Limitations](#9-assumptions--limitations)
10. [Future Enhancements](#10-future-enhancements)
11. [Deliverables](#11-deliverables)
12. [Author](#12-author)

---

## 1. Project Overview

**Context:** A retail company needed to understand sales performance across products, customers, and regions for 2023–2024.

**Problem Statement:** Sales trends were unclear, and the company wanted to identify top-performing products, underperforming products, and revenue drivers by month, category, region, and customer segment.

**Approach:** Cleaned multi-sheet data using Power Query, created a date table, and established relationships in Power Pivot. Built pivot tables for multiple dimensions and designed a dashboard with interactive slicers.

**Outcome:** The final dashboard revealed strong seasonal patterns, revenue concentration among top-performing products, and disproportionate contribution from specific customer segments — insights that were not visible in the raw data alone.

---

## 2. Objectives

- **Primary Objective:** Build a sales dashboard to highlight top-performing products, underperforming products, and revenue trends by month, region, and customer segment.
- **Secondary Objective 1:** Quantify revenue contributions by gender, age group, and customer to inform marketing and inventory strategies.
- **Secondary Objective 2:** Compare 2023 vs 2024 revenue to determine year-over-year growth patterns.

---

## 3. Project Scope & Tools

### Scope

| Dimension | Details |
|-----------|---------|
| **In Scope** | Sales, Products, and Customers tables; analysis of revenue, top/bottom products, monthly trends, region, customer, and demographic contributions |
| **Out of Scope** | Analysis at individual Product ID, Customer ID, and Employee ID level was excluded. The project focused on aggregated performance (category, region, demographic segments) rather than entity-level tracking, as the objective was to identify overall revenue patterns and concentration — not individual performance metrics |
| **Time Period** | January 2023 – December 2024 |
| **Granularity** | Transaction-level data aggregated by month, product, region, and customer demographics |

### Tools & Technologies

| Category | Tool(s) Used |
|----------|-------------|
| Data Storage | Excel |
| Data Processing | Power Query, Power Pivot |
| Analysis | Excel pivot tables, Excel formulas|
| Visualization | Excel dashboard (pivot charts, slicers |
| Version Control | GitHub |
| Documentation | Markdown |

---



## 4. Data Workflow

```
Sales.xlsx, Products.xlsx, Customers.xlsx
      ↓
Power Query: cleaned duplicates, standardized dates,created date table
      ↓
Power Pivot: established relationships between Sales, Products, Customers, and Date table
      ↓
Pivot Tables: monthly revenue, YoY revenue, top 10 products, revenue by region, age, gender, customer
      ↓
Dashboard: interactive charts and slicers for category, region, and year
```

1. **Source:** Three-sheet transactional dataset containing Sales, Products, and Customers.
2. **Ingestion:** Loaded into Power Query for cleaning.
3. **Cleaning:** Removed duplicates, standardized date formats, handled missing product/customer IDs.
4. **Transformation:** Created date table with Month, Year, Weekday/Weekend. Created calculated columns for revenue, YoY change.
5. **Analysis:** Built pivot tables by month, year, region, product, customer, gender, and age. Applied number formatting (K/M) to the revenues.
6. **Output:** Interactive dashboard with total units sold, revenue, revenue by day type, top/underperforming products, revenue by customer, category, and region.

---

## 5. Data Model & Schema

### Dataset / Table: `Sales`

| Field Name | Data Type | Description | Example Value |
|------------|-----------|-------------|---------------|
| `order_id` | int|Unique transaction ID| 1 |
| `order_date` | date | Date of sale | 2023-03-15 |
| `product_id` | int | Product identifier | 20 |
| `ocustomer_id` | int | Customer identifier| 45|
| `employee_id` | int | Employee who handled the sales | 12 |
| `quantity` | int | Units sold | 155 |
| `unit_price` | float | Price per unit | 634.0 |

> **Row count (approx.):** 5001
> **Date range:** 2023-01-01 – 2024-12-31

### Dataset / Table: `Products`

| Field Name | Data Type | Description | Example Value |
|------------|-----------|-------------|---------------|
| `product_id` | int | Product identifier | 20 |
| `product_name` | string | Name of the product| Spaghetti|
| `category` | string | Product category | Grocery |

> **Row count (approx.):** 51

### Dataset / Table: `Customer`

| Field Name | Data Type | Description | Example Value |
|------------|-----------|-------------|---------------|
| `customer_id` | int | Cusomer identifier| 1 |
| `customer_name` | string | Name of customer | Jacob Jones |
| `region` | string | Customer region | South |
| `gender` | string | Customer gender| Male|
| `age` | int | Customer age | 55 |

> **Row count (approx.):** 301
> **Key join / relationship:** `Sales.product_id` → `Products.product_id`; `Sales.customer_id` → `Customers.customer_id`; `Sales.order_date` → `DateTable.date`



---

## 6. Analysis & Metrics

### Analytical Approach

Explored patterns in revenue by month, year, region, product, and customer. Used pivot tables and calculated fields in Power Pivot for YoY analysis. Focused on identifying top/underperforming products and revenue drivers.

### Key Metrics Defined

| Metric | Plain-Language Definition | Why It Matters |
|--------|--------------------------|----------------|
| `Total Revenue` | Sum of quantity by unit price | Measures total business income per period, category, and segment |
| `Total Units Sold` | Total number of products sold | Evaluates sales volume contribution per product |
| `YoY change` | Percentage difference between 2024 vs 2023 revenue | Tracks growth trends and seasonal performance |
| `Revenue by Customer and Region` | Sum of revenue by customer and region | Determines high-value customers and high-performing regions |




### Methods Used

- Descriptive statistics: revenue, units sold, YoY change
- Trend analysis across months and years
- Segmentation by product category, region, customer, age, and gender
- Top 10 and underperforming product identification
- Interactive visualization via Excel dashboard and slicer

---

## 7. Key Insights

**Insight 1: Monthly Revenue Trends**
January and November are peak months, while February and June are low. Suggests seasonal demand patterns influencing revenue.

**Insight 2: Revenue by Category**
Female customers contribute 65% of revenue. Age group 19–37 generates the highest revenue. Marketing and sales strategies should reflect these segments.

**Insight 3: Product Performance**
Top 10 products contribute disproportionately to revenue, while underperforming products generate minimal revenue. Focus inventory and promotions on high performers.

**Insight 4: Regional Performance**
West and East regions outperform North and South. Regional strategies may need adjustment to boost lagging regions.

---

## 8. Recommendations


| Priority | Recommendation | Based On | Suggested Owner |
|----------|---------------|----------|-----------------|
| High | Increase marketing focus on top 10 products | Insight 3: Product Performance | Sales/Marketing Team |
| Medium | Optimize inventory allocation for peak months | Insight 1: Monthly Trends | Operations Team |
| Medium | Target campaigns for high-value demographics (female, age 19–37)| Insight 2: Customer Segments | Marketing Team |
| Low | Investigate low-performing regions to identify barriers | Insight 4: Regional Performance| Regional Managers |

---

## 9. Assumptions & Limitations

### Assumptions
- Transaction-level sales records were assumed to be complete and accurately recorded for the entire January 2023 – December 2024 period, as no independent validation against a source accounting system was performed.
- The analysis assumed that aggregating data to monthly, regional, and category levels was sufficient to identify revenue patterns, given that the project objective focused on performance concentration rather than individual-level behavior.

### Limitations
- The dataset does not include cost data, profit margins, or expense information. As a result, the analysis focuses solely on revenue performance and cannot assess profitability or margin efficiency.
- The analysis is descriptive rather than predictive. It identifies patterns and concentration but does not model future revenue performance.
- The dataset does not include inventory levels or stock availability. Revenue fluctuations may therefore reflect supply constraints rather than demand changes.
- No marketing, promotional, or campaign data was available. Therefore, changes in revenue over time cannot be attributed to external business activities.

---

## 10. Future Enhancements

- [ ]  Add profit and margin analysis to prioritize high-margin products.
- [ ]  Automate monthly data updates using Power Query or Python scripts
- [ ]  Include time-of-day analysis to optimize staffing and promotions.

---

## 11. Deliverables

| Deliverable | Description | Location |
|-------------|-------------|----------|
| Sales Analysis Dashboard | Interactive Excel dashboard with KPIs, trends, and slicers | https://1drv.ms/x/c/4a9770274467d72d/IQDkJ6khsww_TqsnxuVaXLp8ARb4NA27IxvzLuhWvVLcX_E?e=z7r0Kz |

---

## 12. Author

**Okikiola Oyeniyi**
Data Analyst

- 🔗 https://www.linkedin.com/in/okikiola-oyeniyi-?
- 💼 https://oyeniyiokikiola.github.io/
- 📧 oyeniyiokikiola@gmail.com

---

*Last updated: Feb 2026*
