
# Phase 1 Report

## Data Understanding, Business Framing & Analytical Design

---

## Overview

This document presents **Phase 1** of the analytics project, focusing on understanding the available data, framing the business problem, identifying key analytical requirements, and defining the overall reporting approach.
This phase establishes the analytical foundation required for data modeling, dashboard development, and advanced analysis in subsequent phases.

---

## 1. Data Understanding & Structure Analysis

### 1.1 Initial Data Exploration

At the beginning of the project, the available data consisted of two primary tables:

* **Fact_Sales**
  This table contains transactional sales data, including:

  * Net amount
  * Cost
  * Discount
  * Tax
  * Transaction date
  * Service type
  * Package
  * Purchase channel
  * Invoice status

  Each record represents a single sales event.

* **Dim_Subscribers**
  This table includes descriptive attributes of subscribers, such as:

  * Subscriber ID
  * Province and city
  * Customer type
  * Service status
  * Current package
  * ARPU
  * Customer lifecycle-related dates

Based on this structure, **Fact_Sales** was identified as the fact table and **Dim_Subscribers** as the dimension table, with a relational link established through the **Subscriber ID** key.

---

## 2. Business & Industry Context

### 1.2 Industry Identification and Business Domain

Based on column names and data values (e.g., service types such as ADSL, Wireless, TD-LTE, internet packages, installation and renewal statuses), the dataset was identified as belonging to the **Internet Service Provider (ISP) and telecommunications industry**.

The data structure indicates that the core business focuses on:

* Subscription-based sales
* Service renewals
* Management of individual and corporate customers
* Revenue analysis by package and geographic region

This understanding was reinforced through initial data inspection and early alignment sessions with the business stakeholder.

---

## 3. Data Quality Assessment

### 1.3 Data Quality Review and Identified Issues

A statistical review of columns and a sample inspection of approximately 100–200 rows revealed several data quality concerns, including:

* Negative values in discount and tax fields
* High variance in numeric measures such as net amount and ARPU
* Invalid or extremely old dates (e.g., birth dates from 1841)
* Non-meaningful textual values such as `"-----"`
* Inconsistent naming conventions for packages

These issues were documented as **data risks** to be addressed during the data cleansing and modeling phase.

---

## 4. Column Role Definition

### 1.4 Analytical Role of Columns

Without performing analysis at this stage, each column was classified based on its analytical role:

* **Measures**: Net amount, cost, discount, tax
* **Dimensions**: Service type, province, city, package, purchase channel
* **Keys / Identifiers**: Subscriber ID, invoice ID

Additionally, decisions were made regarding:

* Required data type conversions (e.g., transaction date from text to date)
* Standardization of categorical values

The full rationale for these decisions is documented in Section 1.4 of the report.

---

## 5. Business KPIs Definition

### 1.5 Identification of Key Business KPIs

Key Performance Indicators (KPIs) were derived from **managerial questions**, not directly from the data itself, based on stakeholder discussions and decision-making needs.

The primary KPIs include:

* Total revenue
* Gross profit
* ARPU
* Renewal-to-new-purchase ratio
* Revenue by geographic region
* Package performance

All KPIs are:

* Measurable
* Actionable
* Clearly explainable in one sentence
  and directly support management decisions such as regional focus or discount policy optimization.

---

## 6. Reporting Strategy & Audience

### 1.6 Target Audience and Report Types

The project output is designed to be **multi-layered**, addressing different stakeholder needs:

* Executive summary dashboard for the CEO
* Interactive analytical dashboard for marketing and sales teams
* Operational reports for the support team
* Full analytical access for the BI team

**Power BI** was selected as the primary tool to enable filtering, drill-down, and interactive data exploration.

---

## 7. Analytical Objective & Scope

### 1.7 Analysis Goal and Type

The primary objective of this analysis is to create transparency around:

* Sales performance
* Customer behavior
* Package profitability

to support data-driven managerial decision-making.

Phase 1 focuses on **descriptive and diagnostic analysis**. Future phases may extend toward predictive analytics.
Success criteria for this phase include data readiness and clarity of analytical questions required for dashboard design.

---

## 8. Data Risks & Limitations

### 1.8 Identified Risks and Constraints

While the dataset volume is sufficient for analysis (over 38,000 sales records and 40,000 subscribers), several limitations were identified:

* Missing or imprecise financial dates
* Textual inconsistencies
* Illogical values
* Potential data confidentiality constraints

Additionally, the data is not fully standardized and requires cleansing in **Power Query**.
All risks have been logged, and mitigation actions are planned for the next phase.

---

## 9. Phase 1 Summary & Readiness Assessment

### 1.9 Phase 1 Conclusion

By the end of Phase 1, the following elements were clearly defined:

* Data structure and table roles
* Data quality status
* Key business KPIs
* Reporting audiences
* Visualization and analytical approach

This phase serves as the **decision-making foundation** for:

* Data model design
* Power BI dashboard implementation
* DAX measure development

For detailed references on column analysis, KPIs, and data risks, see Sections **1.3**, **1.4**, and **1.5** of this report.

