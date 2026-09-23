# Sales Performance & MIS Dashboard

## Project Overview

This project is an **Excel-based Sales Performance and MIS Dashboard** built using **Microsoft Excel and Power Query**.

The main purpose of this project is to take raw sales transaction data, clean and validate it, analyze business performance, and present the important results in an interactive MIS dashboard.

The project follows this workflow:

**Raw Sales Data → Power Query Cleaning → Data Validation → Cleaned Sales Data → Analysis → MIS Reporting → Dashboard → Key Findings → Business Recommendations**

---

## Business Problem Statement

Sales data can contain duplicate records, missing values, inconsistent text formats, incorrect data types, and invalid numerical values.

When this type of data is used directly for reporting, it can lead to incorrect sales numbers and make it difficult to understand business performance.

The problem addressed in this project is:

> **How can raw sales transaction data be cleaned, validated, analyzed, and converted into an interactive MIS dashboard that helps management monitor sales, profitability, orders, quantity, regional performance, product performance, salesperson performance, and discount-level performance?**

---

## Business Purpose

The purpose of this project is not only to clean the data or create charts. The main purpose is to convert raw sales transactions into useful MIS information that can help the business monitor performance and identify areas that need attention.

The dashboard brings important sales and profitability information into one place so that management can quickly review:

- Revenue and Profit performance.
- Order volume and Quantity sold.
- Regional performance.
- Category and Product performance.
- Salesperson contribution in terms of Revenue and Profit.
- Revenue and Profit across different Discount levels.
- Monthly changes in sales and profitability.

The findings from the dashboard can then be used to support business discussions and possible actions related to sales performance, profitability, product/category performance, salesperson performance, discount monitoring, and data-quality improvement.

---

## Project Objectives

The main objectives of this project were:

- Clean and prepare the raw sales transaction data using Power Query.
- Identify and handle missing, duplicate, inconsistent, and invalid data.
- Validate numerical values and profitability calculations.
- Create KPI metrics for sales and profitability monitoring.
- Build formula-based MIS summaries for reporting.
- Analyze sales performance across different business dimensions.
- Build an interactive Excel dashboard using PivotTables, PivotCharts, KPI cards, and Slicers.
- Identify important findings from the dashboard.
- Provide business recommendations based on the observed data.

---

## Dataset Description

The project uses a sales transaction dataset containing **1,200 raw sales records**.

The data contains the following main fields:

| Column | Description |
|---|---|
| Order_ID | Unique identifier for the sales order |
| Order_Date | Date of the order |
| Region | Sales region |
| State | State associated with the order |
| Salesperson | Salesperson responsible for the order |
| Category | Product category |
| Product | Product sold |
| Quantity | Quantity sold |
| Unit_Price | Price per unit |
| Discount | Discount applied to the order |
| Revenue | Revenue generated from the order |
| Cost | Cost associated with the order |
| Profit | Profit generated from the order |
| Customer_Type | Type of customer |
| Payment_Method | Payment method used |

The reporting analysis is based on the **cleaned dataset containing 1,180 usable records/orders**.

---

## Data Quality Issues Identified

During the initial review of the raw data, I identified several data-quality issues:

- Duplicate records were present.
- Some Region values were missing.
- Some State values were missing.
- Some Salesperson values were missing.
- Some Discount values were missing.
- Some Order_Date values were missing or invalid.
- Region, Category, Salesperson, and State contained inconsistent spaces and capitalization.
- Some numerical fields needed correct data-type handling.
- Numerical values needed validation for invalid or unexpected values.
- Profit values needed to be checked against Revenue and Cost.

---

## Data Cleaning and Transformation Using Power Query

I used **Power Query** to clean and prepare the dataset before performing the analysis.

### 1. Remove Duplicate Records

I checked the raw dataset for duplicate transaction records and removed duplicate rows.

**Why:** Duplicate transactions can increase Revenue, Profit, Quantity, and order counts incorrectly.

### 2. Standardize Categorical Columns

I checked categorical columns such as:

- Region
- State
- Salesperson
- Category

Where required, I used Power Query formatting functions such as:

- **Trim** – to remove extra spaces.
- **Clean** – to remove non-printable characters.
- **Capitalize Each Word** – to standardize capitalization.

**Why:** This helps avoid multiple categories being created because of differences such as `electronics`, `Electronics`, or extra spaces.

### 3. Handle Missing Categorical Values

For missing categorical values such as Region, State, and Salesperson, I used:

**`Unknown`**

**Why:** I did not want to create a false value. Using `Unknown` keeps the record available for reporting while clearly showing that the original value was missing.

### 4. Handle Missing Order Dates

I checked the Order_Date column for missing or invalid dates.

Rows without a valid Order_Date were removed because a valid date is required for monthly and time-based analysis.

**Why:** I did not want to create or assume a date that was not available in the source data.

### 5. Handle Missing Discount Values

I checked the Discount column for null values.

Because Discount is a numerical field, I did not replace missing values with `Unknown` or assume that the missing discount was `0`.

Instead, records with missing Discount values were filtered out.

**Why:** Assuming a missing discount is zero could affect discount and profitability analysis.

### 6. Set Correct Data Types

I checked and corrected data types for the dataset.

Examples:

- Order_ID → Text
- Order_Date → Date
- Region / State / Salesperson / Category / Product → Text
- Quantity → Whole Number
- Unit_Price → Decimal Number
- Discount → Decimal Number
- Revenue → Decimal Number
- Cost → Decimal Number
- Profit → Decimal Number

**Why:** Correct data types are required for accurate calculations, filtering, sorting, grouping, and PivotTable analysis.

### 7. Check for Data-Type Errors

After changing the data types, I checked the dataset using Power Query's data-quality information and made sure there were no errors caused by incorrect data types or invalid conversions.

### 8. Validate Numerical Values

I used Power Query number filters to check numerical columns such as:

- Quantity
- Unit_Price
- Discount
- Revenue
- Cost
- Profit

I checked for invalid conditions such as negative quantities, negative prices, and incorrect discount values.

**Why:** Number filters are more practical than manually checking every row in a large dataset.

### 9. Validate Profit Calculation

I validated the existing Profit column by calculating:

**Profit = Revenue - Cost**

A temporary calculated column was created and compared with the existing Profit values.

Because decimal calculations can have small floating-point differences, I compared the values after rounding them to **2 decimal places**.

The validation confirmed that the Profit values were correct.

The temporary validation columns were removed after the check was completed.

---

## Cleaned Data

After the Power Query cleaning and validation process, the prepared dataset was loaded back into Excel as:

**`Cleaned_Sales_Data`**

The cleaned dataset contains **1,180 usable records/orders** used for the final analysis and reporting.

---

# Analysis and MIS Reporting

I created a separate **Analysis_Sheet** to calculate KPIs, create PivotTables, build formula-based MIS summaries, and perform detailed analysis.

## KPI Metrics

The main KPI metrics are:

- Total Revenue
- Total Profit
- Total Orders
- Total Quantity
- Average Order Value (AOV)
- Profit Margin

### KPI Calculations

**Average Order Value**

`Total Revenue / Total Orders`

This shows the average revenue generated per order.

**Profit Margin**

`Total Profit / Total Revenue`

This shows profit as a percentage of revenue.

---

## Overall KPI Snapshot

The unfiltered dashboard values are:

| KPI | Value |
|---|---:|
| Total Revenue | ₹11,47,63,273.17 |
| Total Profit | ₹2,95,40,009.64 |
| Total Orders | 1,180 |
| Total Quantity | 5,218 |
| Average Order Value | ₹97,257.01 |
| Profit Margin | 25.74% |

---

# Formula-Based MIS Reporting

I also created formula-based reporting sections to automate recurring MIS calculations.

## SUMIFS

Used **SUMIFS** to calculate Total Revenue and Total Profit by Region.

**Purpose:** Automate region-wise MIS reporting from the cleaned sales table.

## COUNTIFS

Used **COUNTIFS** to calculate Order Count by Region.

**Purpose:** Show the number of orders handled by each region.

## IF

Used **IF** to classify regional performance based on Profit Margin.

Example status:

- Healthy
- Needs Review

**Purpose:** Make the MIS summary easier to interpret.

## XLOOKUP

Used **XLOOKUP** to dynamically retrieve:

- Revenue
- Profit
- Order Count
- Profit Margin

for a selected region from the regional MIS summary.

**Purpose:** Support dynamic lookup-based reporting.

## INDEX-MATCH

Used **INDEX-MATCH** to retrieve:

- Revenue
- Profit

for a selected salesperson from the salesperson analysis.

**Purpose:** Support salesperson-level MIS reporting.

## Conditional Formatting

Applied Conditional Formatting to regional Profit Margin values.

**Purpose:** Make differences in regional profitability easier to identify visually.

---

# Business Analysis Covered

## 1. Monthly Revenue and Profit Trend

A **Line Chart** was created to compare monthly Revenue and Profit.

**Purpose:**

- Monitor sales trends over time.
- Identify changes in Revenue.
- Identify changes in Profit.
- Understand monthly movement in business performance.

## 2. Region Analysis

A PivotTable and **Clustered Column Chart** were created to compare Revenue and Profit by Region.

**Purpose:**

- Compare regional performance.
- Identify regions contributing more Revenue and Profit.
- Support regional MIS reporting.

## 3. Category Analysis

A PivotTable and **Clustered Column Chart** were created to compare Revenue and Profit across product categories.

**Purpose:**

- Understand category contribution.
- Identify categories generating higher Revenue and Profit.
- Support category-level performance monitoring.

## 4. Product Analysis

A PivotTable was created to compare:

- Revenue
- Profit
- Quantity

The chart focuses mainly on Revenue and Profit because Quantity has a much smaller scale and can make the Revenue and Profit comparison difficult to read.

Products were sorted by Revenue to support product-level performance comparison.

## 5. Salesperson Analysis

A PivotTable and **Bar Chart** were created to compare Revenue and Profit by Salesperson.

**Purpose:**

- Compare salesperson contribution.
- Identify differences between Revenue performance and Profit performance.
- Support salesperson-level MIS reporting.

Revenue and Profit were kept as separate measures because a salesperson with high Revenue does not necessarily have the highest Profit.

## 6. Discount Analysis

A PivotTable and **Clustered Column Chart** were created to compare Revenue and Profit across different discount levels.

**Purpose:**

- Understand how Revenue and Profit vary across discount levels.
- Support discount-level performance monitoring.
- Provide a basis for further review of discount patterns.

---

# Interactive Excel Dashboard

A separate **Dashboard** sheet was created to bring the main analysis into one place.

The dashboard was designed around an **85% Excel viewing level**, using approximately **columns A:Z and rows 1:33** so the main reporting view can be seen without unnecessary scrolling.

## Dashboard Components

### 6 KPI Cards

- Total Revenue
- Total Profit
- Total Orders
- Total Quantity
- Average Order Value
- Profit Margin

### 6 PivotCharts

1. Monthly Revenue & Profit Trend
2. Region-wise Revenue & Profit
3. Category-wise Revenue & Profit
4. Product-wise Revenue & Profit
5. Salesperson-wise Revenue & Profit
6. Discount-wise Revenue & Profit

### Interactive Filters

- Region slicer
- Category slicer

The Region and Category slicers are connected to the reporting PivotTables, allowing the charts and KPI cards to update together based on the selected filters.

The KPI cards also update with the selected filters, including Revenue, Profit, Orders, Quantity, Average Order Value, and Profit Margin.

---

# Key Findings / Business Outcomes

The dashboard was used to identify the following findings from the available sales data.

### Regional Performance

The **South region** recorded the highest Revenue and Profit among the reported regions.

- Revenue: **₹3,21,31,258.38**
- Profit: **₹81,99,036.29**

This shows that South contributed a significant share of the overall sales and profit in this dataset.

### Category Performance

**Electronics** recorded the highest Revenue and Profit among the analyzed product categories.

This makes Electronics an important category to monitor in the sales MIS report.

### Product Performance

**Laptop** was the highest-revenue product in the product analysis.

This makes Laptop an important product to monitor in terms of sales contribution.

### Salesperson Performance

**Arjun** recorded the highest Revenue among salespersons, while **Sneha** recorded the highest Profit.

This shows why Revenue and Profit should be monitored separately in MIS reporting.

### Discount Performance

The **5% discount level** recorded the highest total Revenue and total Profit among the discount levels in this dataset.

This is an observed relationship in the available data. It does not by itself prove that the 5% discount caused the higher Revenue or Profit, because sales volume, product mix, and other factors can also affect the results.

---

# Business Recommendations

The recommendations below are based on the observed dashboard findings and are intended as areas for business review.

### 1. Monitor High-Contributing Regions

Review the products, categories, and salespersons contributing to the performance of high-revenue regions and monitor whether the same pattern continues in future reporting periods.

### 2. Monitor High-Contributing Categories and Products

Track Electronics and high-revenue products such as Laptop regularly to understand whether their contribution remains consistent over time.

### 3. Review Revenue and Profit Together

Evaluate salesperson performance using both Revenue and Profit instead of Revenue alone so that sales contribution and profitability can be viewed together.

### 4. Review Discount Performance Carefully

Review discount levels together with order volume, product mix, Revenue, and Profit rather than assuming that one discount percentage is always better.

### 5. Improve Source Data Quality

Improve data-entry and source-system validation to reduce missing values, inconsistent text, duplicate records, and invalid values in future reporting cycles.

### 6. Use the Dashboard for Recurring MIS Reviews

Use the dashboard as a regular reporting view for Sales, Profit, Orders, Quantity, regional performance, category performance, product performance, salesperson performance, and discount-level performance.

---

# Tools Used

### Microsoft Excel

- Excel Tables
- PivotTables
- PivotCharts
- Slicers
- XLOOKUP
- INDEX-MATCH
- SUMIFS
- COUNTIFS
- IF
- Conditional Formatting
- KPI Reporting
- MIS Reporting
- Charts and Data Visualization

### Power Query

- Data Cleaning
- Data Standardization
- Duplicate Removal
- Missing-Value Handling
- Data-Type Management
- Numerical Validation
- Profit Validation

---

# Excel Project Structure

The workbook contains the following main sheets:

```text
Raw_Sales_Data
Data_Dictionary
Power_Query_Steps
Cleaned_Sales_Data
Analysis_Sheet
Dashboard
```

### Raw_Sales_Data

Contains the original 1,200 sales transaction records before cleaning.

### Data_Dictionary

Contains definitions and descriptions of the main data columns.

### Power_Query_Steps

Documents the major cleaning and validation workflow performed in Power Query.

### Cleaned_Sales_Data

Contains the cleaned data used for analysis and reporting.

### Analysis_Sheet

Contains:

- KPI calculations
- PivotTables
- Formula-based MIS summaries
- XLOOKUP
- INDEX-MATCH
- Conditional Formatting
- Detailed performance analysis

### Dashboard

Contains:

- 6 KPI cards
- 6 PivotCharts
- Region slicer
- Category slicer
- Interactive MIS reporting view

---

# How to Use the Dashboard

1. Open the Excel workbook.
2. Go to the **Dashboard** sheet.
3. Review the six KPI cards.
4. Use the **Region** slicer to filter the dashboard by Region.
5. Use the **Category** slicer to filter the dashboard by Category.
6. Observe the KPI cards and charts updating based on the selected filters.
7. Use the **Analysis_Sheet** for detailed PivotTable and formula-based analysis.
8. Clear the slicer filters to return to the overall dashboard view.

---

# Project Outcome

The final result is an **interactive Excel MIS dashboard** that converts raw sales transaction data into a structured reporting solution.

The project demonstrates the complete reporting process:

**Data Cleaning → Data Validation → KPI Calculation → MIS Analysis → Visualization → Interactive Dashboard → Key Findings → Business Recommendations**

The workbook provides a practical example of how Excel and Power Query can be used to prepare sales data, monitor performance, identify business patterns, and support recurring MIS reporting.

---

# Repository Structure

```text
Sales_Performance_MIS_Dashboard/
│
├── README.md
└── Sales_Performance_MIS_Dashboard_Project.xlsx
```

---

## Project Skills Demonstrated

**Excel:** PivotTables, PivotCharts, Slicers, XLOOKUP, INDEX-MATCH, SUMIFS, COUNTIFS, IF, Conditional Formatting, KPI Reporting, MIS Reporting

**Power Query:** Data Cleaning, Data Standardization, Missing-Value Handling, Duplicate Removal, Data-Type Management, Numerical Validation, Profit Validation

**Analysis:** KPI Calculation, Trend Analysis, Regional Analysis, Category Analysis, Product Analysis, Salesperson Analysis, Discount Analysis
