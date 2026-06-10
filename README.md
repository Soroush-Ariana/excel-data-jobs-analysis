# Data Jobs Market Analysis

## Introduction

Breaking into the data industry raises a lot of questions — which skills should I focus on? Does learning more tools actually lead to better pay? How do salaries differ between the UK and the US? As someone actively pursuing data analyst roles, I built this project to answer those questions using real data rather than guesswork.

Using a dataset of real-world data job postings from 2023, I analysed the relationships between skills, job titles, salaries, and locations — and drew conclusions that are directly relevant to anyone navigating the data job market today.

### Questions Explored

1. **Do more skills get you better pay?**
2. **What's the salary for data jobs in different regions?**
3. **What are the top skills of data professionals?**
4. **What's the pay for the top 10 skills?**

### Excel Skills Used

- **📊 Pivot Tables**
- **📈 Pivot Charts**
- **🧮 DAX (Data Analysis Expressions)**
- **🔍 Power Query**
- **💪 Power Pivot**

### Dataset

The dataset contains real-world data job postings from 2023, including:

- **👨‍💼 Job titles**
- **💰 Salaries**
- **📍 Locations**
- **🛠️ Skills**

---

## 1️⃣ Do more skills get you better pay?

### 🔍 Power Query (ETL)

#### 📥 Extract

I used Power Query to extract data from the source file (`data_salary_all.xlsx`) and split it into two queries:
- 🗃️ One containing all job information
- 🔧 One listing the skills associated with each job ID

#### 🔄 Transform

Each query was then cleaned and transformed — column types corrected, unnecessary columns removed, text cleaned, and whitespace trimmed.

- 📊 data_jobs_all

    ![data_jobs_all](/Images/2_Project_Analysis_Screenshot1.png)

- 🛠️ data_jobs_skills

    ![data_jobs_skills](/Images/2_Project_Analysis_Screenshot2.png)

#### 🔗 Load

Both cleaned queries were loaded into the workbook as tables, forming the foundation for all subsequent analysis.

- 📊 data_jobs_all

    ![data_jobs_all loaded](/Images/2_Project_Analysis_Screenshot3.png)

- 🛠️ data_jobs_skills

    ![data_jobs_skills loaded](/Images/2_Project_Analysis_Screenshot4.png)

### 📊 Analysis

#### 💡 Insights

- 📈 There is a clear positive correlation between the number of skills requested in a job posting and the median salary — particularly visible in roles like Senior Data Engineer and Data Scientist.
- 💼 Roles requiring fewer skills, such as Business Analyst, tend to offer lower salaries, suggesting that specialisation and breadth of skills both carry measurable market value.

    ![Chart 1](/Images/2_Project_Analysis_Chart1.png)

#### 🤔 So What

For anyone planning their learning path, this is a strong signal that building a diverse, relevant skill set — rather than mastering just one tool — is likely to translate into better compensation.

---

## 2️⃣ What's the salary for data jobs in different regions?

### 🧮 PivotTables & DAX

#### 📈 Pivot Table

I built a PivotTable using the Data Model created in Power Pivot, placing `job_title_short` in the rows area and `salary_year_avg` in the values area. I then added a custom DAX measure to calculate the median salary specifically for US-based roles:

```
=CALCULATE(
    MEDIAN(data_jobs_all[salary_year_avg]),
    data_jobs_all[job_country] = "United States")
```

#### 🧮 DAX

A separate DAX measure was created to calculate the overall median salary across all countries:

```
Median Salary := MEDIAN(data_jobs_all[salary_year_avg])
```

### 📊 Analysis

#### 💡 Insights

- 💼 Senior Data Engineer and Data Scientist roles command the highest median salaries both in the US and internationally, reflecting consistent global demand for advanced data expertise.
- 💰 The salary gap between US and Non-US roles is most pronounced in high-tech positions, likely driven by the concentration of large tech employers in the US market.

    ![Chart 2](/Images/2_Project_Analysis_Chart2.png)

#### 🤔 So What

Understanding regional salary differences is directly useful for salary benchmarking and negotiations — whether you're evaluating a local offer or considering opportunities abroad.

---

## 3️⃣ What are the top skills of data professionals?

### 💪 Power Pivot

#### Data Model

I integrated the `data_jobs_all` and `data_jobs_skills` tables into a single Power Pivot data model, establishing a relationship between them via the `job_id` column. Since both tables had already been cleaned in Power Query, the relationship was created cleanly with no conflicts.

![Data Model](/Images/2_Project_Analysis_Screenshot5.png)

#### Power Pivot Menu

The Power Pivot interface was used to manage the data model and define measures for analysis.

![Power Pivot Menu](/Images/2_Project_Analysis_Screenshot6.png)

### 📊 Analysis

#### 💡 Insights

- 💻 SQL and Python are the most in-demand skills across data roles by a significant margin, confirming their foundational importance in the industry.

    ![Chart 3](/Images/2_Project_Analysis_Chart3.png)

#### 🤔 So What

For someone early in their data career, this analysis reinforces where to focus learning efforts: SQL and Python — a combination that appears consistently across the highest-demand roles.

---

## 4️⃣ What's the pay for the top 10 skills?

### 📈 Advanced Pivot Chart

I created a combo PivotChart to visualise both median salary and skill likelihood (%) side by side:

- 🪙 **Primary Axis:** Median Salary — Clustered Column
- 👍 **Secondary Axis:** Skill Likelihood — Line with diamond markers

The chart was customised with axis titles, gridline adjustments, and marker formatting for clarity.

### 📊 Analysis

#### 💡 Insights

- 💰 Python, Oracle, and SQL are associated with the highest median salaries, reinforcing their value in the market beyond just frequency of appearance.
- 📉 Tools like PowerPoint and Word sit at the bottom of both salary and likelihood rankings — useful for general productivity but not differentiating factors in data roles.

    ![Chart 4](/Images/2_Project_Analysis_Chart4.png)

#### 🤔 So What

This chart is particularly useful for prioritising learning. High salary *and* high likelihood is the sweet spot — and SQL and Python sit squarely in it.

---

## Conclusion

This project gave me practical experience working with a realistic, multi-table dataset using some of Excel's most powerful features — Power Query for data cleaning and transformation, Power Pivot for data modelling, DAX for custom calculations, and PivotCharts for communicating findings visually.

The analysis consistently points in the same direction: specialised, technical skills — particularly Python, SQL, and cloud technologies — are the strongest predictors of higher compensation in the data industry. For someone building their career in data, that's a useful compass.

---

*Built by [Soroush Ariana](https://github.com/Soroush-Ariana) — Data Analyst based in Nottingham, UK*
*📧 arianasoroush@gmail.com*
