# International Graduate Employment Analytics Dashboard

## Project Overview

This project analyzes the employment outcomes of international graduates using Power BI. The dashboard focuses on graduate employment status, salary, education background, field of study, internship experience, visa type, region of study, and job sector.

The goal is to identify patterns that can help understand which factors are related to employment outcomes and salary differences among international graduates.

---

## Dataset

The dataset used in this project is the **International Graduates Employment Dataset** from Kaggle.

Dataset link: https://www.kaggle.com/datasets/quackquackrp/international-graduates-employment-dataset

Original dataset columns include:

- Country of Origin
- Education Level
- Field of Study
- Language Proficiency
- Visa Type
- Gender
- University Ranking
- Region of Study
- Age
- Years Since Graduation
- GPA
- Internship Experience
- Employment Status
- Salary
- Job Sector

---

<div align="center">

# 📘 Documentation

### ***Data Cleaning Process***
![Status](https://img.shields.io/badge/Data-Cleaning-orange)
![Dataset](https://img.shields.io/badge/Data-Transformed-blue)
![Rows](https://img.shields.io/badge/Rows-299,997-success)

</div>

---

## 📊 Documentation Summary

| table | column | issue | row count | magnitude | solvable? | resolution |
|:---|:---|:---|---:|---:|:---:|:---|
| dataset_transformed | all | exact duplicate rows | 3 | 0.001% | Y | removed duplicate records |
| dataset_transformed | job_sector | N/A values | 143,356 | 48% | Y | converted N/A values to Not Applicable |
| dataset_transformed | GPA | GPA values above 4.00 | 6,554 | 2.18% | Y | add custom column name as GPA_Above_4 using formula `[GPA]>4` |
| dataset_transformed | Age & Years_Since_Graduation | estimated graduation age below 16 | 9,869 | 3.29% | N | add custom column name as Grad_Age_Under_16 using formula `[Graduation_Age]<16` |
| dataset_transformed | Salary | salary is null for non-employed records | 143,356 | 47.79% | N | created values as unemployed as 0/1 |
| dataset_transformed | Internship_Experience | Yes/No categorical data | 299,997 | 100% | Y | encoded as 0/1 |
| dataset_transformed | Education_Level | ordinal category | 299,997 | 100% | Y | created custom column as Education_Level_Code |
| dataset_transformed | Language_Proficiency | ordinal category | 299,997 | 100% | Y | created custom column as Language_Proficiency_Code |
| dataset_transformed | University_Ranking | ordinal category | 299,997 | 100% | Y | created custom column as University_Ranking_Code |
| dataset_transformed | numeric_columns | different numeric scales | 299,997 |100%|Y| normalization Age, Years Since Graduation, GPA, and Salary |
| dataset_transformed | Text/Categorical Columns | spaces and unwanted non-printable characters |299,997|100%|Y| applied trim and clean functions |
| fact_table | all | no unique ID column |299,997|100%|Y| created Graduated_ID using index and added `GR-` prefix |

---

## ⚙ Formula Documentation

### Education_Level_Code

```powerquery
if [Education_Level]="Diploma" then 1
else if [Education_Level]="Bachelor's" then 2
else if [Education_Level]="Master's" then 3
else if [Education_Level]="PhD" then 4
else null
```

---

### Language_Proficiency_Code

```powerquery
if [Language_Proficiency]="Basic" then 1
else if [Language_Proficiency]="Intermediate" then 2
else if [Language_Proficiency]="Advanced" then 3
else if [Language_Proficiency]="Fluent" then 4
else null
```

---

### University_Ranking_Code

```powerquery
if [University_Ranking]="Low" then 1
else if [University_Ranking]="Medium" then 2
else if [University_Ranking]="High" then 3
else null
```

---

<div align="center">

</div>

## Data Model

The project uses a **star schema** because it is simple, readable, and suitable for Power BI dashboards.

### Fact Table

`fact_graduate_employment`

This table contains the main graduate records, numeric values, measures, and foreign keys connected to dimension tables.

Main columns:

- Graduate_ID
- Country_ID
- Education_ID
- Field_ID
- Language_ID
- Visa_ID
- Gender_ID
- UniversityRanking_ID
- Region_ID
- Internship_ID
- EmploymentStatus_ID
- JobSector_ID
- Age
- Years_Since_Graduation
- Graduation_Age
- GPA
- Salary
- Age_Normalized
- GPA_Normalized
- Salary_Normalized
- GPA_Above_4
- Grad_Age_Under_16

### Dimension Tables

| Dimension Table | Description |
|---|---|
| `dim_country_of_origin` | Stores country of origin |
| `dim_education` | Stores education level and education code |
| `dim_field` | Stores field of study |
| `dim_language` | Stores language proficiency and language code |
| `dim_visa` | Stores visa type |
| `dim_gender` | Stores gender |
| `dim_university_ranking` | Stores university ranking and ranking code |
| `dim_region` | Stores region of study |
| `dim_internship` | Stores internship experience |
| `dim_employment_status` | Stores employment status |
| `dim_jobs_sector` | Stores job sector |

### Star Schema

```mermaid
erDiagram
    fact_graduate_employment }o--|| dim_country_of_origin : Country_ID
    fact_graduate_employment }o--|| dim_education : Education_ID
    fact_graduate_employment }o--|| dim_field : Field_ID
    fact_graduate_employment }o--|| dim_language : Language_ID
    fact_graduate_employment }o--|| dim_visa : Visa_ID
    fact_graduate_employment }o--|| dim_gender : Gender_ID
    fact_graduate_employment }o--|| dim_university_ranking : UniversityRanking_ID
    fact_graduate_employment }o--|| dim_region : Region_ID
    fact_graduate_employment }o--|| dim_internship : Internship_ID
    fact_graduate_employment }o--|| dim_employment_status : EmploymentStatus_ID
    fact_graduate_employment }o--|| dim_jobs_sector : JobSector_ID



---
# Exploratory Data Analysis (EDA)

## EDA Objective

| Section | Description |
|---|---|
| Objective | Analyze international graduate employment outcomes using Power BI |
| Main Focus | Employment status, salary, education level, field of study, internship experience, GPA, and graduate profile |
| Purpose | Identify patterns that explain employment outcomes and salary differences |
| Tool Used | Power BI |

---

## Pyramid Framework

| Pyramid Level | Description | Applied In This Project |
|---|---|---|
| Top Level | Main objective | Understand international graduate employment outcomes |
| Middle Level | Key metrics and KPIs | Employment Rate, Unemployment Rate, Average Salary, Average GPA, Internship Rate |
| Bottom Level | Supporting metrics | Total Graduates, Employed Graduates, Unemployed Graduates, Continuing Education, Average Age |

---

## Key Metrics and DAX Measures

| Measure Name | DAX Formula | Purpose |
|---|---|---|
| Total Graduates | `COUNTROWS(fact_graduate_employment)` | Counts all graduate records |
| Employed Graduates | `CALCULATE([Total Graduates], dim_employment_status[Employment_Status] = "Employed")` | Counts graduates who are employed |
| Unemployed Graduates | `CALCULATE([Total Graduates], dim_employment_status[Employment_Status] = "Unemployed")` | Counts graduates who are unemployed |
| Continuing Education | `CALCULATE([Total Graduates], dim_employment_status[Employment_Status] = "Continuing Education")` | Counts graduates who are continuing education |
| Employment Rate | `DIVIDE([Employed Graduates], [Total Graduates])` | Calculates the percentage of employed graduates |
| Unemployment Rate | `DIVIDE([Unemployed Graduates], [Total Graduates])` | Calculates the percentage of unemployed graduates |
| Continuing Education Rate | `DIVIDE([Continuing Education], [Total Graduates])` | Calculates the percentage of graduates continuing education |
| Average Salary | `AVERAGE(fact_graduate_employment[Salary])` | Calculates the average salary of employed graduates |
| Total Salary | `SUM(fact_graduate_employment[Salary])` | Calculates the total salary of employed graduates |
| Average GPA | `AVERAGE(fact_graduate_employment[GPA])` | Calculates the average GPA |
| Average Age | `AVERAGE(fact_graduate_employment[Age])` | Calculates the average age |
| Average Years Since Graduation | `AVERAGE(fact_graduate_employment[Years_Since_Graduation])` | Calculates the average years since graduation |
| Internship Count | `CALCULATE([Total Graduates], dim_internship[Internship_Experience] = "Yes")` | Counts graduates with internship experience |
| Internship Rate | `DIVIDE([Internship Count], [Total Graduates])` | Calculates the percentage of graduates with internship experience |
| GPA Above 4 Count | `CALCULATE([Total Graduates], fact_graduate_employment[GPA_Above_4] = TRUE())` | Counts records with GPA above 4 |
| Grad Age Under 16 Count | `CALCULATE([Total Graduates], fact_graduate_employment[Grad_Age_Under_16] = TRUE())` | Counts records with estimated graduation age below 16 |

---
