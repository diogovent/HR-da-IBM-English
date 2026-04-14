# 👥 IBM HR Analytics

# Dashboard:
![Dashboard Preview](https://github.com/diogovent/RH-da-IBM/blob/main/Dashboard.png)

# **📌 Index**

 - About the Project
 - Dataset
 - Technologies Used
 - Dashboard Structure
 - DAX Measures Created
 - Key Insights
 - Recommendations
 - How to Access the Dashboard

---

# **📋 About the Project**

The aim of this project was to apply data analysis techniques and knowledge to a real-world 
Human Resources dataset provided by IBM, in order to extract actionable insights about its workforce.

This project covers the following areas of analysis:

 - Demographic breakdown of staff (age, gender and role)
 - Staff turnover rate and associated factors
 - Job satisfaction
 - Impact of overtime on staff well-being
 - Average salary by role
 - 
---

# **🗂️ Dataset**

Source: Kaggle — IBM HR Analytics Attrition Dataset (https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset?resource=download&select=WA_Fn-UseC_-HR-Employee-Attrition.csv)

Provided by IBM

Number of records: 1,470 employees

Number of columns: 35 variables

---

# **🛠️ Technologies Used**

 - Power BI Desktop — building dashboards and data models
 - DAX (Data Analysis Expressions) — creating measures and calculated columns
 - Power Query — transforming and cleaning data

---

# **📊 Dashboard Structure**

| Section | Description |
|---|---|
| **Key KPIs** | Total number of employees, average salary and staff turnover rate |
| **Gender Breakdown** | Comparison between male and female employees |
| **Age Group Breakdown** | Grouping into age groups created using DAX |
| **Distribution by Role** | Roles with the highest number of employees |
| **Job Satisfaction** | Percentage by level (Low, Moderate, High, Very High) |
| **Overtime** | Employees who work overtime vs. those who do not |

---

# **🧮 DAX Measures Created**

Below are the main dimensions and calculated values developed in this project:

Total number of employees:
```dax
   Total de Funcionários = COUNTROWS(Dados_RH)
````

Total by gender:
```dax
 - Total de Funcionários Masculinos = CALCULATE(COUNTROWS(Dados_RH), Dados_RH[Gender] = "Male")
 - Total de Funcionários Femeninos = CALCULATE(COUNTROWS(Dados_RH), Dados_RH[Gender] = "Female")
````

Percentage by gender:
```dax
 - % de Funcionários Masculinos = DIVIDE([Total de Funcionários Masculinos],[Total de Funcionários])
 - % de Funcionários Femeninos = DIVIDE([Total de Funcionários Femeninos],[Total de Funcionários])
````

Average length of service within the company:
```dax
 - Experiência Média de Trabalho = AVERAGE(Dados_RH[TotalWorkingYears])
````

Average salary:
```dax
 - Salário Médio = AVERAGE(Dados_RH[MonthlyIncome])
````

Turnover rate and %:
```dax
 - Total de Ex Funcionarios = CALCULATE(COUNTROWS(Dados_RH),Dados_RH[Attrition] = "Yes")
 - % de Ex Funcionários = DIVIDE([Total de Ex Funcionarios],[Total de Funcionários])
````

Overtime:
```dax
 - Hora Extra Sim = CALCULATE(COUNTROWS(Dados_RH),Dados_RH[OverTime] = "Yes")
 - Hora Extra Não = CALCULATE(COUNTROWS(Dados_RH),Dados_RH[OverTime] = "No")
````

Calculated Column — Age Group:
```dax
 - Faixa Etaria = SWITCH(
    TRUE(),
    Dados_RH[Age] <= 17, "0-17",
    Dados_RH[Age] >= 18 && Dados_RH[Age] <= 25, "18-25",
    Dados_RH[Age] >= 26 && Dados_RH[Age] <= 35, "26-35",
    Dados_RH[Age] >= 36 && Dados_RH[Age] <= 45, "36-45",
    Dados_RH[Age] >= 46 && Dados_RH[Age] <= 55, "46-55",
    "56+"
)
````

---

# **📈 Key Insights**

### 👥 Workforce

IBM has **1,470 employees** in the dataset analysed.

The predominant age group is between **26 and 45 years old**, representing the company’s core workforce.
There is a predominance of **male employees (≈60%)** compared to **female employees (≈40%)**.


### 💰 Remuneration

The average monthly salary is **$6,503**.

The roles with the highest number of employees are **Executive** and **Research Scientist**, 
both of which have historically been associated with higher pay in the technology sector.


### 🚨 Critical Points

The **turnover rate stands at 16.12%** — a figure higher than what is considered healthy for the technology sector (typically between 10–13%).

Almost **40% of employees** report a level of satisfaction that is **‘Low’** or **‘Moderate’**, which is a significant warning sign.

**28.3% of employees** work overtime, which may be contributing to burnout among critical teams.

---

# **💡 Recommendations**

Based on the analysis carried out, the following recommendations are made to IBM:

1. **Conduct a thorough internal survey** to identify the root causes of dissatisfaction, 
with a particular focus on departments with the highest staff turnover rates.

2. **Review the overtime policy** — the fact that 28.3% of staff are working overtime is a figure which,
if left unchecked, could accelerate burnout and exacerbate staff turnover.

 4. **Cross-reference job satisfaction with job title and length of service** to identify whether there is a specific pattern 
(e.g. employees with 5–10 years’ experience are more dissatisfied — often the most valuable and hardest to replace).

5. **Draw up a retention plan** targeting the 26–45 age group, which accounts for the majority of the workforce.

---

# **🔗 How to Access the Dashboard**

You can interact with the full dashboard via the Power BI Service: https://app.powerbi.com/groups/me/reports/865a4e19-1e2d-4d82-b965-7991eb501a15/76202f17b6daa6a0a0a8?experience=power-bi

Alternatively, you can access it via the document titled "Projeto.pbix" which is in this repository
