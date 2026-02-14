# 📊 ISP Sales Performance Dashboard – Power BI Project

---

## 🖼 Dashboard Preview

### Executive Sales Performance

![Executive Dashboard](Images\Images-Dashboard\Report_1.png)

### Employes Performance

![Executive Dashboard](Images\Images-Dashboard\Dashboard_Employes.png)

### Geographic Performance

![Geographic Dashboard](Images\Images-Dashboard\Dashboard_Geographic.png)

### Service Performance

![Service Dashboard](Images\Images-Dashboard\Dashboard_Service.png)

### Operational / All Reports

![Operational Dashboard](Images\Images-Dashboard\Report_2.png)

---

# Project Overview

This project presents a complete end-to-end Business Intelligence solution developed in **Power BI** for an Internet Service Provider (ISP).

The objective of this dashboard is to provide:

* Executive-level sales transparency
* Service and package performance analysis
* Geographic concentration risk assessment
* Sales team operational performance monitoring
* Customer behavior insights

The solution follows a structured multi-phase BI development methodology including:

1. Business Understanding
2. Data Modeling
3. UX & Dashboard Design
4. KPI Engineering
5. Interactive Reporting & Drill-through

---

# Phase 1 – Data Understanding & Business Framing

## Data Sources

Two primary datasets were provided:

### Fact_Sales

Transactional table containing:

* Net Amount
* Cost
* Discount
* Tax
* Transaction Date
* Service Type
* Package
* Invoice Status
* Sales User

Each row represents one sales event.

### Dim_Subscribers

Descriptive customer table containing:

* Subscriber ID
* Province / City
* Customer Type (Individual / Corporate)
* Current Package
* ARPU
* Lifecycle Information

Fact_Sales was identified as the central **fact table**, and Dim_Subscribers as a **dimension table**, linked through Subscriber ID.

---

## Industry Context

Based on service types (ADSL, TD-LTE, Wireless), renewal patterns and subscription logic, the dataset belongs to the **ISP / Telecommunications industry**.

The business operates on:

* Subscription-based revenue
* Service renewals
* Regional sales distribution
* ARPU-driven profitability

---

## Data Quality Assessment

Identified issues:

* Negative discount values
* Invalid historical dates
* High variance in ARPU
* Text inconsistencies
* Non-standard categorical values

These were documented and addressed in the ETL phase.

---

## KPI Framework

KPIs were derived from business questions rather than raw data fields.

Core KPIs include:

* Total Revenue
* Total Profit
* ARPU
* Renewal Ratio
* Revenue by Province
* Revenue by Service
* Sales Concentration Ratio
* Profit Margin by Region

All KPIs are measurable, actionable and decision-oriented.

---

# Phase 2 – Data Modeling (Star Schema)

A **Star Schema** approach was implemented.

### Fact Table

* Fact_Sales

### Dimension Tables

* Dim_Subscribers
* Dim_Date (Persian & Gregorian)
* Dim_Measure (Disconnected KPI table)
* Reload (Refresh tracking)

### Relationships

* Subscriber → One-to-Many → Sales
* Date → One-to-Many → Sales
* Dim_Measure → Disconnected (DAX layer)

This structure ensures:

* High performance
* Clean filter direction
* Accurate calculations
* Future scalability

---

# Phase 3 – UX Design & Dashboard Architecture

The dashboard follows a structured storytelling approach.

## Page 1 – Sales Performance (Executive Overview)

Decision Focus:

* Is revenue growing?
* Is profit aligned with revenue?
* Is ARPU stable?

Visuals:

* KPI Cards (Revenue, Profit, Subscribers, ARPU)
* Revenue vs Profit Trend (Line Chart)
* Revenue Collection Status (Donut: Paid / Overdue / Unpaid)
* Tooltip with MoM change

---

## Page 2 – Operational / Sales Team Performance

Decision Focus:

* Is revenue concentrated among few salespeople?
* Does high volume equal high quality?
* Is operational risk present?

Visuals:

* Top Salespeople by Revenue (Stacked by Customer Type)
* Scatter: Volume vs Profit Quality
* Clustered Bar: Working vs Non-Working Days
* Active Employees (Working / Non-working)
* Drill-through to Salesperson Profile Page

Drill-through page includes:

* Individual KPI summary
* Monthly performance trend
* Profit per order
* ARPU contribution

---

## Page 3 – Geographic Performance

Decision Focus:

* Where is revenue concentrated?
* Are high-sales provinces also high-profit?
* Is there geographic concentration risk?

Visuals:

* Iran Map (Revenue-based gradient)
* Revenue by Province (Bar)
* Combo Chart: Revenue + ARPU
* High-ARPU Cities Analysis

---

## Page 4 – Service Performance

Decision Focus:

* Which services generate sustainable profit?
* Which packages drive revenue?
* How does ARPU impact service performance?

Visuals:

* Revenue by Service
* Service Status Distribution (100% Stacked)
* Top Packages
* Revenue by Service (Stacked Column with Small Multiples by ARPU Category)

---

## Page 5 – Customer Behavior Analysis

Decision Focus:

* What percentage of customers are active?
* What is retention performance?
* Which customer segment generates highest value?

Visuals:

* Active vs Inactive Ratio
* Renewal Ratio
* Revenue by Customer Type
* ARPU Distribution

---

# Advanced Features Implemented

* Drill-through navigation (Salesperson level)
* Tooltip-driven micro analysis
* Small Multiples for ARPU segmentation
* Dynamic KPI selection (Dim_Measure)
* Working vs Non-Working day grouping
* Concentration risk detection logic
* Clean visual hierarchy
* Custom theme (Neon Yellow / Dark UI)

---

# Technical Stack

* Power BI Desktop
* Power Query (ETL)
* DAX Measures
* Star Schema Modeling
* Custom JSON Theme
* Git version control

---

# Project Outcome

The final dashboard enables:

* Executive-level decision making
* Risk detection in sales operations
* Service-level profitability evaluation
* Geographic performance assessment
* Data-driven strategic planning

This solution transforms raw ISP sales data into a structured, scalable, and decision-focused analytical platform.

