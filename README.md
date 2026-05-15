



Pasted markdown(2).md
File
just add a design on this one enhance for readability dont add any text or value (readme file in github)


Pasted markdown(3).md
File
then this one also 

<div align="center">

# 🎓 International Graduate Employment Analytics Dashboard

### 📊 Data Analytics Final Project

![Power BI](https://img.shields.io/badge/Visualization-Power%20BI-yellow?style=for-the-badge)
![Dataset](https://img.shields.io/badge/Dataset-Kaggle-blue?style=for-the-badge)
![Status](https://img.shields.io/badge/Project-Completed-success?style=for-the-badge)

</div>

---

# 📖 Project Overview

This project analyzes the employment outcomes of international graduates using Power BI. The dashboard focuses on graduate employment status, salary, education background, field of study, internship experience, visa type, region of study, and job sector.

The goal is to identify patterns that can help understand which factors are related to employment outcomes and salary differences among international graduates.

---

# 📂 Dataset

<div align="center">

## 🌍 International Graduates Employment Dataset

</div>

The dataset used in this project is the **International Graduates Employment Dataset** from Kaggle.

🔗 Dataset Link:  
https://www.kaggle.com/datasets/quackquackrp/international-graduates-employment-dataset

---

## 📑 Original Dataset Columns

- 🌍 Country of Origin
- 🎓 Education Level
- 📚 Field of Study
- 🗣️ Language Proficiency
- 🛂 Visa Type
- 👤 Gender
- 🏫 University Ranking
- 🌎 Region of Study
- 🎂 Age
- ⏳ Years Since Graduation
- 📈 GPA
- 💼 Internship Experience
- 📊 Employment Status
- 💰 Salary
- 🏢 Job Sector

---

<div align="center">

# 📘 Documentation

### ***Data Cleaning Process***

![Status](https://img.shields.io/badge/Data-Cleaning-orange?style=for-the-badge)
![Dataset](https://img.shields.io/badge/Data-Transformed-blue?style=for-the-badge)
![Rows](https://img.shields.io/badge/Rows-299,997-success?style=for-the-badge)

</div>

---

# 📊 Documentation Summary

| Table | Column | Issue | Row Count | Magnitude | Solvable? | Resolution |
|:---|:---|---|---:|---:|:---:|:---|
| `dataset_transformed` | all | exact duplicate rows | 3 | 0.001% | ✅ | removed duplicate records |
| `dataset_transformed` | job_sector | N/A values | 143,356 | 48% | ✅ | converted N/A values to Not Applicable |
| `dataset_transformed` | GPA | GPA values above 4.00 | 6,554 | 2.18% | ✅ | add custom column name as `GPA_Above_4` using formula `[GPA]>4` |
| `dataset_transformed` | Age & Years_Since_Graduation | estimated graduation age below 16 | 9,869 | 3.29% | ❌ | add custom column name as `Grad_Age_Under_16` using formula `[Graduation_Age]<16` |
| `dataset_transformed` | Salary | salary is null for non-employed records | 143,356 | 47.79% | ❌ | created values as unemployed as 0/1 |
| `dataset_transformed` | Internship_Experience | Yes/No categorical data | 299,997 | 100% | ✅ | encoded as 0/1 |
| `dataset_transformed` | Education_Level | ordinal category | 299,997 | 100% | ✅ | created custom column as `Education_Level_Code` |
| `dataset_transformed` | Language_Proficiency | ordinal category | 299,997 | 100% | ✅ | created custom column as `Language_Proficiency_Code` |
| `dataset_transformed` | University_Ranking | ordinal category | 299,997 | 100% | ✅ | created custom column as `University_Ranking_Code` |
| `dataset_transformed` | numeric_columns | different numeric scales | 299,997 | 100% | ✅ | normalization Age, Years Since Graduation, GPA, and Salary |
| `dataset_transformed` | Text/Categorical Columns | spaces and unwanted non-printable characters | 299,997 | 100% | ✅ | applied trim and clean functions |
| `fact_table` | all | no unique ID column | 299,997 | 100% | ✅ | created `Graduate_ID` using index and added `GR-` prefix |

---

# ⚙️ Formula Documentation

## 🎓 Education_Level_Code

```powerquery
if [Education_Level]="Diploma" then 1
else if [Education_Level]="Bachelor's" then 2
else if [Education_Level]="Master's" then 3
else if [Education_Level]="PhD" then 4
else null
🗣️ Language_Proficiency_Code
if [Language_Proficiency]="Basic" then 1
else if [Language_Proficiency]="Intermediate" then 2
else if [Language_Proficiency]="Advanced" then 3
else if [Language_Proficiency]="Fluent" then 4
else null
🏫 University_Ranking_Code
if [University_Ranking]="Low" then 1
else if [University_Ranking]="Medium" then 2
else if [University_Ranking]="High" then 3
else null
🗄️ Data Model
The project uses a Star Schema because it is simple, readable, and suitable for Power BI dashboards.

📌 Fact Table
fact_graduate_employment
This table contains the main graduate records, numeric values, measures, and foreign keys connected to dimension tables.

Main Columns
Graduate_ID

Country_ID

Education_ID

Field_ID

Language_ID

Visa_ID

Gender_ID

UniversityRanking_ID

Region_ID

Internship_ID

EmploymentStatus_ID

JobSector_ID

Age

Years_Since_Graduation

Graduation_Age

GPA

Salary

Age_Normalized

GPA_Normalized

Salary_Normalized

GPA_Above_4

Grad_Age_Under_16

🧩 Dimension Tables
Dimension Table	Description
dim_country_of_origin	Stores country of origin
dim_education	Stores education level and education code
dim_field	Stores field of study
dim_language	Stores language proficiency and language code
dim_visa	Stores visa type
dim_gender	Stores gender
dim_university_ranking	Stores university ranking and ranking code
dim_region	Stores region of study
dim_internship	Stores internship experience
dim_employment_status	Stores employment status
dim_jobs_sector	Stores job sector
⭐ Star Schema



<div align="center">
⭐ Enhanced GitHub README Design
</div> ```
Source reference: 



# Final Project in Data Analytics

## Files

| File | Description |
|---|---|
| [Dataset](dataset.csv) | Dataset used for the project |
| [Documentation Part 1](Documentation%20Part%201.md) | Data preprocessing, CLEAN Framework, transformed data, and data model |
| [Documentation Part 2](Documentation%20part%202.md) | Exploratory Data Analysis, measures, dashboard wireframe, and dashboard design |
| [Insights and Recommendation](Insights%20and%20Recommendation.md) | Data-driven insights, recommendations, and real-world interpretation |
| [Wireframe 1 - Employment Overview](1%20-%20Employment%20Overview.png) | Wireframe/dashboard page for employment overview |
| [Wireframe 2 - Salary Analysis](2%20-%20Salary%20Analysis.png) | Wireframe/dashboard page for salary analysis |
| [Wireframe 3 - Graduate Profile](3%20-%20Graduate%20Profile.png) | Wireframe/dashboard page for graduate profile |
| [Final Power BI Dashboard](Final%20Power%20BI%20Dashboard%20(Group%202%20-%20C302).pbix) | Final Power BI dashboard file for Group 2 - C302 | (lastly this one)

<div align="center">

# 🎓 Final Project in Data Analytics

![Power BI](https://img.shields.io/badge/Visualization-Power%20BI-yellow?style=for-the-badge)
![Project](https://img.shields.io/badge/Project-Final%20Analytics-blue?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)

</div>

---

# 📂 Project Files

<table>
<tr>
<th>📄 File</th>
<th>📝 Description</th>
</tr>

<tr>
<td><a href="dataset.csv">📊 Dataset</a></td>
<td>Dataset used for the project</td>
</tr>

<tr>
<td><a href="Documentation%20Part%201.md">📘 Documentation Part 1</a></td>
<td>Data preprocessing, CLEAN Framework, transformed data, and data model</td>
</tr>

<tr>
<td><a href="Documentation%20part%202.md">📗 Documentation Part 2</a></td>
<td>Exploratory Data Analysis, measures, dashboard wireframe, and dashboard design</td>
</tr>

<tr>
<td><a href="Insights%20and%20Recommendation.md">📈 Insights and Recommendation</a></td>
<td>Data-driven insights, recommendations, and real-world interpretation</td>
</tr>

<tr>
<td><a href="1%20-%20Employment%20Overview.png">🖼️ Wireframe 1 - Employment Overview</a></td>
<td>Wireframe/dashboard page for employment overview</td>
</tr>

<tr>
<td><a href="2%20-%20Salary%20Analysis.png">🖼️ Wireframe 2 - Salary Analysis</a></td>
<td>Wireframe/dashboard page for salary analysis</td>
</tr>

<tr>
<td><a href="3%20-%20Graduate%20Profile.png">🖼️ Wireframe 3 - Graduate Profile</a></td>
<td>Wireframe/dashboard page for graduate profile</td>
</tr>

<tr>
<td><a href="Final%20Power%20BI%20Dashboard%20(Group%202%20-%20C302).pbix">⚡ Final Power BI Dashboard</a></td>
<td>Final Power BI dashboard file for Group 2 - C302</td>
</tr>

</table>

---

<div align="center">

### ⭐ Enhanced GitHub README File Structure

</div>

<div align="center">

# 🎓 Final Project in Data Analytics

![Power BI](https://img.shields.io/badge/Visualization-Power%20BI-yellow?style=for-the-badge)
![Project](https://img.shields.io/badge/Project-Final%20Analytics-blue?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)

</div>

---

# 📂 Project Files

<table>
<tr>
<th>📄 File</th>
<th>📝 Description</th>
</tr>

<tr>
<td><a href="dataset.csv">📊 Dataset</a></td>
<td>Dataset used for the project</td>
</tr>

<tr>
<td><a href="Documentation%20Part%201.md">📘 Documentation Part 1</a></td>
<td>Data preprocessing, CLEAN Framework, transformed data, and data model</td>
</tr>

<tr>
<td><a href="Documentation%20part%202.md">📗 Documentation Part 2</a></td>
<td>Exploratory Data Analysis, measures, dashboard wireframe, and dashboard design</td>
</tr>

<tr>
<td><a href="Insights%20and%20Recommendation.md">📈 Insights and Recommendation</a></td>
<td>Data-driven insights, recommendations, and real-world interpretation</td>
</tr>

<tr>
<td><a href="Final%20Power%20BI%20Dashboard%20(Group%202%20-%20C302).pbix">⚡ Final Power BI Dashboard</a></td>
<td>Final Power BI dashboard file for Group 2 (C302)</td>
</tr>

</table>

---

<div align="center">


</div> (add here by Ervin Esguerra, Hoshea Balajdia, Nica Dizon, Joan Gutierez, and Patrick Paragas)

<div align="center">

# 🎓 Final Project in Data Analytics

![Power BI](https://img.shields.io/badge/Visualization-Power%20BI-yellow?style=for-the-badge)
![Project](https://img.shields.io/badge/Project-Final%20Analytics-blue?style=for-the-badge)
![Status](https://img.shields.io/badge/Status-Completed-success?style=for-the-badge)

</div>

---

# 📂 Project Files

<table>
<tr>
<th>📄 File</th>
<th>📝 Description</th>
</tr>

<tr>
<td><a href="dataset.csv">📊 Dataset</a></td>
<td>Dataset used for the project</td>
</tr>

<tr>
<td><a href="Final%20Power%20BI%20Dashboard%20(Group%202%20-%20C302).pbix">⚡ Final Power BI Dashboard</a></td>
<td>Final Power BI dashboard file for Group 2 (C302)</td>
</tr>

</table>

---

<div align="center">

## 👥 Project Members

### ✨ Ervin Esguerra  
### ✨ Hoshea Balajdia  
### ✨ Nica Dizon  
### ✨ Joan Gutierez  
### ✨ Patrick Paragas  

</div>

