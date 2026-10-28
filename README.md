# HR Analytics & Attrition Dashboard 📊

<img width="1327" height="745" alt="HR-Analytics" src="https://github.com/user-attachments/assets/edee6e95-cd5d-4142-a129-e12f8a721bd0" />

An interactive Power BI dashboard that analyzes employee attrition and shows how it changes across job roles, departments and time. Selecting a Job Role instantly recalculates every KPI and chart through custom DAX measures.

🎥 **Demo video:** [Watch on LinkedIn](https://www.linkedin.com/posts/ata-yilmaz12_powerbi-dax-dataanalytics-ugcPost-7521204381824733184--P-1/)

## Key Findings

Overall attrition is **16.12%** (237 of 1,470 employees), but it varies a lot by role:

| Job Role | Employees | Attrition | Rate |
|---|---|---|---|
| Sales Representative | 83 | 33 | **39.76%** |
| Laboratory Technician | 259 | 62 | 23.94% |
| Human Resources | 52 | 12 | 23.08% |
| Research Scientist | 292 | 47 | 16.10% |
| Manufacturing Director | 145 | 10 | 6.90% |
| Healthcare Representative | 131 | 9 | 6.87% |

- Sales Representatives leave at about **2.5x the company average**.
- Research & Development has the most leavers in absolute terms (133), but raw counts hide the real risk: the rate matters more than the count.

## Data Model

- **Fact table:** `HR_Analytics_Fact`
- **Dimension:** `CALENDAR` (synthetic date table), related one-to-many to the fact table on `CALENDAR[Date]` → `HR_Analytics_Fact[Hire_Date]`

## DAX Measures

```DAX
Total Employees = COUNTROWS ( HR_Analytics_Fact )

Attrition Count =
CALCULATE ( [Total Employees], HR_Analytics_Fact[Attrition] = "Yes" )

Attrition Rate =
DIVIDE ( [Attrition Count], [Total Employees], 0 )
```

`CALCULATE` changes the filter context to count only employees who left, and `DIVIDE` safely handles division by zero. All three measures respond to the Job Role slicer, which is why the KPI cards update live.

## Dashboard Contents

- **KPI cards:** Total Employees, Attrition Count, Attrition Rate
- **Attrition Trend:** employees who left, grouped by hire year (via the Calendar table)
- **Attrition by Department:** number of leavers per department
- **Job Role slicer:** cross-filters every visual on the page

## Dataset

[IBM HR Analytics Employee Attrition & Performance](https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset) (Kaggle). This is a fictional dataset created by IBM data scientists, so the findings illustrate the analysis method and are not real company data. The `Hire_Date` column is derived for time analysis and is not part of the original dataset.

## How to Open

1. Install [Power BI Desktop](https://powerbi.microsoft.com/desktop/) (free, Windows).
2. Download `HR-Analytics-PowerBI-Dashboard.pbix` and open it.

## Tools

Power BI · DAX · Data Modeling
