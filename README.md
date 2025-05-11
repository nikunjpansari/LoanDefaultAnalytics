# End-to-End Power BI Project: Loan Default Analytics

An end-to-end walkthrough of building a Loan Default analytics solution in Power BI, sourcing data from Power BI Dataflows (default CSV), performing transformations, modeling with DAX, and creating interactive visuals.

---

## Table of Contents

1. [Project Overview](#project-overview)  
2. [Prerequisites](#prerequisites)  
3. [Architecture & Dataflow Setup](#architecture--dataflow-setup)  
4. [Data Preparation](#data-preparation)  
5. [DAX Calculations](#dax-calculations)  
6. [Report Development](#report-development)  
7. [Deployment & Refresh](#deployment--refresh)  

---

## Project Overview

This project demonstrates how to:

- Download, install, and configure an on-premises data gateway in **Standard Mode**  
- Import and stage a **Loan Default** CSV into **SQL Server**  
- Create a **Power BI Dataflow** from the SQL staging layer  
- Connect **Power BI Desktop** to the Dataflow  
- Clean and profile data in **Power Query Editor**  
- Build robust **DAX measures** for analytics  
- Develop interactive **Power BI** visuals and validate results  
- Configure **incremental refresh** and scheduled data refresh  
- Publish the report to the **Power BI Service** and share with stakeholders

---

## Prerequisites

- Power BI Desktop (latest version)  
- SQL Server instance (local or cloud)  
- Power BI Pro or Premium Per User license  
- On-premises data gateway installed and registered  

---

## Architecture & Dataflow Setup

1. **Gateway Setup**: Download, install, and configure the Power BI On-premises Data Gateway (Standard Mode).  
2. **SQL Server Staging**: Bulk-load the Loan Default CSV into a staging table (e.g., `dbo.LoanDefaults`).  
3. **Create Dataflow**: In Power BI Service, create a Dataflow that connects to the staging table via the gateway.  
4. **Dataflow Transformations**: Apply light transformations (rename columns, enforce data types) and refresh the Dataflow.  
5. **Connect Desktop**: In Power BI Desktop, use **Get Data → Power BI Dataflows** to import entities from the Dataflow.

---

## Data Preparation

- **Column Definitions & Dataset Description**: Document each field (LoanID, ApplicantAge, EmploymentType, AnnualIncome, LoanAmount, LoanPurpose, CreditScoreCategory, DefaultStatus, ApplicationDate).  
- **Data Types & Profiling**: In Power Query Editor, verify data types; use Column Quality and Distribution views to handle nulls, outliers, duplicates.

---

## DAX Calculations

- **Loan Amount by Purpose**  
  *DAX Used: `SUMX`, `FILTER`, `NOT`, `ISBLANK`*  
- **Average Income by Employment Type**  
  *DAX Used: `CALCULATE`, `AVERAGE`, `ALLEXCEPT`*  
- **Default Rate by Employment Type**  
  *DAX Used: `ALL`, `ALLEXCEPT`, `COUNTROWS`, `DIVIDE`, `FILTER`*  
- **Average Loan by Age Groups**  
  *DAX Used: `AVERAGE`, `AVERAGEX`, `VALUES`*  
- **Default Rate by Year**  
  *DAX Used: `CALCULATE`, `COUNTROWS`, `ALLEXCEPT`, `FILTER`, `DIVIDE`*  
- **Median Loan Amount by Credit Score Category**  
  *DAX Used: `MEDIANX`*  
- **YOY Loan Amount Change**  
  *DAX Used: `SAMEPERIODLASTYEAR`*  
- **YOY Default Rate Change**  
  *DAX Used: subtraction of current and previous period measures*  
- **YTD Loan Amount by Credit Score & Marital Status**  
  *DAX Used: `TOTALYTD`*  
- **Decomposition Tree Measure**  
  *DAX Used: `SWITCH` for dynamic breakdowns*

---

## Report Development

- **Donut Chart**: Average Loan Amount by Age Group & Marital Status (validate proportions).  
- **Clustered Column Chart**: Total Loan by Credit Score Category & Mortgage/Dependents (validate totals).  
- **Line Charts**: YOY Loan Amount and YOY Default Rate Change.  
- **Scatter Plot**: Loan Amount vs. Annual Income with tooltips.  
- **Decomposition Tree**: Drill into key drivers of defaults (CreditScoreCategory, EmploymentType, LoanPurpose).

---

## Deployment & Refresh

1. **Publish**: In Power BI Desktop, select **Publish** → choose target workspace.  
2. **Dataset Configuration**: In Power BI Service, set gateway connection and credentials.  
3. **Incremental Refresh**: Configure partitions on `ApplicationDate` in the dataset settings.  
4. **Scheduled Refresh**: Set up daily (or desired frequency) refresh under dataset settings.  
5. **Share Report**: Assign report access to stakeholders or embed in Microsoft Teams/SharePoint.  
