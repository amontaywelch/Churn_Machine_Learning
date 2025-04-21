# Churn_Machine_Learning

## Project Overview
This project focuses on predicting customer churn using behavioral, demographic, and engagement data. I started by defining churn based on purchase inactivity, then explored key trends using SQL in BigQuery. After feature engineering and data preparation, I trained and evaluated multiple machine learning models in Python, including Random Forest, XGBoost, and logistic regression.

The project was structured to reflect how cross-functional teams use churn insights in a business setting. Churn segments were defined to support marketing teams in targeting re-engagement campaigns. Feature importance and behavioral trends were analyzed to inform product managers about user activity and retention triggers. The data pipeline followed scalable practices relevant to data engineering workflows, and final insights were designed to help customer success teams identify and proactively support at-risk users.

The final model uncovered leading indicators of churn—such as reduced app activity and declining email engagement—which were visualized in a Power BI dashboard. This dashboard enables business users to monitor at-risk customers, explore churn trends over time, and take data-informed action to improve retention.

This project reflects an end-to-end data workflow with a strong business focus, combining technical skills with cross-functional collaboration to solve a common but critical challenge: keeping customers engaged.

## Executive Summary
- Defined churn as having an engagement score < 30 using behavioral data from 10,000 synthetic customer records.

- Conducted data exploration in BigQuery (SQL), followed by modeling in Python (scikit-learn, XGBoost).

- Trained and evaluated multiple classifiers; tuned XGBoost achieved the best balance of precision and recall with 89.7% accuracy

- Identified top churn predictors: time since last purchase, app usage, purchase frequency, and email engagement.

- Created feature importance visuals and ROC curves to support model interpretation.

- Built an interactive Power BI dashboard to monitor churn trends and inform retention strategies for marketing and customer success teams.

## Key Questions Answered
- How do behaviors like app usage, time since last purchase, and email engagement signal early signs of churn?

- What are the earliest detectable changes in customer activity before churn occurs?

- Which customer segments—by spending, engagement, or usage—are most likely to churn?

- Which engagement strategies (e.g. app opens, emails) are most strongly associated with retention?

- Where can marketing and customer success teams focus their efforts to reduce churn and increase lifetime value?

## Tools Utilized
- SQL (Google BigQuery): Performed data exploration, aggregation, and feature summary analysis

- Python (Google Colab): Built machine learning models, engineered features, and evaluated model performance

- Pandas & NumPy: Handled data wrangling, cleaning, and statistical transformations

- Seaborn & Matplotlib: Created visualizations for EDA and model insights (feature importance, ROC curves)

- Scikit-learn: Used for preprocessing, train-test split, and model evaluation metrics

- XGBoost: Tuned and optimized tree-based churn prediction model with class weighting and early stopping

- Power BI: Built an interactive dashboard to highlight churn segments, trends, and KPIs for business users

## Dataset Overview

This project uses a synthetic dataset of 10,000 customers, designed to reflect real-world behavioral, demographic, and engagement patterns. The dataset includes both raw attributes and engineered features relevant to churn prediction.

### **Key Feature Groups**

- **Demographics**  
  `customer_id`, `age`, `gender`, `city`, `signup_days_ago`

- **Behavioral Metrics**  
  `total_spend`, `avg_order_value`, `purchase_frequency`, `time_since_last_purchase`,  
  `most_frequent_category`, `discount_usage_rate`, `customer_support_calls`,  
  `device_type`, `preferred_purchase_time`

- **Engagement Signals**  
  `app_opens_last_30d`, `email_open_rate`, `engagement_score`

- **Target Labels**  
  `churn` (binary)  (Note: Churn was defined as having a cumulative engagement score of less than 30.)

  ## Exploratory Analysis
  Exploratory Data Analysis was conducted using SQL in Google BigQuery, followed by additional visualization in Python (pandas, seaborn, matplotlib). The goal was to identify patterns that signal churn, guide feature engineering, and support downstream modeling decisions.

   ### **Key Findings from EDA**:
 - **Engagement Decline Precedes Churn**
SQL analysis showed churned customers had less app opens at 8.4 times per month, compared to 10.1 app opens per month by retained customers.


A histogram in Python visually confirmed the distribution of `engagement_score`, with a drop below 30:





Email Open Rate is a Strong Engagement Signal
SQL aggregations revealed churners and retained customers are similar with email openings, at 0.65 and 0.72, respectively. 
This behavioral gap suggests declining email interaction is an early signal of disengagement.

Recency Drives Risk
A recency bucketing query showed that churn probability increased significantly after 30 days, with a steep rise beyond 45 days of inactivity.
This insight directly supported the 45-day churn definition used throughout the project.

Support Calls Indicate Friction
Churned customers contacted support 1.8x more frequently than retained users, suggesting unresolved issues may precede churn despite engagement.

Minimal Impact from Demographics
Gender, device type, and age showed no meaningful separation between churned and retained users. These features were retained for completeness but deprioritized during feature selection.



## Machine Learning Approach
The goal of this project was to accurately predict which customers are at risk of churning, enabling timely and targeted retention strategies. The modeling process included feature selection, class balancing, hyperparameter tuning, and performance evaluation.

Workflow Summary
Target Variable:
churn (binary) — 1 = churned, 0 = retained

Modeling Tools Used:
scikit-learn, XGBoost, pandas, GridSearchCV for tuning

Training & Testing Split:
80/20 split with stratification to preserve class balance

Class Imbalance Handling:
Applied scale_pos_weight in XGBoost to improve recall on minority churn class

“Missing a churner is costlier than a false positive” — recall was prioritized.



  











