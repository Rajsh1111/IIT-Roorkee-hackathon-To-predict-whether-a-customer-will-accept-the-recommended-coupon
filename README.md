# IIT-Roorkee-hackathon-To-predict-whether-a-customer-will-accept-the-recommended-coupon

# Hackathon Problem Statement:
To predict if a customer is going to accept a coupon for a particular venue, considering demographic and contextual attributes:

• train data- 10,147 records 
 
• test data – 2,537 records 

You are hired as a data scientist at a leading shopping mall in the country. The shopping mall has tied up with different restaurants/bars to provide discount coupons to all its customers. The coupons increase the footfalls at these restaurants and helps the shopping mall to attract more customers. The organization have been relying simple guidelines to determine what coupons are to be provided to the customers, however the organization feels that they need a more robust model to determine whether a customer will accept the recommended coupon or not to improve the use rate. Organization plans to use a mix of client's details that they have captured to create this model. You are provided with the historical data of the recommended coupons along with customer details in the previous years and your task is to come up with a model which would be able to predict whether a customer will accept the recommended coupon
The coupons have been issued from the mall to increase the footfalls in the restaurants and overall customers for the Mall

# Solution:
We had to come up with a model which would be able to predict whether a customer will accept the recommended coupon issued from the mall to increase the footfalls in the restaurants and overall customers for the Mall.

First of all, we completed several exploratory data analysis tasks and subsequently pre-processed the data:
Process Followed: Step 1 - Understanding Data & Data Cleaning
Car: It was found that this feature had 99% null values. Hence this feature was dropped
toCoupon_GEQ5min: This feature had only 1 as value. Hence it was removed

Other categorical features with null values were filled with mode

Step 2 – Feature Engineering & Label Encoding
Occupation: This feature had many numbers of values. Hence this was grouped into 4 main categories:
-	Student
-	Unemployed
-	Employed 
-	Retired
These were label encoded to make them ordinal with hierarchy
New Features:
Age: Binning was done for age feature
toCoupon_GEQ15min: toCoupon_GEQ25min: These features were combined together to form a new feature: distance
	If 15 min was 0 then distance = 0
	If 15 min was 1 and 25min = 0, distance = 1
	If 25min = 1, then distance = 2

All other features were One Hot Encoded.

Step 3,4,5– Model Selection, Prediction & Evaluation:
The training data was run on models like
'LogisticRegression', 'SVC', 'KNeighborsClassifier', 'GaussianNB', 
'DecisionTreeClassifier', 'BaggingClassifier', 'RandomForestClassifier',
'GradientBoostingClassifier', 'AdaBoostClassifier','XGBClassifier'
The best results came from RandomForest, Gradient and XGBoost Classifier
These classifiers were further tuned for hyperparameters using RandomSearchCV.

It was found that XGBoost with the following parameters gives the best result:
base_score=0.5, colsample_bylevel=0.75, colsample_bytree=0.6,
       gamma=0, learning_rate=0.085, max_depth=13,
       min_child_weight=0.7, missing=None, n_estimators=200, nthread=-1,
       objective='binary:logistic', reg_alpha=0.7, reg_lambda=2,
       scale_pos_weight=1, seed=1, silent=True, subsample=1

Please refer H2_MightyCondas_FinalSubmission.ipynb for the same.
