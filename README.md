# GlobalTech HR — Workforce & Attrition Dashboard

A Power BI dashboard analyzing employee attrition, satisfaction, and workforce trends for a fictional tech company (GlobalTech Solutions), built from a raw, intentionally messy dataset to simulate a real-world analytics workflow — from data cleaning through to a finished, decision-ready report.

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=flat&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-blue?style=flat)
![Status](https://img.shields.io/badge/status-complete-brightgreen)

---

## Project Overview

GlobalTech Solutions is a fictional company losing employees at a rate that concerns leadership, but with no clear picture of where the problem is concentrated, who's most at risk, or whether there's a measurable early-warning signal. This project turns raw, messy HR records into specific, defensible findings leadership could actually act on.

## Business Questions Answered

- How big is the attrition problem, in one clear headline number?
- Is attrition evenly spread across the company, or concentrated in specific departments or roles?
- Does employee satisfaction actually predict who leaves?
- How long do employees typically stay?
- Is there a seasonal pattern to hiring?

## Key Findings

| Metric | Result |
|---|---|
| Total Employees | 430 |
| Attrition Rate | 22% |
| Average Tenure | 3.02 years |
| Average Salary | $87,760 |

- **Sales has the highest department-level attrition rate (24.6%)**; Finance and Marketing retain employees best
- **Software Engineer has the highest attrition rate of any role at 43%** — nearly double the next-highest role, a far sharper signal than the department-level view alone reveals
- Satisfaction does relate to attrition, though modestly: employees who left averaged **2.92/5** satisfaction versus **3.04/5** for those who stayed

The role-level finding (Software Engineer) turned out to be the most important insight in the whole project — a good example of why it pays to look one level deeper than the first obvious breakdown.

## Dashboard Preview

The final report includes:
- 4 KPI cards (Total Employees, Attrition Rate, Average Tenure, Average Salary)
- Attrition rate by department (bar chart)
- Attrition rate by job role (bar chart)
- Satisfaction score by attrition status (bar chart)
- Hires by month (line chart)
- Interactive slicers: Department, Work Mode, OverTime

*(Add a screenshot of your finished dashboard here — drag the exported PNG/PDF into this repo and reference it, e.g. `![Dashboard Screenshot](screenshots/dashboard.png)`)*

## Data Source

The dataset is a synthetically generated, intentionally messy export (`GlobalTech_HR_RAW.xlsx`) simulating real-world data quality issues:

- Inconsistent text formatting (e.g., "Sales" / "sales" / "SALES", "HR" / "Human Resources")
- Salary stored as text with currency symbols mixed with clean numbers
- Meaningful blank values (unanswered satisfaction surveys, still-employed staff with no exit date)
- Inconsistent Yes/No/Y/N values in the OverTime column
- Duplicate and blank rows

## Tools & Skills Used

- **Power Query** — data cleaning, standardizing text, fixing data types, handling meaningful nulls
- **DAX** — CALCULATE, DIVIDE, AVERAGEX, DATEDIFF, ISBLANK, SUMMARIZE
- **Data Modeling** — star schema design (fact + dimension tables), relationship management
- **Power BI Desktop** — report design, interactive slicers, visual formatting

## Data Model

**Fact table:** `HR Export` — one row per employee
**Dimension tables:**
- `Departments` — unique departments, connected 1-to-many to HR Export
- `Calendar` — a generated date table (not extracted from raw data) ensuring a complete, unbroken date range for accurate hiring-trend analysis

```
Departments (1) ──────< HR Export >────── (1) Calendar
```

## Key DAX Measures

```dax
Attrition Rate = 
DIVIDE([Total Attritions], [Total Employees], 0)

Average Satisfaction Score = 
AVERAGE('HR Export'[Satisfaction Survey])

Average Tenure (Years) = 
AVERAGEX(
    'HR Export',
    DATEDIFF('HR Export'[Hire Date], 
             IF(ISBLANK('HR Export'[Exit Date]), DATE(2024,12,31), 'HR Export'[Exit Date]), 
             YEAR)
)
```

**Note on Average Tenure:** uses a fixed reference date (`DATE(2024,12,31)`) instead of `TODAY()`, deliberately anchoring the calculation to the dataset's intended timeframe. Using `TODAY()` would cause tenure numbers to silently inflate every year the file is reopened — a bug caught and fixed during development.

**Note on Average Satisfaction Score:** relies on blank survey responses being left untouched during cleaning (not fabricated with a placeholder value), since `AVERAGE()` automatically excludes nulls — filling blanks with 0 would have silently skewed this measure.

## Data Cleaning Highlights

- Standardized inconsistent Department, Gender, Education, and Work Mode text values into clean categories
- Converted Salary from mixed text/currency format into a usable Whole Number
- Preserved meaningful blank values (unanswered surveys, still-employed staff) rather than fabricating placeholder data
- Removed exact duplicate rows and blank rows using a verified, independently-checked process

## Repository Contents

```
├── GlobalTech_HR_RAW.xlsx         # Raw, messy source dataset
├── GlobalTech_HR_Dashboard.pbix   # Power BI report file
├── GlobalTech_HR_Dashboard.pdf    # Static PDF export of the dashboard
├── screenshots/                   # Dashboard preview images
└── README.md                      # This file
```

## How to Use

1. Clone or download this repository
2. Open `GlobalTech_HR_Dashboard.pbix` in [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (free)
3. Use the slicers (Department, Work Mode, OverTime) to explore the data interactively
4. Refresh the data connection if using the raw `.xlsx` file with updated data

## About This Project

This project was built as part of a portfolio demonstrating end-to-end BI analyst skills: taking raw, imperfect data through cleaning, modeling, calculation, and visualization to a finished, decision-ready dashboard — mirroring the kind of ambiguous, real-world data a Data/BI Analyst encounters on the job.

---

**Author:** Aryan Mantrawadi
**Connect:** [LinkedIn](#) · [Portfolio](#)
