<div align="center">

# 📘 Documentation

### Data Quality Issues & Resolution Log

![Dataset](https://img.shields.io/badge/Dataset-dataset_transformed-blue)
![Rows](https://img.shields.io/badge/Rows-299,997-success)
![Status](https://img.shields.io/badge/Documentation-Completed-orange)

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

Documentation generated from transformation audit table

</div>
