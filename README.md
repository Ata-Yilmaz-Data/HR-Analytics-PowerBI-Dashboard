# HR Analytics & Attrition Dashboard 📊

## 📌 Business Problem
The organization is facing challenges with employee retention. This project aims to analyze historical HR data to uncover attrition trends, identify the most impacted departments, and provide actionable insights for the HR department.

## 🛠️ Technical Architecture & Skills Demonstrated
*   **Data Modeling (Star Schema):** Built a robust Star Schema architecture featuring a synthetic `Calendar` table with a 1-to-many relationship to the `HR_Analytics_Fact` table.
*   **DAX Engineering:** Avoided basic drag-and-drop mechanics by writing custom DAX measures for dynamic filter context evaluation:
    *   `Attrition Count = CALCULATE([Total Employees], HR_Analytics_Fact[Attrition] = "Yes")`
    *   `Attrition Rate = DIVIDE([Attrition Count], [Total Employees], 0)`
*   **Interactive Visualization:** Developed an executive-level dashboard emphasizing clarity, data labels, and cross-filtering capabilities without visual clutter.

## 🎯 Key Insights
*   **Overall Attrition:** The company experiences an overall attrition rate of **16.12%** (237 out of 1470 employees).
*   **Departmental Bleed:** The **Research & Development** department holds the highest raw number of exiting employees, followed by Sales.
*   **Trend Analysis:** The Time Intelligence line chart indicates a massive spike in attrition over the most recent years, requiring immediate executive intervention.

*(Note: View the interactive video demonstration on my LinkedIn profile).*
