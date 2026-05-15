# Exploratory Data Analysis (EDA)

## EDA Objective

The purpose of the Exploratory Data Analysis is to understand the employment outcomes of international graduates. The analysis focuses on employment status, salary, education level, field of study, internship experience, GPA, and other graduate profile factors.

EDA helps answer questions such as:

- How many graduates are employed, unemployed, or continuing education?
- What is the overall employment rate?
- What is the average salary of employed graduates?
- Which education levels or fields of study show stronger employment outcomes?
- How does internship experience relate to employment status?

---

---

## 📊 EDA Measures and Formulas

| Category | Measure | Formula | Description |
|:---|:---|:---|:---|
| KPI | Total Graduates | `COUNTROWS(fact_graduate_employment)` | Counts all graduate records |
| KPI | Employed Graduates | `CALCULATE([Total Graduates], dim_employment_status[Employment_Status] = "Employed")` | Counts employed graduates |
| KPI | Unemployed Graduates | `CALCULATE([Total Graduates], dim_employment_status[Employment_Status] = "Unemployed")` | Counts unemployed graduates |
| KPI | Continuing Education | `CALCULATE([Total Graduates], dim_employment_status[Employment_Status] = "Continuing Education")` | Counts graduates continuing education |
| KPI | Employment Rate | `DIVIDE([Employed Graduates], [Total Graduates])` | Calculates percentage of employed graduates |
| KPI | Unemployment Rate | `DIVIDE([Unemployed Graduates], [Total Graduates])` | Calculates percentage of unemployed graduates |
| KPI | Continuing Education Rate | `DIVIDE([Continuing Education], [Total Graduates])` | Calculates percentage of graduates continuing education |
| Summary | Average Salary | `AVERAGE(fact_graduate_employment[Salary])` | Calculates average salary of employed graduates |
| Summary | Total Salary | `SUM(fact_graduate_employment[Salary])` | Calculates total salary |
| Summary | Average GPA | `AVERAGE(fact_graduate_employment[GPA])` | Calculates average GPA |
| Summary | Average Age | `AVERAGE(fact_graduate_employment[Age])` | Calculates average age |
| Summary | Average Years Since Graduation | `AVERAGE(fact_graduate_employment[Years_Since_Graduation])` | Calculates average years since graduation |
| Summary | Internship Count | `CALCULATE([Total Graduates], dim_internship[Internship_Experience] = "Yes")` | Counts graduates with internship experience |
| Summary | Internship Rate | `DIVIDE([Internship Count], [Total Graduates])` | Calculates percentage of graduates with internship experience |
| Data Quality | GPA Above 4 Count | `CALCULATE([Total Graduates], fact_graduate_employment[GPA_Above_4] = TRUE())` | Counts records with GPA above 4 |
| Data Quality | Grad Age Under 16 Count | `CALCULATE([Total Graduates], fact_graduate_employment[Grad_Age_Under_16] = TRUE())` | Counts records with estimated graduation age below 16 |

---

## 🖥️ Dashboard Wireframe Summary

| Dashboard Page | Visual | Purpose | Key Metrics |
|:---|:---|:---|:---|
| Overview Dashboard | KPI Cards | Display overall graduate employment statistics | Total Graduates, Employment Rate, Average Salary |
| Employment Analysis | Bar & Pie Charts | Analyze employment distribution | Employed, Unemployed, Continuing Education |
| Salary Insights | Histogram & Box Plot | Analyze salary distribution and outliers | Average Salary, Salary Range |
| Academic Performance | Scatter Plot | Explore GPA vs Salary relationship | GPA, Salary |
| Internship Impact | Column Chart | Compare employment outcomes with internship experience | Internship Rate, Employment Rate |
| Demographic Analysis | Age Distribution Chart | Analyze graduate demographics | Average Age, Years Since Graduation |
| Data Quality Dashboard | Tables & KPI Cards | Monitor data quality issues | GPA Above 4, Grad Age Under 16 |
| Filters Panel | Slicers | Enable interactive filtering | Education Level, Job Sector, University Ranking |

---

---

## 🖥️ Dashboard Documentation

| Dashboard Element | Description | Purpose |
|:---|:---|:---|
| Dashboard Title | International Graduate Employment Analytics Dashboard | Identifies the main topic of the dashboard |
| Dashboard Tool | Power BI | Used for data visualization, KPI creation, filtering, and interactive reporting |
| Dashboard Framework | DASH Framework | Used to organize the dashboard based on decision, audience, signal, and hierarchy |
| Main Objective | Analyze international graduate employment outcomes | Helps understand employment status, salary, education, field of study, internship experience, and graduate profile |
| Target Audience | Students, educators, school administrators, and career planning officers | Helps users understand employment trends and support career-related decisions |
| Data Model | Star Schema | Connects one fact table to multiple dimension tables for better filtering and analysis |
| Fact Table | `fact_graduate_employment` | Stores graduate records, numeric measures, and foreign keys |
| Dimension Tables | Country, Education, Field, Language, Visa, Gender, Region, Internship, Employment Status, Job Sector | Stores descriptive categories used for slicers and chart grouping |
| Interactivity | Slicers and chart interactions | Allows users to filter and explore the data by country, education, field, region, gender, visa type, and employment status |

---

---

## 📊 DASH Framework Application

| DASH Pillar | Application in Dashboard | Explanation |
|:---|:---|:---|
| Decision | Understand graduate employment and salary outcomes | The dashboard helps answer which graduate characteristics are linked to employment and salary |
| Audience | Students, educators, administrators, and career planning officers | The dashboard is designed for users who need to understand graduate employability |
| Signal | KPI cards and main charts | Important metrics such as employment rate, average salary, internship rate, and total graduates are shown clearly |
| Hierarchy | KPIs at the top, slicers on the left, charts in the middle | The layout guides users from summary information to detailed analysis |

---

---

## 📈 Dashboard Visuals

| Visual | Chart Type | Fields / Measures Used | Purpose |
|:---|:---|:---|:---|
| Total Graduates | KPI Card | `Total Graduates` | Shows total number of graduates |
| Employment Rate | KPI Card | `Employment Rate` | Shows percentage of employed graduates |
| Unemployment Rate | KPI Card | `Unemployment Rate` | Shows percentage of unemployed graduates |
| Average Salary | KPI Card | `Average Salary` | Shows average salary of employed graduates |
| Internship Rate | KPI Card | `Internship Rate` | Shows percentage of graduates with internship experience |
| Employment Status Distribution | Donut Chart | `dim_employment_status[Employment_Status]`, `Total Graduates` | Shows employment status distribution |
| Employment Rate by Education Level | Bar Chart | `dim_education[Education_Level]`, `Employment Rate` | Compares employment rate by education level |
| Total Graduates by Country | Bar Chart | `dim_country_of_origin[Country_of_Origin]`, `Total Graduates` | Shows graduate count by country |
| Average Salary by Job Sector | Bar Chart | `dim_jobs_sector[Job_Sector]`, `Average Salary` | Compares salary across job sectors |
| Average Salary by Field of Study | Bar Chart | `dim_field[Field_of_Study]`, `Average Salary` | Compares salary across academic fields |
| Average Salary by Region | Bar Chart | `dim_region[Region_of_Study]`, `Average Salary` | Compares salary by study region |
| Average Salary by Years Since Graduation | Line Chart | `fact_graduate_employment[Years_Since_Graduation]`, `Average Salary` | Shows salary trend based on years since graduation |
| Employment Status by Internship Experience | Stacked Bar Chart | `dim_internship[Internship_Experience]`, `dim_employment_status[Employment_Status]`, `Total Graduates` | Compares employment status by internship experience |

---

