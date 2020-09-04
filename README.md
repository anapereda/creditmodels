# Machine Learning Credit Models 

## Resampling 

In this challenge we developed Machine Learning Logistic Regression model to predit loan status of high or low risk based on all the numerical values given in the LoanStats_2019Q1.csv data set. Classification features ('loan_status', 'home_ownership', 'verification_status', 'issue_d', 'loan_status', 'pymnt_plan', 'initial_list_status', 'next_pymnt_d', 'application_type','hardship_flag', 'debt_settlement_flag') were dropped in this initial model to evaluate its perfomane based on numerical values and all values were scaled using a Standard Scalar. 

### Naive Random Oversampling
As expected, the dataset was imbalanced between low and high risk; after the first random sampling between the train and test dataset there were 51366 low risk loand and 246 high risk loans. The Naive Random Oversampled equalized the number of low and high risk; after developong the Logistic Regression model and predicting values for y_train the balance accuracy score was 0.7123 or 71.23% predictions were accurate. This model has a very low precision at identifying high risk, and almost perfect for low risk loans; recall value is 0.8 points higher gor low risk however both are above 0.6 percent. F1 score was high for low risk loans and very low for high risk; thus the model does a good job predicting low risk while it is not perfoming well at all when predicting for high risk loans.

### SMOTE Oversampling
I also used SMOTE oversampling to evaluate the performance of the Logistic Regression Model. Balanced accuracy test was 0.706 or 70.6%; performance was slightly decreased. Precision score was again very low for high risk and perfect for low risk; recall were above 0.6, low risk had slightly better performance. F1 score was as expected high in low_risk while very low in high risk (due to the imbalance between precision and recall)

### Undersampling
Using a undersampling method; high risk training value had only 246 data points.From the very first marker we see a reduction 0.64 or 64% balanced accuracy test. Precision behaved similary; low for high risk and perfect score on low risk; recall again were balances between o.6 and 0.7 and f1 score was high los low risk loans and low for high risk loans. This model is also doing a good job at predicting low risk loan while not really doing a good job in predinting high risk loans. 

### Cluster centroids

Finally we used a cluster centroids undersampling method; the accuracy score improved and was 0.69 or 69%. Precision is very low in high risk and high for low risk, and there is an increase in recall and for the first time the model scores higher for high risk. F1 level still behave similar in high risk (low score) due to imbalance petween precision and recall. This is the model that I would choose when improving my model.

## Ensamble 

After trying different resampling methods; the machile learning model did not perform that well. We are going to try two ensamble learnes, balanced random forest and an Easy Ensamble AdaBoost classifier with a simple oversampling. 

### Balanced Random Forest

This model had a balanced accuracy score 0.702 or 70.2%; precision was 0.02 and recall 0.68. The model was a llittle bit better and then by using feature importance we see htat using total_rec_prncp, total_pymnt, total_pymnt_inv, last_pymnt_amnt, total_rec_int and int_rate are the most important features to predict loan status

### Easy Ensamble AdBoost classifier

Finally the adboos classifier had 0.72 balanced accuracy score. Precision 0.02 and recall of 0.56; this is the model that predicted the most accurate and still has higher recall meaning that it is not overfitting the data and can applied to other data. 


### Conclusion 

I would not use any of this model because it is not preficting correctly high risk. I would use build a logistic regression model using AdBoost and instead of simple oversampling using cluster centroid. Finally I think the list of features should be greatly reduced, maybe using the very first ten variables and also encoding categorical data so it can be tested to be used in the model. 
