# Data Cleaning and Preparation Process

## Overview

This document describes the data cleaning and preparation steps performed before building the Power BI dashboard for the Cafe Business Profitability and Operations Analysis project.

The objective of this stage was to transform raw operational datasets into a structured and reliable format suitable for analysis, visualization, and business decision-making.

---

## Data Source

The datasets were obtained from **Ngee Ann Polytechnic** as part of an academic analytics project.

The data consisted of multiple sales records collected across different operational periods and food court locations.

The primary datasets included:

* Sales data for **October 2022 – April 2023**
* Sales data for **October 2023**
* Supporting operational and product information
* Menue prices in 2022 and 2023
* Operation Costs
* NP Acad Calander

---

## Step 1: Data Import

All datasets were imported into **Power BI Power Query Editor**.

Each dataset initially existed as separate files representing different operational periods.

---

## Step 2: Combining Sales Datasets

To create a continuous timeline for analysis:

* The sales datasets from **October 2022 – April 2023** and **October 2023** were combined.
* The datasets were merged using the **Append Queries** function in Power Query.
* Appending allowed all transaction records to be stored within a single unified sales table.

This ensured consistent time-series analysis across reporting periods.

---

## Step 3: Data Cleaning Operations

Several transformation steps were applied to standardize and prepare the data.

### Column Adjustments

* Removed unnecessary columns
* Reordered columns for logical structure
* Renamed columns for clarity and consistency
  

### Data Type Standardization

* Converted columns into appropriate data types

  * Dates → Date format
  * Numerical fields → Decimal/Whole Number
  * Text fields → Text format

---

## Step 4: Date Transformations

To support time-based analysis:

* Inserted **Start of Month** values
* Extracted **Month Name**
* Extracted **Year**
* Created additional time-related columns for trend analysis

These transformations enabled monthly aggregation and comparison across periods.

---

## Step 5: Text Transformations

Product and categorical fields required cleaning to ensure consistency:

* Extracted first characters and last characters where needed
* Standardized naming formats
* Merged columns to create combined identifiers

These steps prevented duplicate category issues during analysis.

for example first 3 letters of a month combined with last 2 numbers in a year

---

## Step 6: Custom Columns Creation

Multiple calculated columns were created using Power Query custom expressions:

* Added Custom Columns for derived business metrics
* Created intermediate transformation columns
* Applied additional logic adjustments through successive custom steps

Custom columns allowed preprocessing calculations before loading data into the Power BI model.

example PROFIT= SALES - COSTS

<img width="244" height="476" alt="image" src="https://github.com/user-attachments/assets/8ccf3080-9952-46b8-9659-7bc3feb48338" />

---

## Step 7: Final Validation

Before loading data into the model:

* Verified row counts after appending datasets
* Checked for null or incorrect values
* Confirmed correct data types
* Ensured consistency across all appended records

---

## Outcome

The final cleaned dataset provided:

* A unified sales table covering all required periods
* Standardized product and operational fields
* Reliable time-based attributes
* Structured data ready for modeling and dashboard development

This cleaned dataset formed the foundation for all subsequent data modeling, DAX calculations, and business analysis performed in the Power BI dashboard.
