# 🎓 International Graduate Employment Analysis Dashboard

<div align="center">

![Banner](https://img.shields.io/badge/EDA-Employment%20Analysis-blue?style=for-the-badge)
![Power BI](https://img.shields.io/badge/Visualization-Power%20BI-yellow?style=for-the-badge)
![Status](https://img.shields.io/badge/Project-Completed-success?style=for-the-badge)

</div>

---

## 📌 Exploratory Data Analysis (EDA)

### 🎯 EDA Objective

The purpose of the Exploratory Data Analysis is to understand the employment outcomes of international graduates. The analysis focuses on employment status, salary, education level, field of study, internship experience, GPA, and other graduate profile factors.

EDA helps answer questions such as:

* 📍 How many graduates are employed, unemployed, or continuing education?
* 📍 What is the overall employment rate?
* 📍 What is the average salary of employed graduates?
* 📍 Which education levels or fields of study show stronger employment outcomes?
* 📍 How does internship experience relate to employment status?

---

# 📊 EDA Measures and Formulas

<table>
<tr>
<th>Category</th>
<th>Measure</th>
<th>Formula</th>
<th>Description</th>
</tr>

<tr>
<td><b>KPI</b></td>
<td>Total Graduates</td>
<td><code>COUNTROWS(fact_graduate_employment)</code></td>
<td>Counts all graduate records</td>
</tr>

<tr>
<td><b>KPI</b></td>
<td>Employed Graduates</td>
<td><code>CALCULATE([Total Graduates], dim_employment_status[Employment_Status] = "Employed")</code></td>
<td>Counts employed graduates</td>
</tr>

<tr>
<td><b>KPI</b></td>
<td>Unemployed Graduates</td>
<td><code>CALCULATE([Total Graduates], dim_employment_status[Employment_Status] = "Unemployed")</code></td>
<td>Counts unemployed graduates</td>
</tr>

<tr>
<td><b>KPI</b></td>
<td>Continuing Education</td>
<td><code>CALCULATE([Total Graduates], dim_employment_status[Employment_Status] = "Continuing Education")</code></td>
<td>Counts graduates continuing education</td>
</tr>

<tr>
<td><b>KPI</b></td>
<td>Employment Rate</td>
<td><code>DIVIDE([Employed Graduates], [Total Graduates])</code></td>
<td>Calculates percentage of employed graduates</td>
</tr>

<tr>
<td><b>KPI</b></td>
<td>Unemployment Rate</td>
<td><code>DIVIDE([Unemployed Graduates], [Total Graduates])</code></td>
<td>Calculates percentage of unemployed graduates</td>
</tr>

<tr>
<td><b>KPI</b></td>
<td>Continuing Education Rate</td>
<td><code>DIVIDE([Continuing Education], [Total Graduates])</code></td>
<td>Calculates percentage of graduates continuing education</td>
</tr>

<tr>
<td><b>Summary</b></td>
<td>Average Salary</td>
<td><code>AVERAGE(fact_graduate_employment[Salary])</code></td>
<td>Calculates average salary of employed graduates</td>
</tr>

<tr>
<td><b>Summary</b></td>
<td>Total Salary</td>
<td><code>SUM(fact_graduate_employment[Salary])</code></td>
<td>Calculates total salary</td>
</tr>

<tr>
<td><b>Summary</b></td>
<td>Average GPA</td>
<td><code>AVERAGE(fact_graduate_employment[GPA])</code></td>
<td>Calculates average GPA</td>
</tr>

<tr>
<td><b>Summary</b></td>
<td>Average Age</td>
<td><code>AVERAGE(fact_graduate_employment[Age])</code></td>
<td>Calculates average age</td>
</tr>

<tr>
<td><b>Summary</b></td>
<td>Average Years Since Graduation</td>
<td><code>AVERAGE(fact_graduate_employment[Years_Since_Graduation])</code></td>
<td>Calculates average years since graduation</td>
</tr>

<tr>
<td><b>Summary</b></td>
<td>Internship Count</td>
<td><code>CALCULATE([Total Graduates], dim_internship[Internship_Experience] = "Yes")</code></td>
<td>Counts graduates with internship experience</td>
</tr>

<tr>
<td><b>Summary</b></td>
<td>Internship Rate</td>
<td><code>DIVIDE([Internship Count], [Total Graduates])</code></td>
<td>Calculates percentage of graduates with internship experience</td>
</tr>

<tr>
<td><b>Data Quality</b></td>
<td>GPA Above 4 Count</td>
<td><code>CALCULATE([Total Graduates], fact_graduate_employment[GPA_Above_4] = TRUE())</code></td>
<td>Counts records with GPA above 4</td>
</tr>

<tr>
<td><b>Data Quality</b></td>
<td>Grad Age Under 16 Count</td>
<td><code>CALCULATE([Total Graduates], fact_graduate_employment[Grad_Age_Under_16] = TRUE())</code></td>
<td>Counts records with estimated graduation age below 16</td>
</tr>

</table>

---

# 🖥️ Dashboard Wireframe Summary

| Dashboard Page            | Visual                 | Purpose                                                | Key Metrics                                      |
| :------------------------ | :--------------------- | :----------------------------------------------------- | :----------------------------------------------- |
| 📌 Overview Dashboard     | KPI Cards              | Display overall graduate employment statistics         | Total Graduates, Employment Rate, Average Salary |
| 📌 Employment Analysis    | Bar & Pie Charts       | Analyze employment distribution                        | Employed, Unemployed, Continuing Education       |
| 📌 Salary Insights        | Histogram & Box Plot   | Analyze salary distribution and outliers               | Average Salary, Salary Range                     |
| 📌 Academic Performance   | Scatter Plot           | Explore GPA vs Salary relationship                     | GPA, Salary                                      |
| 📌 Internship Impact      | Column Chart           | Compare employment outcomes with internship experience | Internship Rate, Employment Rate                 |
| 📌 Demographic Analysis   | Age Distribution Chart | Analyze graduate demographics                          | Average Age, Years Since Graduation              |
| 📌 Data Quality Dashboard | Tables & KPI Cards     | Monitor data quality issues                            | GPA Above 4, Grad Age Under 16                   |
| 📌 Filters Panel          | Slicers                | Enable interactive filtering                           | Education Level, Job Sector, University Ranking  |

---

# 📷 Dashboard Preview

## 1️⃣ Employment Overview Dashboard

![Employment Overview](./1%20-%20Employment%20Overview.png)

### Included Visuals

* ✅ KPI Cards
* ✅ Employment Distribution
* ✅ Graduate Overview Metrics

---

## 2️⃣ Salary Analysis Dashboard

![Salary Analysis](./2%20-%20Salary%20Analysis.png)

### Included Visuals

* ✅ Salary Distribution
* ✅ Average Salary by Sector
* ✅ Salary Trend Analysis

---

## 3️⃣ Graduate Profile Dashboard

![Graduate Profile](./3%20-%20Graduate%20Profile.png)

### Included Visuals

* ✅ Demographic Analysis
* ✅ GPA and Education Insights
* ✅ Internship and Employment Comparison

---

# 📊 DASH Framework Application

| DASH Pillar  | Application in Dashboard                                          | Explanation                                                                                                       |
| :----------- | :---------------------------------------------------------------- | :---------------------------------------------------------------------------------------------------------------- |
| 🎯 Decision  | Understand graduate employment and salary outcomes                | The dashboard helps answer which graduate characteristics are linked to employment and salary                     |
| 👥 Audience  | Students, educators, administrators, and career planning officers | The dashboard is designed for users who need to understand graduate employability                                 |
| 📈 Signal    | KPI cards and main charts                                         | Important metrics such as employment rate, average salary, internship rate, and total graduates are shown clearly |
| 🧭 Hierarchy | KPIs at the top, slicers on the left, charts in the middle        | The layout guides users from summary information to detailed analysis                                             |

---

# 📈 Dashboard Visuals

| Visual                                     | Chart Type        | Fields / Measures Used                                                                                 | Purpose                                                  |
| :----------------------------------------- | :---------------- | :----------------------------------------------------------------------------------------------------- | :------------------------------------------------------- |
| Total Graduates                            | KPI Card          | `Total Graduates`                                                                                      | Shows total number of graduates                          |
| Employment Rate                            | KPI Card          | `Employment Rate`                                                                                      | Shows percentage of employed graduates                   |
| Unemployment Rate                          | KPI Card          | `Unemployment Rate`                                                                                    | Shows percentage of unemployed graduates                 |
| Average Salary                             | KPI Card          | `Average Salary`                                                                                       | Shows average salary of employed graduates               |
| Internship Rate                            | KPI Card          | `Internship Rate`                                                                                      | Shows percentage of graduates with internship experience |
| Employment Status Distribution             | Donut Chart       | `dim_employment_status[Employment_Status]`, `Total Graduates`                                          | Shows employment status distribution                     |
| Employment Rate by Education Level         | Bar Chart         | `dim_education[Education_Level]`, `Employment Rate`                                                    | Compares employment rate by education level              |
| Total Graduates by Country                 | Bar Chart         | `dim_country_of_origin[Country_of_Origin]`, `Total Graduates`                                          | Shows graduate count by country                          |
| Average Salary by Job Sector               | Bar Chart         | `dim_jobs_sector[Job_Sector]`, `Average Salary`                                                        | Compares salary across job sectors                       |
| Average Salary by Field of Study           | Bar Chart         | `dim_field[Field_of_Study]`, `Average Salary`                                                          | Compares salary across academic fields                   |
| Average Salary by Region                   | Bar Chart         | `dim_region[Region_of_Study]`, `Average Salary`                                                        | Compares salary by study region                          |
| Average Salary by Years Since Graduation   | Line Chart        | `fact_graduate_employment[Years_Since_Graduation]`, `Average Salary`                                   | Shows salary trend based on years since graduation       |
| Employment Status by Internship Experience | Stacked Bar Chart | `dim_internship[Internship_Experience]`, `dim_employment_status[Employment_Status]`, `Total Graduates` | Compares employment status by internship experience      |

---

<div align="center">

### ⭐ Designed for Better GitHub Readability

</div>
