# NimbusFlow | SaaS Revenue Intelligence & Business Analytics

**An end-to-end business analytics project exploring revenue growth, customer retention, subscription performance, customer acquisition, and payment collection for a hypothetical SaaS company.**

**Live Dashboard:** [View NimbusFlow Dashboard](https://nimbusflow-dashboard.netlify.app/)

<img width="1000" height="400" alt="Screenshot 2026-11-14 230013" src="https://github.com/user-attachments/assets/c8ea561a-5968-4422-afe8-70cd3b34c22a" />

<img width="1000" height="400" alt="Screenshot 2026-11-14 230131" src="https://github.com/user-attachments/assets/6d05bf8a-ce91-462b-b395-eb1bdfa40eab" />

<img width="1000" height="400" alt="Screenshot 2026-11-14 230436" src="https://github.com/user-attachments/assets/ba417983-8ad9-4f19-99c6-69018caee76b" />


# Table of Contents

1. [Project Overview](#1-project-overview)
2. [Project Workflow](#2-project-workflow)
3. [Dataset](#3-dataset)
4. [Data Cleaning and Preparation](#4-data-cleaning-and-preparation)
5. [SQL Business Analysis](#5-sql-business-analysis)
6. [Key Performance Indicators (KPIs)](#6-key-performance-indicators-kpis)
7. [Dashboard Development](#7-dashboard-development)
8. [Dashboard Hosting](#8-dashboard-hosting)
9. [Technology Stack](#9-technology-stack)

<img width="1000" height="400" alt="Screenshot 2026-11-14 230038" src="https://github.com/user-attachments/assets/2826980c-69da-4508-9c28-8ed53a15071b" />

<img width="1000" height="400" alt="Screenshot 2026-11-14 230402" src="https://github.com/user-attachments/assets/3e206fc5-6d22-4865-94ab-4412c9fc9637" />

<img width="1000" height="400" alt="Screenshot 2026-11-14 230457" src="https://github.com/user-attachments/assets/97836355-9e37-49ee-b94d-1d98cf6d854e" />


## 1. Project Overview

NimbusFlow is a hypothetical B2B SaaS company that provides subscription-based software to businesses through different pricing plans.

This project focuses on understanding how a subscription-based business performs over time. It examines the complete revenue lifecycle, starting from customer acquisition and subscription creation to revenue generation, customer retention, and invoice collection.

The project uses a synthetic dataset containing **456,857 records across six interconnected tables**, covering a reporting period from January 2024 to December 2025.

The objective is to transform raw business data into useful information that can help management understand business performance and make better decisions.

The project is divided into five major stages:

- Dataset creation and exploration
- Data cleaning and preparation using Python
- Business analysis using SQL and PostgreSQL
- Interactive dashboard development
- Dashboard deployment using Netlify

## 2. Project Workflow

The project follows a structured analytics workflow, with each stage building on the previous one.

<pre>
Raw Dataset (CSV Files)
        |
        v
Data Exploration and Cleaning
        |
        v
Python / Jupyter Notebook
        |
        v
Cleaned and Prepared Data
        |
        v
SQL Analysis (PostgreSQL)
        |
        v
Business Metrics and Findings
        |
        v
Dashboard Development
        |
        v
Deployment on Netlify
        |
        v
Interactive Revenue Intelligence Dashboard
</pre>

| Stage | Work Performed |
|---|---|
| Dataset | Created a large, interconnected synthetic SaaS dataset |
| Data Cleaning | Explored, cleaned, standardized, and validated the raw data |
| SQL Analysis | Investigated business questions and calculated performance metrics |
| Dashboard | Presented important KPIs and business trends through interactive visualizations |
| Hosting | Published the dashboard online using Netlify |

---

## 3. Dataset

### Dataset Overview

The project uses a synthetic dataset designed to represent the operations of a B2B SaaS subscription business.

It contains **456,857 records distributed across six tables**.

| Dataset | Records | Description |
|---|---:|---|
| customers.csv | 10,000 | Customer details, signup information, and acquisition channels |
| plans.csv | 8 | Available subscription plans and their pricing |
| subscriptions.csv | 14,000 | Customer subscriptions, billing cycles, and subscription status |
| subscription_events.csv | 32,849 | Subscription upgrades, downgrades, cancellations, and reactivations |
| invoices.csv | 390,000 | Customer invoices, billed amounts, payments, and outstanding balances |
| marketing_spend.csv | 10,000 | Marketing expenditure, campaigns, and customer acquisition |
| **Total** | **456,857** | **Six interconnected datasets** |

### Understanding the Tables

Each table represents a different part of the company's business operations.

**1. Customers**

Contains information about the customers using NimbusFlow.

Important fields include:
- Customer ID
- Signup Date
- Acquisition Channel
- Country
- Company Size
- Industry
- Campaign ID

**2. Plans**

Contains information about the subscription plans offered by the company.

The dataset includes eight plans, ranging from Free to Enterprise Plus.

Important fields include:
- Plan Name
- Plan Tier
- Monthly Price
- Annual Price
- Included Seats
- Billing Currency

**3. Subscriptions**

Tracks the subscription history of customers.

It helps analyze which plans customers use, how long they remain subscribed, and whether their subscriptions are active or cancelled.

Important fields include:
- Subscription ID
- Customer ID
- Plan ID
- Start and End Dates
- Billing Cycle
- Subscription Status
- Discount Percentage
- Cancellation Reason

**4. Subscription Events**

Records important changes in a customer's subscription.

Examples include:
- Upgrading to a higher-priced plan
- Downgrading to a lower-priced plan
- Cancelling a subscription
- Reactivating a cancelled subscription

These records are particularly useful for understanding changes in Monthly Recurring Revenue (MRR).

**5. Invoices**

Contains billing and payment information for customer subscriptions.

Important fields include:
- Invoice Date
- Billing Period
- Amount Due
- Amount Paid
- Payment Status
- Payment Method
- Payment Date
- Due Date
- Days Overdue

This table supports revenue collection, payment performance, and outstanding balance analysis.

**6. Marketing Spend**

Contains information about marketing expenditure and campaign performance.

It helps compare the cost of acquiring customers across different channels.

Important fields include:
- Acquisition Channel
- Campaign Name
- Marketing Spend
- Attributed New Customers
- Attributed Paid Customers
- Country
- Campaign Type

### Dataset Relationships

The six tables are connected through common identifiers.

| Relationship | Purpose |
|---|---|
| Customers → Subscriptions | Connects customers with their subscriptions |
| Plans → Subscriptions | Identifies the plan associated with each subscription |
| Subscriptions → Subscription Events | Tracks changes throughout a subscription's lifecycle |
| Subscriptions → Invoices | Connects subscriptions with their billing records |
| Marketing Spend → Customers | Supports acquisition and campaign analysis through channel and campaign attribution |

These relationships allow information from different tables to be combined for business analysis.

### Data Quality Challenges

To make the project closer to real-world analytics work, the raw dataset contains intentionally introduced data-quality issues.

Approximately 2–4% of records are affected by these issues.

| Issue | Example |
|---|---|
| Missing Values | Missing acquisition channels or company information |
| Duplicate Records | Repeated invoice or event records |
| Inconsistent Formatting | Different spellings, capitalization, and extra spaces |
| Date Errors | Incorrect dates or invalid billing periods |
| Numerical Errors | Negative amounts or invalid discount percentages |
| Outliers | Unusually high invoice amounts or marketing expenditure |
| Referential Issues | Records containing invalid foreign-key references |
| Logical Inconsistencies | Subscription statuses that conflict with their event history |

The purpose of introducing these issues is to demonstrate how raw business data can be inspected, corrected, and validated before it is used for analysis.

---

## 4. Data Cleaning and Preparation

**Tools: Python, Pandas, NumPy, Jupyter Notebook**

The raw CSV files are first explored and prepared using Python in a Jupyter Notebook.

The objective is to make the data reliable and consistent before performing business analysis.

### Main Cleaning Activities

| Activity | What Was Done |
|---|---|
| Data Inspection | Examined dataset dimensions, columns, data types, and sample records |
| Missing Values | Identified missing information and handled it using appropriate rules |
| Duplicate Removal | Detected and addressed duplicate records |
| Data Standardization | Corrected inconsistent text formats, capitalization, and whitespace |
| Date Validation | Checked date formats, billing periods, and subscription timelines |
| Numerical Validation | Identified invalid amounts, discounts, and other numerical values |
| Outlier Detection | Investigated unusual values in financial and operational fields |
| Relationship Validation | Checked connections between customers, subscriptions, plans, and invoices |
| Business Rule Validation | Checked whether records followed expected subscription and billing logic |

### Data Quality Handling

Not every data-quality issue should be treated in the same way.

For example:

- Extra spaces and inconsistent capitalization can usually be corrected automatically.
- Duplicate records need to be checked before removal because repeated transactions can be legitimate.
- Missing values may require recovery from related records or an appropriate business rule.
- Invalid financial or subscription records may need to be flagged or excluded from specific calculations.

The original raw data is preserved, and intentional data-quality issues are documented in `data_quality_issue_log.csv`.

### Output

The cleaning stage produces prepared data suitable for SQL analysis and dashboard calculations.

---

## 5. SQL Business Analysis

**Tools: PostgreSQL, SQL**

After preparing the data, the next stage focuses on answering business questions using SQL.

The six datasets are structured as relational tables, allowing information to be combined across customers, subscriptions, plans, invoices, and marketing campaigns.

The analysis covers five major business areas.

### A. Revenue and Growth Analysis

| # | Business Question |
|---|---|
| 1 | How has MRR changed month over month, and which months had the strongest or weakest growth? |
| 2 | How much of the new recurring revenue comes from new customers versus existing customer upgrades? |
| 3 | Which months experienced negative net new MRR, and what caused the decline? |
| 4 | Which customer segments contribute the largest share of recurring revenue? |
| 5 | How does revenue per paying customer vary across subscription plans and company sizes? |

### B. Customer Retention and Churn

| # | Business Question |
|---|---|
| 6 | What are the monthly customer churn and gross revenue churn rates? |
| 7 | Which customer signup cohorts have the strongest retention at months 1, 3, 6, and 12? |
| 8 | At what subscription tenure do customers cancel most frequently? |
| 9 | Which acquisition channels have the highest customer churn? |
| 10 | Which customer segments experience the largest revenue losses from churn? |

### C. Subscription and Plan Analysis

| # | Business Question |
|---|---|
| 11 | Which subscription plans have the highest upgrade and downgrade rates? |
| 12 | What are the most common plan transitions, and which produce the largest MRR changes? |
| 13 | How much MRR is lost through downgrades compared with cancellations? |
| 14 | Are discounted customers more or less likely to upgrade, downgrade, or churn than full-price customers? |

### D. Customer Acquisition Analysis

| # | Business Question |
|---|---|
| 15 | Which acquisition channels have the lowest CAC and highest revenue per acquired customer? |
| 16 | Which channels have the shortest estimated CAC payback period? |
| 17 | What percentage of acquired customers become paying customers within 30, 60, and 90 days? |

### E. Invoice and Payment Analysis

| # | Business Question |
|---|---|
| 18 | How do invoice collection and failed-payment rates vary across plans and billing cycles? |
| 19 | How much billed revenue remains unpaid, and how old are outstanding invoices? |
| 20 | Which customer segments combine strong retention, high revenue per account, and low acquisition costs? |

### SQL Techniques Used

The analysis uses SQL techniques commonly applied in business intelligence and data analytics.

- Joins across multiple relational tables
- Common Table Expressions (CTEs)
- Aggregate functions
- Conditional aggregation
- CASE statements
- Window functions
- LAG and LEAD
- Date and time calculations
- Cohort analysis
- Ranking and running totals
- Customer-level and monthly analysis

The objective is not simply to write complex queries, but to use SQL to investigate business performance and produce meaningful results.

---

## 6. Key Performance Indicators (KPIs)

The dashboard uses business metrics to summarize the company's performance.

Below are the main KPIs and how they are calculated.

### Revenue KPIs

| KPI | Meaning | Calculation |
|---|---|---|
| MRR | Monthly Recurring Revenue from active paid subscriptions | Sum of month-end subscription MRR |
| ARR | Annualized recurring revenue | MRR × 12 |
| Net MRR Growth | Percentage change in recurring revenue | (Closing MRR − Opening MRR) / Opening MRR |
| New MRR | Recurring revenue from first-time and reactivated customers | Sum of new and reactivated MRR |
| Expansion MRR | Additional recurring revenue from existing customers | MRR gained through upgrades and expansion |
| Contraction MRR | Recurring revenue lost through downgrades | MRR reduction from existing customers |
| Churned MRR | Recurring revenue lost through cancellations | MRR lost from cancelled subscriptions |
| Net New MRR | Total net change in recurring revenue | New + Expansion − Contraction − Churned MRR |

### Retention KPIs

| KPI | Meaning | Calculation |
|---|---|---|
| Logo Churn | Percentage of paying customers lost | Lost Customers / Opening Paying Customers |
| NRR | Revenue retained from the opening customer base, including expansion | (Opening MRR + Expansion − Contraction − Churn) / Opening MRR |
| GRR | Revenue retained after contraction and churn, excluding expansion | (Opening MRR − Contraction − Churn) / Opening MRR |
| ARPA | Average recurring revenue per paying account | Closing MRR / Paying Customers |
| Customer Lifetime | Observed duration of a customer's paid relationship | Time from first payment to churn or observation end |

### Acquisition KPIs

| KPI | Meaning | Calculation |
|---|---|---|
| CAC | Cost of acquiring a new paying customer | Marketing Spend / Newly Paying Customers |
| CAC Payback | Estimated time required to recover acquisition cost | CAC / First-Month MRR per New Paying Customer |
| Signup-to-Paid Conversion | Percentage of signups that become paying customers | Customers Paying Within N Days / Eligible Signups |

### Payment KPIs

| KPI | Meaning | Calculation |
|---|---|---|
| Collection Rate | Percentage of billed amounts collected | Amount Paid / Amount Due |
| Failed Payment Rate | Percentage of due invoices that failed | Failed Invoices / Due Invoices |
| Cash Collected | Total amount received from customers | Sum of Amount Paid |
| Outstanding Revenue | Billed amount that remains unpaid | Amount Due − Amount Paid |

**Important metric definitions:**

- MRR is calculated using month-end active subscription values.
- ARR is an annualized run rate, not recognized annual revenue.
- NRR includes expansion revenue, while GRR does not.
- CAC uses newly paying customers as its denominator.
- CAC payback is an estimate and is not adjusted for gross margin.
- Reactivated customers are included in new MRR but excluded from first-time new paying customer counts.
- Churn calculations use opening-period paying customers as the denominator.

---

## 7. Dashboard Development

**Tools: HTML, CSS, JavaScript, Chart.js**

After the data preparation and SQL analysis stages, the important business metrics are presented through an interactive dashboard.

The dashboard is built as a browser-based application using HTML, CSS, and JavaScript, with Chart.js for visualizations.

It contains five dedicated pages.

### Page 1: Executive Overview

Provides management with a quick understanding of the company's overall performance.

**Main KPIs:**
- Annualized MRR (ARR)
- Net MRR Growth
- Net Revenue Retention (NRR)
- Paying Customers
- Customer Churn
- Average Revenue per Account (ARPA)

**Visualizations:**
- Monthly MRR Trend
- Paying Customer Trend
- Customer Churn Trend
- ARPA Trend

### Page 2: Revenue Intelligence

Explains where recurring revenue comes from and what causes it to increase or decrease.

**Main KPIs:**
- New MRR
- Expansion MRR
- Contraction MRR
- Churned MRR
- NRR
- GRR

**Visualizations:**
- Monthly Revenue Bridge
- Net New MRR Trend
- Revenue Movement Breakdown
- NRR and GRR Trends

### Page 3: Customer Retention

Focuses on customer behavior, retention patterns, and churn.

**Main KPIs:**
- Gross Revenue Retention
- Average Observed Customer Lifetime
- Churned Customers

**Visualizations:**
- Monthly Logo Churn Trend
- Cohort Retention Heatmap
- Retention by Acquisition Channel
- Retention by Company Size
- Customer Lifetime by Channel
- Customer Lifetime Distribution
- Churn by Subscription Tenure

### Page 4: Subscription and Plan Analytics

Analyzes subscription performance and how customers move between pricing plans.

**Main KPIs:**
- Upgrade Rate
- Downgrade Rate
- Discount vs. List Price

**Visualizations:**
- Active Subscriptions by Plan
- MRR Contribution by Plan
- Upgrade and Downgrade Trends
- Plan Transition Matrix
- Revenue per Customer by Plan
- Discounted vs. Full-Price Revenue
- Actual MRR vs. List-Price MRR

### Page 5: Acquisition and Payments

Evaluates marketing performance and invoice collection.

**Acquisition KPIs:**
- Signup-to-Paid Conversion
- Blended CAC
- Estimated CAC Payback

**Acquisition Visualizations:**
- New Customers by Channel
- Signup-to-Paid Conversion
- CAC by Channel
- CAC Payback by Channel
- Paid Revenue by Channel
- Channel Economics Table

**Payment KPIs:**
- Failed Payment Rate
- Cash Collected
- Due Invoices

**Payment Visualizations:**
- Invoice Collection Rate
- Failed Payment Trend
- Payment Status Distribution

### Dashboard Filters

A reporting period selector allows users to change the time window.

Available options include:

- Last 24 Months
- Last 12 Months
- Last 6 Months
- Last 3 Months
- Calendar Year 2024
- Calendar Year 2025

The selected period updates the KPIs and visualizations across all five dashboard pages.

---

## 8. Dashboard Hosting

The dashboard is hosted on **Netlify**, making it accessible through a public web link without requiring users to install anything.

**Live Dashboard:** [https://nimbusflow-dashboard.netlify.app/](https://nimbusflow-dashboard.netlify.app/)

The dashboard runs directly in a web browser.

Its visualizations and calculations use the prepared dataset embedded in the dashboard, so a separate application backend is not required for the deployed version.

The project uses Chart.js and Google Fonts through external CDN services, so an internet connection is required for those resources.

---

## 9. Technology Stack

| Technology | Application |
|---|---|
| Python | Data cleaning and processing |
| Jupyter Notebook | Data exploration and cleaning workflow |
| Pandas | Data manipulation and transformation |
| NumPy | Numerical operations |
| PostgreSQL | Relational database and SQL analysis |
| SQL | Business analysis and KPI calculations |
| HTML | Dashboard structure |
| CSS | Dashboard design and styling |
| JavaScript | Dashboard logic and interactivity |
| Chart.js | Data visualization |
| Netlify | Dashboard hosting and deployment |
