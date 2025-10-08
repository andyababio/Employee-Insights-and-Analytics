
# 📊 DISC-CORP Workforce Analytics Dashboard (MySQL + Power BI)

##  Project Overview
This project demonstrates an end-to-end **data analytics workflow** focused on HR insights at **DISC-CORP**.  
The goal was to clean, analyze, and visualize employee data to uncover key **workforce trends** that enable data-driven decision-making within Human Resources.

---

##  Objectives
- How is the workforce distributed across departments and locations?
- What are the company’s attrition and retention trends over time?
- How diverse is the organization in terms of gender and race?
- What is the relationship between age, tenure, and employee exits?

---

##  Insights
👥 Workforce Distribution Across Departments and Locations

The dashboard reveals that the majority of DISC-CORP employees are concentrated in the [Top Department – e.g., Operations], accounting for [X%] of the total workforce. Departments such as [Department 2] and [Department 3] follow closely behind.
In terms of geography, [Top Location – e.g., Headquarters] houses the highest number of employees ([X] staff), while [Remote/Regional Office] and [Other Locations] show smaller but growing employee bases. This distribution highlights DISC-CORP’s strong central presence and potential for future regional expansion.

📉 Attrition and Retention Trends Over Time

Analysis of hire and termination dates indicates that [X] employees have exited the company, resulting in a total attrition rate of [Y%]. The average tenure across the organization is [Z years], suggesting moderate employee stability.
Year-over-year trends reveal that attrition [increased/decreased/stabilized] in [recent year], with departments like [High Exit Dept] showing the highest turnover, while [Low Exit Dept] maintained strong retention. These insights can guide targeted retention strategies to reduce exits in vulnerable areas.

🌍 Workforce Diversity by Gender and Race

The diversity analysis shows a [balanced/skewed] gender distribution, with [X% male] and [Y% female] employees.
Racial representation data indicates that [Top Race Group] makes up [X%] of the workforce, followed by [Other Groups] at [Y%], reflecting [level of diversity – e.g., moderate representation across multiple groups].
These findings highlight the company’s current diversity profile and provide a basis for future inclusion initiatives.

---

<img width="1092" height="611" alt="Screenshot 2025-10-08 at 10 22 36 PM" src="https://github.com/user-attachments/assets/7ba217c8-7f0a-4d34-b1dc-f727d6a7675d" />

---

##  Data Source
The dataset contains employee-level information such as personal demographics, employment details, and termination records.  

**Key fields include:**  
`emp_id`, `gender`, `race`, `department`, `jobtitle`, `hire_date`, `termdate`, `location`, `age`, `tenure`

---

##  Tools & Technologies
| Tool | Purpose |
|------|----------|
| **MySQL** | Data cleaning, transformation, and exploratory analysis |
| **Power BI** | Dashboard creation and data visualization |
| **Excel** | Preliminary dataset review and formatting |

---

##  Key KPIs
-  **Total Employees**
-  **Current Staff**
-  **Total Exits**
-  **Exit Percentage**
-  **Average Age**
-  **Average Tenure**


⏳ Relationship Between Age, Tenure, and Employee Exits

The dashboard uncovers a clear relationship between age, tenure, and turnover. Employees aged [X–Y years] show the highest exit rates, often associated with shorter tenures of [Z years or less].
Conversely, long-serving employees (tenure above [A years]) tend to be older (above [B years]) and demonstrate greater job stability.
This pattern suggests that younger or newly hired staff may require targeted engagement, mentorship, or development programs to improve retention early in their employment journey.

---

##  Key Deliverables
1. **MySQL Data Cleaning Script**  
   - Handles missing values, standardizes date formats, and calculates derived metrics (e.g., Age, Tenure)
2. **Power BI Dashboard**  
   - Interactive visualizations of workforce KPIs
3. **Documentation & Insights Summary**  
   - Explains metrics, filters, and data-driven insights

---

##  Project Workflow
1. **Data Import & Cleaning** → MySQL  
2. **Exploratory Analysis** → SQL queries for workforce patterns  
3. **Data Connection** → Power BI (via MySQL connector)  
4. **Visualization & Insights** → Dashboard creation and interpretation  

---


##  Key Learnings
- Reinforced knowledge of **data cleaning and transformation** in SQL  
- Learned to connect and refresh **MySQL data in Power BI**  
- Improved dashboard design and **KPI storytelling** for HR analytics  

---

##  Conclusion
This project showcases how **data-driven workforce analytics** can support organizational decision-making.  
It highlights the importance of combining **data engineering (MySQL)** and **data visualization (Power BI)** to generate meaningful business insights.

---

