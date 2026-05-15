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

| Measure Name | DAX Formula | Purpose |
|---|---|---|
| Total Graduates | `COUNTROWS(fact_graduate_employment)` | Counts all graduate records |
| Employed Graduates | `CALCULATE([Total Graduates], dim_employment_status[Employment_Status] = "Employed")` | Counts employed graduates |
| Unemployed Graduates | `CALCULATE([Total Graduates], dim_employment_status[Employment_Status] = "Unemployed")` | Counts unemployed graduates |
| Continuing Education | `CALCULATE([Total Graduates], dim_employment_status[Employment_Status] = "Continuing Education")` | Counts graduates continuing education |
| Employment Rate | `DIVIDE([Employed Graduates], [Total Graduates])` | Calculates the percentage of employed graduates |
| Unemployment Rate | `DIVIDE([Unemployed Graduates], [Total Graduates])` | Calculates the percentage of unemployed graduates |
| Continuing Education Rate | `DIVIDE([Continuing Education], [Total Graduates])` | Calculates the percentage of graduates continuing education |
| Average Salary | `AVERAGE(fact_graduate_employment[Salary])` | Calculates average salary of employed graduates |
| Total Salary | `SUM(fact_graduate_employment[Salary])` | Calculates total salary |
| Average GPA | `AVERAGE(fact_graduate_employment[GPA])` | Calculates average GPA |
| Average Age | `AVERAGE(fact_graduate_employment[Age])` | Calculates average age |
| Average Years Since Graduation | `AVERAGE(fact_graduate_employment[Years_Since_Graduation])` | Calculates average years since graduation |
| Internship Count | `CALCULATE([Total Graduates], dim_internship[Internship_Experience] = "Yes")` | Counts graduates with internship experience |
| Internship Rate | `DIVIDE([Internship Count], [Total Graduates])` | Calculates percentage of graduates with internship experience |
| GPA Above 4 Count | `CALCULATE([Total Graduates], fact_graduate_employment[GPA_Above_4] = TRUE())` | Counts records with GPA above 4 |
| Grad Age Under 16 Count | `CALCULATE([Total Graduates], fact_graduate_employment[Grad_Age_Under_16] = TRUE())` | Counts records with estimated graduation age below 16 |

