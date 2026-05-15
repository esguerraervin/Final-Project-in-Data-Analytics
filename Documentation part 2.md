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

## EDA Framework: Pyramid Framework

This project follows the **Pyramid Framework**, where the analysis starts from basic metrics and builds up to key performance indicators and insights.

```text
                 OBJECTIVE
     Understand graduate employment outcomes

                    KPIs
 Employment Rate | Average Salary | Internship Rate

              SUPPORTING METRICS
 Total Graduates | Average GPA | Average Age
 Graduates by Country | Graduates by Education


## EDA Measures and Formulas

| Category | Measure | Formula | Description |
|---|---|---|---|
| KPI | **Total Graduates** | `COUNTROWS(fact_graduate_employment)` | Counts all graduate records |
| KPI | **Employed Graduates** | `CALCULATE([Total Graduates], dim_employment_status[Employment_Status] = "Employed")` | Counts employed graduates |
| KPI | **Unemployed Graduates** | `CALCULATE([Total Graduates], dim_employment_status[Employment_Status] = "Unemployed")` | Counts unemployed graduates |
| KPI | **Continuing Education** | `CALCULATE([Total Graduates], dim_employment_status[Employment_Status] = "Continuing Education")` | Counts graduates continuing education |
| KPI | **Employment Rate** | `DIVIDE([Employed Graduates], [Total Graduates])` | Calculates percentage of employed graduates |
| KPI | **Unemployment Rate** | `DIVIDE([Unemployed Graduates], [Total Graduates])` | Calculates percentage of unemployed graduates |
| KPI | **Continuing Education Rate** | `DIVIDE([Continuing Education], [Total Graduates])` | Calculates percentage of graduates continuing education |
| Summary | **Average Salary** | `AVERAGE(fact_graduate_employment[Salary])` | Calculates average salary of employed graduates |
| Summary | **Total Salary** | `SUM(fact_graduate_employment[Salary])` | Calculates total salary |
| Summary | **Average GPA** | `AVERAGE(fact_graduate_employment[GPA])` | Calculates average GPA |
| Summary | **Average Age** | `AVERAGE(fact_graduate_employment[Age])` | Calculates average age |
| Summary | **Average Years Since Graduation** | `AVERAGE(fact_graduate_employment[Years_Since_Graduation])` | Calculates average years since graduation |
| Summary | **Internship Count** | `CALCULATE([Total Graduates], dim_internship[Internship_Experience] = "Yes")` | Counts graduates with internship experience |
| Summary | **Internship Rate** | `DIVIDE([Internship Count], [Total Graduates])` | Calculates percentage of graduates with internship experience |
| Data Quality | **GPA Above 4 Count** | `CALCULATE([Total Graduates], fact_graduate_employment[GPA_Above_4] = TRUE())` | Counts records with GPA above 4 |
| Data Quality | **Grad Age Under 16 Count** | `CALCULATE([Total Graduates], fact_graduate_employment[Grad_Age_Under_16] = TRUE())` | Counts records with estimated graduation age below 16 |

## Dashboard Wireframe Documentation

| Dashboard Page | Section | Visual / Component | Fields or Measures Used | Purpose |
|---|---|---|---|---|
| Employment Overview | Header | Dashboard Title | International Graduate Employment Dashboard | Shows the main title of the dashboard |
| Employment Overview | Left Panel | Country of Origin Slicer | `dim_country_of_origin[Country_of_Origin]` | Filters dashboard by country |
| Employment Overview | Left Panel | Education Level Slicer | `dim_education[Education_Level]` | Filters dashboard by education level |
| Employment Overview | Left Panel | Field of Study Slicer | `dim_field[Field_of_Study]` | Filters dashboard by field of study |
| Employment Overview | Left Panel | Region of Study Slicer | `dim_region[Region_of_Study]` | Filters dashboard by study region |
| Employment Overview | Left Panel | Gender Slicer | `dim_gender[Gender]` | Filters dashboard by gender |
| Employment Overview | Left Panel | Visa Type Slicer | `dim_visa[Visa_Type]` | Filters dashboard by visa type |
| Employment Overview | Left Panel | Employment Status Slicer | `dim_employment_status[Employment_Status]` | Filters dashboard by employment status |
| Employment Overview | Top KPI Section | Total Graduates Card | `Total Graduates` | Displays total number of graduate records |
| Employment Overview | Top KPI Section | Employment Rate Card | `Employment Rate` | Displays percentage of employed graduates |
| Employment Overview | Top KPI Section | Unemployment Rate Card | `Unemployment Rate` | Displays percentage of unemployed graduates |
| Employment Overview | Top KPI Section | Average Salary Card | `Average Salary` | Displays average salary of employed graduates |
| Employment Overview | Top KPI Section | Internship Rate Card | `Internship Rate` | Displays percentage of graduates with internship experience |
| Employment Overview | Main Chart Section | Employment Status Distribution | `dim_employment_status[Employment_Status]`, `Total Graduates` | Shows distribution of employed, unemployed, and continuing education graduates |
| Employment Overview | Main Chart Section | Employment Rate by Education Level | `dim_education[Education_Level]`, `Employment Rate` | Compares employment rate by education level |
| Employment Overview | Bottom Chart Section | Total Graduates by Country of Origin | `dim_country_of_origin[Country_of_Origin]`, `Total Graduates` | Shows graduate count by country |
| Salary Analysis | Header | Dashboard Title | Salary Analysis Dashboard | Shows the page title |
| Salary Analysis | Top KPI Section | Average Salary Card | `Average Salary` | Shows average salary of employed graduates |
| Salary Analysis | Top KPI Section | Total Salary Card | `Total Salary` | Shows total salary amount |
| Salary Analysis | Main Chart Section | Average Salary by Job Sector | `dim_jobs_sector[Job_Sector]`, `Average Salary` | Compares average salary across job sectors |
| Salary Analysis | Main Chart Section | Average Salary by Field of Study | `dim_field[Field_of_Study]`, `Average Salary` | Compares average salary across fields of study |
| Salary Analysis | Main Chart Section | Average Salary by Region | `dim_region[Region_of_Study]`, `Average Salary` | Compares average salary by study region |
| Salary Analysis | Bottom Chart Section | Average Salary by Years Since Graduation | `fact_graduate_employment[Years_Since_Graduation]`, `Average Salary` | Shows salary trend based on years since graduation |
| Graduate Profile | Header | Dashboard Title | Graduate Profile Dashboard | Shows the page title |
| Graduate Profile | Top KPI Section | Average Age Card | `Average Age` | Shows average age of graduates |
| Graduate Profile | Top KPI Section | Average GPA Card | `Average GPA` | Shows average GPA of graduates |
| Graduate Profile | Main Chart Section | Graduates by Gender | `dim_gender[Gender]`, `Total Graduates` | Shows graduate count by gender |
| Graduate Profile | Main Chart Section | Graduates by Visa Type | `dim_visa[Visa_Type]`, `Total Graduates` | Shows graduate count by visa type |
| Graduate Profile | Main Chart Section | Graduates by Language Proficiency | `dim_language[Language_Proficiency]`, `Total Graduates` | Shows graduate count by language proficiency |
| Graduate Profile | Bottom Chart Section | Employment Status by Internship Experience | `dim_internship[Internship_Experience]`, `dim_employment_status[Employment_Status]`, `Total Graduates` | Compares employment status by internship experience |


