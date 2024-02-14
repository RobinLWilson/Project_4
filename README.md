# **<p>Employee Attrition</p>**


## Overview and Project Goals

Welcome to our Human Resources Attrition Analysis Project! This project focuses on utilizing data analytics to understand and analyze employee attrition within an organization. In other words, we want to understand why a person leaves a company because reducing turnover costs helps companies operate more efficiently. As data analysts, our role is crucial in identifying key factors, and providing actionable insights to help the HR department make informed decisions.

## Questions the team hopes to answer

### Identify Key Contributors to Attrition
We want to explore the various factors that contribute to attrition, such as business travel, job roles, age, compensation, etc and identify which factors have the most significant impact.

### Identify Future Attrition
Ideally we want to predict if an employee is going to leave in the future.  This gives HR and management time to create incentives for high impact employees to remain with the company, thus reducing turnover costs.

## Project Structure
### 1. Data Collection
Data Source: 
https://www.kaggle.com/datasets/samruddhi4040/hr-data-analytics 

With over 1,400 data points and over 40 features, we were confident that even after cleaning the data we would have the minimum required 1,000 observations and 10 features.

Data Cleaning: 
- We downloaded the csv and conducted the cleaning process in Jupter notebook using python and pandas pd.  
- We dropped the following unnecessary columns:
    - 'EmployeeCount' and 'EmpID' because we will use 'EmployeeNumber'
    - 'Over18' because all the employees were over 18
    - 'StandardHours' because all the employees had the same value of 80

- Then we set the index of the DataFrame to be 'EmployeeNumber'
- Then we dropped the duplicate values which accounted for 7 data points. By using the ".count" feature, we identified there were nulls in the "YearsWithCurrentManager" variable.  After dropping the nulls, we verified no nulls remained by using "isna()".  
- Next we needed to start converting all object datatypes into numerical values for the machine learning.  To begin, we identified all the object datatypes ('AgeGroup', 'Attrition', 'BusinessTravel', 'Department', 'EducationField', 'Gender', 'JobRole', 'MaritalStatus', 'SalarySlab', 'OverTime').  We then looked at each object variable using ".unique()" in order to:
    - correct inconsistent data (i.e. the 'Travel' column had 'Travel_Rarely' and 'Non-Travel')
    - analyze the data and determine if the data is Binary, Relational/Ordinal, or Independent.  All data except for "JobRole" and "Department" were quickly analyzed; after discussion, we decided that these alone were independent data, but together they became relational.  So we created a new column ("Department_Role") of the merged data from "JobRole" and "Department." 
 The features were categorized as follows:    
        - Binary: 'Attrition', 'Gender', 'OverTime'
        - Relational/Ordinal: 'AgeGroup', 'BusinessTravel', 'MaritalStatus', 'SalarySlab', 'Department_Role'
        - Independent: 'EducationField'
- At this point the data was exported into a csv file for the visualizations.

- We continued to prepare the data for the statistical analysis & model by taking all the object variables from above and converting them to numberical values.
- Converting the Binary data:

  <img width="469" alt="image" src="https://github.com/RobinLWilson/Project_4/assets/139357402/c4e02098-24ee-46ea-8b18-cc8e188bae9d">
  
- Converting the Relational/Ordinal data: We used mapping to assign the values in 'AgeGroup', 'BusinessTravel', 'MaritalStatus', 'SalarySlab'.
  
  <img width="433" alt="image" src="https://github.com/RobinLWilson/Project_4/assets/139357402/d14b8bc2-8f55-4d4e-b09c-e469ae255117">

  For the 'Department_Role', the following additional steps were taken:
- The 'Department_Role' column was copied three times and renamed "Sales", "Human_Resources", and "Research_&_Development" respectively.  Then the columns were filtered on the data that began with the column's department name and all the other cells with filled with "None."  Then the remaining appropriate values were mapped and the "None" values were filled with a "NaN_placeholder."  Finally the NaN's were replaced with 0 and the entire column datatype was converted to an integer.
- 
   <img width="598" alt="image" src="https://github.com/RobinLWilson/Project_4/assets/139357402/47cf6c5a-454d-4e3b-b515-82027377bf01">
   <img width="806" alt="image" src="https://github.com/RobinLWilson/Project_4/assets/139357402/73f461da-3bd6-4785-810a-0fbad91432b2">
   
- Converting the Indepedent data: Before using 'get_dummies' to convert 'EducationField', we dropped the final unnecessary columns: 'Department_Role', 'JobRole', 'Department'.  Then after verifying that 'EducationField' was the final object datatype, we applied 'get_dummies' to the dataframe.
- Finally we verified that all the object datatypes had been changed and that there were no nulls remaining in the data.

### 2. Exploratory Data Analysis (EDA) &  Data Visualizations
We conducted the Chi2 test on Attrition and each feature to determine the statistically significant variables.  The following table details our results:

<img width="442" alt="image" src="https://github.com/RobinLWilson/Project_4/assets/139357402/098c3408-76a8-46f9-9c4e-b7e97a276e2c">

This was done to drive and focus our visualizations (created in Tableau Public) that shed light on pertinent workforce realities. https://public.tableau.com/app/profile/janka.glenn/viz/Project_4_17074464774080/Dashboard  

The organization currently comprises 1473 employees, exhibiting an attrition rate of 16% with an average employee age of 37.
Our analysis indicates a notable correlation between attrition and frequent business travel. However, no statistically significant association was observed between attrition and performance rating, as evidenced by a Chi-square statistic of 0.0004802863597185681 and a P-value of 0.9825154111364345.
Furthermore, there is a substantial link between attrition and age groups. Employees within the 26-35 age range exhibit a higher propensity to leave, suggesting a potential association with entry-level positions.
Our findings also reveal a significant association between attrition and the Research & Development department, as indicated by a Chi-square statistic of 1.123879905034171 and a P-value of 0.28908454133190753. Conversely, no significant correlation was identified between attrition and gender.
Moreover, attrition is notably associated with salary slabs, with entry-level positions posing a higher risk than senior roles. This association follows a descending trend, indicating that higher salaries are associated with a smaller likelihood of attrition.
Specifically, the sales department is experiencing higher attrition rates. Additionally, our analysis highlights that overtime is not favorable in terms of attrition. These insights provide valuable information for strategic workforce planning and retention efforts within the organization.

![Dashboard](https://github.com/RobinLWilson/Project_4/assets/140012839/d41f6485-8a7c-4e2d-84cb-a3f7dd29d3ff)

![Overal_Attrition](https://github.com/RobinLWilson/Project_4/assets/140012839/83ea9af2-6d15-4e32-9fba-136775ab54e9)
![Attrition_by_Dept_vs_Job_Role](https://github.com/RobinLWilson/Project_4/assets/140012839/5e6d766a-24e9-4604-8d14-0f7501f60b9a)
![Attrition_by_Education_Field](https://github.com/RobinLWilson/Project_4/assets/140012839/02a61c04-35c4-4481-a591-49370b71d808)
![Attrition_by_Salary_Group](https://github.com/RobinLWilson/Project_4/assets/140012839/8c5501b7-9b1e-44bf-abf5-83066d6588ee)
![Commute](https://github.com/RobinLWilson/Project_4/assets/140012839/0f886f9f-5765-45cc-a668-74892f8311c6)
![Hourly_Rate_vs_Age](https://github.com/RobinLWilson/Project_4/assets/140012839/6f8bc2bf-c46a-42b2-bb18-095ee947e921)
![Job_Involvement_vs_Age_Group](https://github.com/RobinLWilson/Project_4/assets/140012839/f4cfd1ad-6fcc-4958-9e43-e5ff18871e1f)
![Job_Level_vs_Age_Group](https://github.com/RobinLWilson/Project_4/assets/140012839/202ff760-8b7e-422f-aeda-6fc4f9716186)
![Monthly_Income](https://github.com/RobinLWilson/Project_4/assets/140012839/8458281f-27e4-4e48-84e3-b134bcf48218)
![Travel_Effect](https://github.com/RobinLWilson/Project_4/assets/140012839/560a77be-04b3-4502-8c58-31b865126a3f)
![Training_Hours](https://github.com/RobinLWilson/Project_4/assets/140012839/a5b5afae-ed7d-43f1-bf5f-257b7ae4e3c4)
![Over_Time](https://github.com/RobinLWilson/Project_4/assets/140012839/b4a88758-2f80-4c31-a280-76e2293d782c)

### 3. Predictive Modeling and Results
Model Selection: Choose appropriate models for predicting attrition.
Training and Testing: Split the data into training and testing sets.
Evaluation Metrics: Determine the evaluation metrics for assessing model performance.

Interpret Results: Explain the findings from the analysis and modeling.
Logistic Regression with Min/Max Scaler:
<img width="327" alt="image" src="https://github.com/RobinLWilson/Project_4/assets/139357402/04028763-1930-456d-b78a-c417f4e10feb">

Logistic Regression with Standard Scaler:
<img width="323" alt="image" src="https://github.com/RobinLWilson/Project_4/assets/139357402/77c1e397-1982-4a3c-96c1-a9634b691877">

Modeling Results After Each Optimization:
<img width="736" alt="image" src="https://github.com/RobinLWilson/Project_4/assets/139357402/738b50e3-6298-41bb-9f94-6427b8863ee4">

### 4. Recommendations
Recommendations: Provide actionable recommendations for reducing attrition based on the insights gained.
Dependencies
List any dependencies or software required to run the code and reproduce the analysis. Include versions to ensure compatibility.



Develop predictive models to forecast potential attrition based on historical data. This will assist in proactively addressing issues and implementing retention strategies.


### 5. Future Research
This report presents a comprehensive analysis of key employee-related features within our dataset, utilizing chi-square statistics and associated p-values to establish statistical significance. The following features have demonstrated notable statistical associations:

- EnvironmentSatisfaction
- JobSatisfaction
- MaritalStatus
- StockOptionLevel
- WorkLifeBalance
- YearsAtCompany
- YearsInCurrentRole
  
Recommendations for Future Analysis:

Given the observed statistical significance, it is imperative to conduct a more in-depth analysis into the background of the data. The following areas are recommended for further exploration:

Covid-19 Impact:

Investigate the potential influence of the Covid-19 pandemic on employee satisfaction and organizational dynamics. Assess how external factors may have contributed to the observed statistical relationships.

Geographic Influence:

Explore regional variations within the dataset to identify potential correlations between employee features and the geographic location of the company. Consider cultural, economic, and social factors that may impact employee satisfaction.
Company Reputation:

Analyze the dataset in relation to the reputation of the company. Assess whether there are discernible patterns indicating a correlation between employee features and the overall perception of the organization.
Conclusion:

The findings from the chi-square analysis highlight significant associations within key employee-related features. To gain a comprehensive understanding, it is recommended to delve deeper into the background of the data, considering external factors such as Covid-19, geographic location, and company reputation. This nuanced analysis will provide valuable insights for strategic decision-making and workforce management.

## Data Analysts and Roles
- [Janka Glenn](https://github.com/jankaglenn)  ![Gmail Badge][(https://img.shields.io/badge/Gmail-EA4335?logo=gmail&logoColor=fff&style=flat)](mailto:jankaglenn@gmail.com) ![LinkedIn Badge][(https://img.shields.io/badge/LinkedIn-0A66C2?logo=linkedin&logoColor=fff&style=flat)](https://www.linkedin.com/in/janka-glenn-243934230/)
  - Data Cleaning
  - Tableau Dashboard
  - Visualizations
  - GitHub README

- [Robin Wilson](https://github.com/RobinLWilson) ![Gmail Badge][(https://img.shields.io/badge/Gmail-EA4335?logo=gmail&logoColor=fff&style=flat)](mailto:wilson.robin.leigh@gmail.com) ![LinkedIn Badge][(https://img.shields.io/badge/LinkedIn-0A66C2?logo=linkedin&logoColor=fff&style=flat)](https://www.linkedin.com/in/robin-wilson-0361ba283/)

[Robin Wilson](https://github.com/RobinLWilson) 
[![Gmail Badge](https://img.shields.io/badge/Gmail-EA4335?logo=gmail&logoColor=fff&style=flat)](mailto:wilson.robin.leigh@gmail.com) 
[![LinkedIn Badge](https://img.shields.io/badge/LinkedIn-0A66C2?logo=linkedin&logoColor=fff&style=flat)](https://www.linkedin.com/in/robin-wilson-0361ba283/) 
  - Data Source Research
  - Data Cleaning
  - Machine Learning
  - GitHub README
  

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
