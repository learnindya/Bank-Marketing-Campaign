# Bank-Marketing-Campaign
A consumer bank requested an automated system to predict whether a new customer would open a term deposit or not.
Special request: use Neural Network classifier.

## Exploratory Data Analysis
- The average age of customer is 39. Customers are mostly in the 18-70 age bracket.
- The average balance is 448 euros.
- Bank made calls evenly throughout the month. May recorded the highest count of calls. March has the highest conversion rate, followed by December, September, October.
- Bank typically made 2 calls, with average duration per call is 180 s (3 minutes). 
- Most customer hasn't been contacted previously. For customers who received campaigns before, the outcome are 82% identified as 'unknown'.
- Most customers are blue-collar workers, followed by management, technician, admin, and services in order. The highest conversion rate happened to student, followed by retired, unemployed, management and admin.
- 60% of customers are married, followed by single and divorced. Relatively, single customers responded better than divorced and married customers.
- More than a half customers completed secondary education, with 30% in tertiary level. Higher education seems to imply higher conversion rate.
- 98% of customers do not have default credit account and 84% of customers do not have personal loan.
- Customers who have housing loan are 10% higher than those without housing loan.
- Overall, there are only 12% of customers who opened a term deposit. Customers who opened deposit account mostly do not have any loan and unpaid credit.
  
Correlation:
- The target variable (y) has the highest correlation with duration of call.
There is a slight positive correlation between target and balance, the number of days since last contact, and the number of contacts performed before.
There is a slight negative correlation between target and personal loan, housing loan, and number of campaign.

## Data Preprocessing
- Remove outliers with z-score > 3
- Label encoding for education and month
- One-hot encoding for marital, job, contact, poutcome
- Drop age, day, default, marital_divorced, job_unknown, self-employed, job_technician, job_admin., contact_telephone to shorten modelling speed. Reason: Pearson's correlation with target is below 0.01
- Normalization

## Result
- Accuracy testing data: 0.92
- Accuracy training data: 0.91
- roc_auc training data: 0.92
- roc_auc testing data: 0.90

## Summary
- A predictor with accuracy=92% and AUC=92% was achieved using Neural Network algorithm. Further recommendation for better predictor include:
  * Use SMOTE to balance data before splitting train & test data
  * Tune the hyperparameters (hidden_layer_sizes, activation, solver, alpha, learning rate) of MLPClassifier using GridSearch to find better accuracy and AUC
  * Tune the hyperparameters of MLPClassifier using keras package and BayesianOptimization to see the optimal hyperparameters
  * Consider using other algorithms such as Logistic Regression, kNN, Decision Tree, Random Forest
- Duration is the most important feature that affect customer's decision to open deposit account. Therefore, increase duration of call to customers, but limit the number of calls to 2 because it's the optimum value.
- Focus on customers with zero loans.
- Pursue leads with higher balance.
- Hypothesis testing could be carried out to determine whether the difference in job and education affect customer's decision.
- Further analysis on the effect of month needs to be carried out. Is it a seasonal trend? What happened in those months?
- The bank needs to improve its record keeping and follow up campaigns diligently.
- Future action could include the creation of customer profile. Customers can be clustered based on their balance, job, and education. Each cluster could be targeted with different product and marketing approach.
