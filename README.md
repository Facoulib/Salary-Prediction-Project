# Salary Prediction Project

The objective of the project is to examine a set of job postings with their corresponding salaries and then predict salaries for a new set of job postings.
This project and its reuslts can have various applications such as:
- helping companies and Human Resources departments to estimate the appropriate salaries of their future employees. 
- allowing job seekers to negotiate a suitable salary with knowledge of different salary averages.
- assisting federal and state governments to evaluate the current salaries trend in the job market.


# Given Datasets

train_features.csv: Each row represents an observation for each individual job posting. The "jobId" column is unique to each job posting and the other columns are the different features of the job postings. The file has eight(8) columns.

train-salaries.csv: Each row is a unique job posting with its corresponding salary. The file contains two (2) columns. The file is combined with train_features.csv to train the machine learning models.

test_features.csv: Similar to train_features.csv, each row in this file is metadata for each individual job posting. The file has eight (8) columns and is used to predict the new salaries. 

## Features

* JobId: unique identifier for each job positing
* companyId: unique identifier for each company posting the job position
* jobType: type of job position (e.g janitor, manager, CEO)
* degree: highest degree earned (e.g Bachelor, Doctoral)
* major: major of the degree obtained (e.g. Businesss, Literature, engineering)
* industry: field or industry of the job posting (e.g education, oil, finance)
* yearsExperience: years of experience required/obtained for the job
* milesFromMetropolis: distance away from the metropolis, in miles(mi)
* salary: salary paid for the job, in thousands US dollars; target variable



# Features summary
## salary
![image](https://user-images.githubusercontent.com/70416558/120111457-aa552180-c137-11eb-840f-c3ed7d7352bd.png)
The "salary" variable is normally distributed with only a few observations with more than $200,000 salary. There is no abnormal outliers from the boxplot (salary <=0; those have been removed previously. 


*Correlation matrix*
![image](https://user-images.githubusercontent.com/70416558/120111553-fb651580-c137-11eb-8f80-c3168ba341de.png)
The correlation matrix shows that "companyId" is not correlated with "salary", "milesFromMetropolis" has a negative correlation and the all the other features have a positive correlation with the target variable "salary". Therefore, only the six (6) features (jobType, degree, major, industry, milesFromMetropolis, yearsExperience) are useful to predict the salaries. 


## jobType
![image](https://user-images.githubusercontent.com/70416558/120111765-da50f480-c138-11eb-825b-56d699f87992.png)
Upper management job positions (CEO, CTO, CFO) have the highest salaries and janitors have the lowest salaries. 


## degree
![image](https://user-images.githubusercontent.com/70416558/120111864-36b41400-c139-11eb-942d-ff84d7b52e80.png)
Individuals with doctoral and masters degrees have highest salaries and those without degrees have the lowest salaries.


## major
![image](https://user-images.githubusercontent.com/70416558/120111883-44699980-c139-11eb-8b77-0f1fe55ad9cd.png)
Individuals in STEM and business majors have the highest salaries.


## industry
![image](https://user-images.githubusercontent.com/70416558/120111809-feacd100-c138-11eb-8677-f3434675c289.png)
Job positions in the oil field, finance and web give the highest salaries while those in education have the lowest salaries.


## milesFromMetropolis
![image](https://user-images.githubusercontent.com/70416558/120111911-58ad9680-c139-11eb-81db-356a2029d976.png)
Job positions far away from metropolis have lower salaries and job positions close to metropolis have high salaries. 


## yearsExperience
![image](https://user-images.githubusercontent.com/70416558/120111857-2734cb00-c139-11eb-95b6-967e6ace7e6e.png)
Job positions requiring more years of experience (more than 10 years) have the highest salaries.



# Prediction Models 
The following three (3) models have been found suitable to predict the salaries:Linear regression, random forest and gradient boosting regressor.
The Mean Squared Error (MSE) is the metric used to access the efficacy of each model. A 5-fold cross validation on each model generates the following MSE values:
![image](https://user-images.githubusercontent.com/70416558/120112191-729ba900-c13a-11eb-84a4-b700faf81473.png)

Based on the MSE values, the best model is the Gradient Boosting regressor model. The model is then fit into the trainig data, then used to predict the salaries from the test features. 



# Results
The following table shows a quick view of the predicted salaries (in thousands US dollars) obtained from the gradient boosting regressor model. 

![image](https://user-images.githubusercontent.com/70416558/120112428-6fed8380-c13b-11eb-8615-f0f87f364495.png)


## Feature Importances
The years of experience is the most important factor in predicting the salary of a given job posting. Features such as the distance from metropolis and job types are also important.
![image](https://user-images.githubusercontent.com/70416558/120112529-d07cc080-c13b-11eb-80dd-f03dcd8a660d.png)
