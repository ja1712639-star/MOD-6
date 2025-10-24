# Glassdoor Jobs Salary Prediction

## Project Overview
This project performs Exploratory Data Analysis (EDA) and builds a predictive model for tech job salaries using job postings data from **Glassdoor**.  
The goal is to analyze salary trends across roles, locations, and company sizes, and to build a model that estimates expected salary ranges from job attributes.

## Business Context
In the fast-changing tech industry, salary decisions affect hiring, talent retention, and career choices. This project helps:
 Job seekers benchmark expected pay for different tech roles.
 Employers set competitive salaries.
 Recruiters and analysts find salary trends by location, role, and company size.

## Problem Statement 
Analyze how salary varies by job role, company size, and location — and build a predictive model that estimates salaries from job features.

Key questions:
- How do salaries differ between roles (e.g., Data Scientist vs. Software Engineer)?
- What is the impact of company size on pay?
- How do salaries vary by city (e.g., San Francisco vs. AustiN)?
- Can we reliably predict salary using available job attributes?

## Dataset
The dataset contains Glassdoor job postings (2017–2018) and includes company and job-related features.

Main columns / features used
-'job_title' – Job role name  
- 'salary_estimate' – Salary range or estimate (raw)  
- 'min_salary', 'max_salary', 'avg_salary' – Engineered numeric salary fields  
- 'job_description' – Text description of the job  
- 'rating' – Company Glassdoor rating  
- 'company_name' – Employer name  
- 'location' – Job location (city, state)  
- 'headquarters' – Company HQ  
- 'size' – Company size (Small/Medium/Large)  
- 'founded' – Year company was founded  
- 'type_of_ownership' – Ownership (e.g., Private, Public)  
- 'industry', 'sector', 'revenue' – Company metadata  
- 'hourly' – Flag if hourly pay  
- 'num_comp' – Number of competitors listed  
- 'desc_len' – Length of job description (engineered)

> Notes: Some features are engineered during preprocessing (e.g., `min_salary`, `max_salary`, `avg_salary`, `desc_len`).

## Approach
1. Data Loading & Exploration
   - Inspect data (`head()`, `info()`, `describe()`) and create a data dictionary.
2. Data Cleaning
   - Handle missing values, standardize text fields (job titles, locations), and extract numeric salary data from `salary_estimate`.
3. Feature Engineering
   - Create `min_salary`, `max_salary`, `avg_salary`, `desc_len`, and categorical encodings as needed.
4. Exploratory Data Analysis (EDA)
   - Visualize distributions and relationships using at least five plot types (histogram, bar chart, boxplot, scatter, heatmap).
   - Answer business questions about roles, locations, and company size.
5. Modeling
   - Train regression models to predict salary (`avg_salary`), tune hyperparameters, and evaluate using cross-validation and a test set.

## Key Findings (summary)
- Salary levels vary significantly by role and location (major tech hubs generally pay more).
- Larger companies tend to offer higher salaries, but exceptions exist by role and location.
- Job description length and company rating can be correlated with salary in some roles.
- A predictive model can estimate salary ranges reasonably well using engineered features and role/location encodings (model performance and tuning details are in the notebook).
  
## Conclusion

1.Salary Variation by Job Role & Location.

2.Predictive Modeling Insights

-Decision Tree Regressor: On average, predictions are off by $11k. Some predictions have larger errors, sensitive to outliers. Explains ~62% of the variance in salaries. Remark: Basic Decision Tree captures patterns but is prone to overfitting. Performance is moderate.

-Extra Trees Regressor: Better than Decision Tree; lower average error. Handles outliers better than Decision Tree. Explains ~80% of variance; strong predictive power. Remark: Default Extra Trees is already performing well, stable, and reliable for salary prediction.

-Tuned Extra Trees Regressor: R² ~0.774, MAE ~$9k, RMSE: 17.59 → hyperparameter tuning did not improve performance in this dataset; defaults already perform well.

-This can happen because: The dataset is relatively small or clean, so defaults already work well. The parameter grid may not have included the optimal combination.

-Overfitting during cross-validation caused the tuned model to generalize slightly worse on the test set.

3.Business Implications
-Job seekers can benchmark expected salaries by role, company size, and location.
-Companies can use these insights to remain competitive in attracting talent.
-The predictive model provides a reliable tool to estimate salary ranges based on job attributes.


