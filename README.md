# GlobalTech Solutions — Workforce & Attrition Dashboard

## Overview
A Power BI dashboard analyzing employee workforce data for GlobalTech Solutions, covering retention, satisfaction, and department-level attrition trends from 2018–2024.

## Purpose
HR and department leaders needed visibility into where and why employees were leaving, so they could target retention efforts at the roles and departments most affected instead of relying on anecdotal feedback.

## What I Did
- Cleaned and modeled raw HR data (`GlobalTech_HR_RAW.xlsx`) covering employee tenure, salary, job role, department, work mode, and attrition status.
- Built interactive slicers for **Department**, **Work Mode**, and **Over Time (Attrition Yes/No)** to let stakeholders drill into specific segments.
- Created KPI cards summarizing headcount, attrition rate, average tenure, and average salary.
- Built visuals to compare:
  - Attrition rate by job role and by department
  - Average satisfaction score for employees who stayed vs. left
  - Monthly headcount trend across the year
- Documented the build process and design decisions in `GlobalTech_HR_Solution_Guide.pdf`.

## Outcome / Key Insights
- **430** total employees analyzed, with an overall attrition rate of **22%**.
- Average tenure is **3.02 years**; average salary is **$87.76K**.
- Employees who left report a lower average satisfaction score (**2.92**) than those who stayed (**3.04**) — a modest but measurable early warning signal.
- **Software Engineer** and **Sales Manager** roles show the highest attrition rates (0.43 and 0.35), while **Sales** and **Engineering** are the highest-attrition departments.
- These findings point HR toward targeted retention initiatives for high-risk roles/departments rather than broad, unfocused programs.

## Dashboard Preview
![Dashboard Screenshot](Screenshot%202026-08-10%20161929.png)

## Files
| File | Description |
|---|---|
| `GlobalTech_HR_RAW.pbix` | Power BI project file (data model, DAX measures, report) |
| `GlobalTech_HR_RAW.xlsx` | Raw source data |
| `GlobalTech_HR_RAW.pdf` | Exported PDF version of the report |
| `GlobalTech_HR_Solution_Guide.pdf` | Write-up of the approach and solution steps |
| `Screenshot 2026-08-10 161929.png` | Dashboard preview image |

## Tools Used
Power BI Desktop, DAX, Power Query

---
*Prepared by Aryan Mantrawadi — August 2026*
