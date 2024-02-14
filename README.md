# **<p>Employee Attrition</p>**
![Screenshot 2024-02-13 130559](https://github.com/RobinLWilson/Project_4/assets/140012839/4f699f11-38ba-4ecd-986b-cf759c168a2a)


## Overview and Project Goals

Welcome to our Human Resources Attrition Analysis Project! This project focuses on utilizing data analytics to understand and analyze employee attrition within an organization. In other words, we want to understand why a person leaves a company because reducing turnover costs helps companies operate more efficiently. As a data analyst, our role is crucial in uncovering patterns, identifying key factors, and providing actionable insights to help the HR department make informed decisions.

## Questions the team hopes to answer

### Understand Attrition Trends
Analyze historical data to identify patterns and trends related to employee attrition. Determine if there are specific time periods, departments, or roles more prone to attrition.

### Identify Key Factors
Explore the various factors that contribute to attrition, such as job satisfaction, work-life balance, compensation, and career growth. Identify which factors have the most significant impact.

### Identify Future Attrition
Predict if an employee might leave in the future, giving HR and management time to create incentives for high impact employees to remain with the company.

## Project Structure
### 1. Data Collection
Data Source: 
https://www.kaggle.com/datasets/samruddhi4040/hr-data-analytics  
With over 1,400 data points and over 40 features, we were confident that even after cleaning the data we would have the minimum required 1,000 observations and 10 features.

Data Cleaning: 
- We downloaded the csv and conducted the cleaning process in Jupter notebook using python and pandas pd.  
- We dropped the following unnecessary columns:
    - 'DailyRate', 'HourlyRate', and 'MonthlyRate' because we will use the SalarySlab bins
    - 'EmployeeCount' and 'EmployeeNumber' because we will use EmpID
    - 'Over18' because all the employees were over 18
    - 'RelationshipSatisfaction' because there was not enough information around this variable
    - 'StandardHours' because all the employees had the same value of 80
    - 'Age' because we will use the AgeGroup bins

- Then we dropped the duplicate values which accounted for 7 data points. By using the ".count" feature, we identified there were nulls in the "YearsWithCurrentManager" variable.  After dropping the nulls, we verified no nulls remained by using "isna()".  
- Next we needed to start converting all object datatypes into numerical values for the machine learning.  To begin, we identified all the object datatypes ('EmpID', 'AgeGroup', 'Attrition', 'BusinessTravel', 'Department', 'EducationField', 'Gender', 'JobRole', 'MaritalStatus', 'SalarySlab', 'OverTime').  We then looked at each object variable using ".unique()" in order to:
    - correct inconsistent data (i.e. the 'Travel' column had 'Travel_Rarely' and 'Non-Travel')
    - analyze the data and determine if the data is Binary, Relational, or Independent.  All data except for "JobRole" and "Department" were quickly analyzed, but after discussion, we decided that these alone were independent data, but together they became relational.  So we created a new column ("Department_Role") of the merged data from "JobRole" and "Department." 
 The columns were categorized as follows:    
        - Binary: 'Attrition', 'Gender', 'OverTime'
        - Relational: 'AgeGroup', 'BusinessTravel', 'MaritalStatus', 'SalarySlab', 'Department_Role'
        - Independent: 'EducationField'
- At this point the data was exported into a csv file for the visualizations.
- We continued to prepare the data for the model by taking all the object variables from above and converting them to numberical values.
### 2. Exploratory Data Analysis (EDA)
Descriptive Statistics: Provide summary statistics to describe the overall attrition rate and relevant metrics.
Data Visualization: 
### 3. Feature Selection
Identify Features: Select the most relevant features that impact attrition.
Correlation Analysis: Analyze the correlation between different features.
### 4. Predictive Modeling
Model Selection: Choose appropriate models for predicting attrition.
Training and Testing: Split the data into training and testing sets.
Evaluation Metrics: Determine the evaluation metrics for assessing model performance.
### 5. Interpretation and Recommendations
Interpret Results: Explain the findings from the analysis and modeling.
Recommendations: Provide actionable recommendations for reducing attrition based on the insights gained.
Dependencies
List any dependencies or software required to run the code and reproduce the analysis. Include versions to ensure compatibility.

## How to Use
Provide instructions on how to run the analysis, including any necessary scripts or commands.


Develop predictive models to forecast potential attrition based on historical data. This will assist in proactively addressing issues and implementing retention strategies.

## Visualization: 
We used Tableu Public for the visualisation part. https://public.tableau.com/app/profile/janka.glenn/viz/Project_4_17074464774080/Dashboard3

## Process:
### Data Sourcing and Cleaning:

     
## Results
![Attrition_by_Dept_Job_Role](https://github.com/RobinLWilson/Project_4/assets/140012839/4a3c4757-d4d4-4d2b-97b4-7c7d280bd112)
![Travel_Effect](https://github.com/RobinLWilson/Project_4/assets/140012839/816bce40-d574-486e-99f2-b184010fad23)
![Distance_Effect](https://github.com/RobinLWilson/Project_4/assets/140012839/ae38573b-f3bf-4876-97b9-7ca09dc2fb4e)
![Hourly_Rate_Age](https://github.com/RobinLWilson/Project_4/assets/140012839/b21414a6-73b1-46fc-8ce5-a328587876e6)
![Job_Level_vs_Age_Group](https://github.com/RobinLWilson/Project_4/assets/140012839/c427e4ab-1290-4fe4-9eda-9c13ff7f3653)
![Linegraph_by_Age](https://github.com/RobinLWilson/Project_4/assets/140012839/e0628dd2-a893-40a4-a80f-a3a4ecc622ef)
![Monthly_Income](https://github.com/RobinLWilson/Project_4/assets/140012839/9110b69b-7560-442f-bacd-f692853c65fb)
![Travel_Effect](https://github.com/RobinLWilson/Project_4/assets/140012839/dad74dc4-5f52-47f5-b366-ebef868ae320)
![Work_Experience Dept](https://github.com/RobinLWilson/Project_4/assets/140012839/7d1ded02-8b6a-43c4-8aec-95edee119b6e)


## Summary

## What would we have done differently


## Data Analysts and Roles
- [Janka Glenn](https://github.com/jankaglenn)  ![Gmail Badge](https://img.shields.io/badge/Gmail-EA4335?logo=gmail&logoColor=fff&style=flat) ![LinkedIn Badge](https://img.shields.io/badge/LinkedIn-0A66C2?logo=linkedin&logoColor=fff&style=flat)
  - Data Cleaning
  - Tableau Dashboard
  - GitHub Pages

- [Robin Wilson](https://github.com/RobinLWilson)
  - Data Source Research
  - Data Cleaning
  - Machine Learning
  - GitHub Pages
  

## Software
###  Data Cleaning:
    - Python
    - Jupyter Notebook
    - Pandas library
    - Numpy
### Dashboard
    - Tableau Public
    - Microsoft PowerPoint
### Machine Learning
    - Google Colab
    - TensorFlow
    - Scikit-Learn
    - Logistic Regression
    - Decision Tree Classifier
### Background
![image](https://github.com/RobinLWilson/Project_4/assets/140012839/e5065d9d-e645-4932-9a9e-c52ad9ccc393)

## Predictive Modeling

![Python Badge](https://img.shields.io/badge/Python-3776AB?logo=python&logoColor=fff&style=flat)
 ![Tableau Badge](https://img.shields.io/badge/Tableau-E97627?logo=tableau&logoColor=fff&style=flat)
![Google Colab Badge](https://img.shields.io/badge/Google%20Colab-F9AB00?logo=googlecolab&logoColor=fff&style=flat)
![Jupyter Badge](https://img.shields.io/badge/Jupyter-F37626?logo=jupyter&logoColor=fff&style=flat)
![Microsoft Excel Badge](https://img.shields.io/badge/Microsoft%20Excel-217346?logo=microsoftexcel&logoColor=fff&style=flat)
![GitHub Badge](https://img.shields.io/badge/GitHub-181717?logo=github&logoColor=fff&style=flat)
![TensorFlow Badge](https://img.shields.io/badge/TensorFlow-FF6F00?logo=tensorflow&logoColor=fff&style=flat)
![scikit-learn Badge](https://img.shields.io/badge/scikit--learn-F7931E?logo=scikitlearn&logoColor=fff&style=flat)
![pandas Badge](https://img.shields.io/badge/pandas-150458?logo=pandas&logoColor=fff&style=flat)
![NumPy Badge](https://img.shields.io/badge/NumPy-013243?logo=numpy&logoColor=fff&style=flat)
![Microsoft PowerPoint Badge](https://img.shields.io/badge/Microsoft%20PowerPoint-B7472A?logo=microsoftpowerpoint&logoColor=fff&style=flat)
