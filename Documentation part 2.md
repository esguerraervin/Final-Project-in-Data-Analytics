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

