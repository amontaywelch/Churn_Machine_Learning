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
EDA was conducted in Google BigQuery (SQL) and Python (pandas, seaborn, matplotlib) to uncover patterns in customer behavior that predict churn. The goal was to identify meaningful signals for early intervention and inform feature selection for modeling.

### Key Insights
 - Churn Distribution & Class Imbalance
   - Insight: Out of 10,000 customers, 1203 were labeled as churned(12.03%), revealing a substantial class imbalance.





   Why This Matters: This kind of imbalance can cause the models trained to favor the majority class (retained customers), and overlook churners. To address this, the modeling phase incorporated class weights to improve the recall on churn predictions.  This ensured the model prioritized identifying at-risk customers — a critical goal for retention-focused business strategies.


 - Engagement Score Distribution & Churn Definition
   - Insight: Churn was defined in this project as having an engagement score of less than 30. This was a score derived from several behavioral signals, such as app opens, email interactions and purchase patterns.
  


  Why This Matters: Rather than using a set churn definition (such as account cancellation), using an engagement score threshold can help determine at-risk customers who are approaching the historical churning zone, enabling methods to intervene with a possible churn. 



  - Behavioral Averages By Churn Status
  - Insight:  Churned users consistently showed lower overall engagement and spending behavior.

 Why This Matters: This reinforces that disengagement isn’t limited to low-spend users. Even previously high-spend customers may churn if usage drops. These behavioral features were strong predictors and heavily factored into the machine learning model.


 - Purchase Frequency Strongly Predicts Churn
 - Insight: The longer the gap since the last purchase, the higher the likelihood of churn — especially after 45 days.

 - Why this matters:
Customers with 45+ days of inactivity had the highest churn rate, validating the use of recency as both a risk indicator and a feature in the churn model. This insight is critical for businesses to trigger re-engagement efforts based on inactivity thresholds.


Email Open Rates Reveal Early Disengagement
Insight: Churned users had much lower email engagement — averaging just 12%, compared to 45% among retained users.
Why this matters:
Email open rate is a non-intrusive, passive signal of engagement that can be tracked easily. A steep decline in email interaction often occurs before full churn, making it one of the earliest actionable triggers for marketing teams to intervene with targeted campaigns.


 Support Calls Correlate with Churn
 Insight: Churners contacted customer support 1.8 times more frequently than retained users.
 Why this matters:
High support call volume is a potential red flag for frustration or unresolved issues. By monitoring support interactions alongside usage trends, businesses can spot at-risk customers who may leave despite being active — and step in with better customer success strategies.







  











