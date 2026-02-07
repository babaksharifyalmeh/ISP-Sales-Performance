
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

---

## Phase 2 – Data Modeling & Relationships

In **Phase 2** of the project, the primary focus was on designing the data model, defining a robust analytical structure, and establishing standard, best-practice relationships between tables.
The objective of this phase was to create a scalable, high-performance foundation that enables accurate and reliable analysis within **Power BI**.

---

## 2.1 Data Modeling Approach

For this project, a **Star Schema** data modeling approach was adopted.

In this structure, **Fact_Sales** serves as the central fact table, containing transactional sales data and core numerical measures such as:

* Net amount
* Cost
* Discount
* Tax

Surrounding the fact table, the following dimension tables were designed:

* **Dim_Subscribers**: Contains descriptive attributes of subscribers, enabling customer-based analysis.
* **Dim_Date**: A dedicated date dimension supporting both Gregorian and Persian calendars, enabling standardized time-based analysis and time intelligence.
* **Dim_Measure**: A logical dimension used to manage KPIs and enable dynamic KPI selection within the reporting layer.

The Star Schema was selected due to its simplicity, high readability, optimal performance in Power BI, and strong alignment with the nature of sales and transactional data.
This approach minimizes relationship complexity, improves query performance, and facilitates future model expansion.

---

## 2.2 Data Model Diagram (Star Schema)

> **![Star Schema data model diagram](Images\Model_Relashanship\Star_Model.png)**
> *(This image should illustrate Fact_Sales at the center with Dim_Subscribers, Dim_Date, and Dim_Measure arranged around it in a star-shaped structure.)*

---

## 2.3 Data Relationships Design

Following the model design, table relationships were defined in a controlled and standardized manner, adhering to analytical modeling best practices.

* The relationship between **Dim_Subscribers** and **Fact_Sales** is defined through the *Subscriber ID* field and follows a **One-to-Many** cardinality.
  Each subscriber can be associated with multiple sales records, with filter direction applied from the dimension table to the fact table. This enables sales analysis based on subscriber attributes.

* The relationship between **Dim_Date** and **Fact_Sales** is established via the *Transaction Date* field and is also **One-to-Many**.
  This structure supports period-based analysis, trend comparisons, and the use of standard time intelligence functions.

* **Dim_Measure** is implemented as a **disconnected table**, meaning it has no physical relationship with the fact table.
  It is used exclusively within the DAX layer to enable dynamic KPI selection and improve dashboard flexibility without increasing relationship complexity.

* The **Reload** table is a standalone display table used solely to present the last data refresh timestamp and does not participate in analytical relationships.

---

## 2.4 Outcome of Phase 2

The output of Phase 2 is a clear, stable, optimized, and extensible data model that:

* Prevents calculation errors caused by ambiguous or incorrect relationships
* Improves overall report performance
* Provides a strong foundation for KPI definition and managerial dashboard development in subsequent phases

This data model serves as the **core analytical backbone** for all analyses and visualizations developed in the next phases of the project.

