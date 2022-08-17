# loan Hackathon
Loan Defaulters

# Problem Statement
A personal loan is an unsecured credit provided by financial institutions based on criteria like employment history, repayment capacity, income level, profession, and credit history. This is also known as a consumer loan or a multi-purpose loan, and it helps the borrower meet any of their immediate needs.
One of the leading bankers in US has approached you to predict on the defaulters with the help of the recent data on the personal loans availed by various customers.
We have to build a robust machine learning model that would distinguish the future applicants who might default and help the bank to take proactive measures.

# Data Preprocessong and EDA
 Firstly we deal with null values and all  the null values are upto max 6.5% range, in both train and test data, thus we can be imputed by median or mode.
After imputing missing values From the above describe values, we may observe features and  infer that Yearly Income might be slightly right skewed.
Thus we can impute median values to be on the safer side.we also observe that Debt to Income ratio might be slightly right skewed.
Thus we can impute median values to be on the safer side. We should impute with modefor Regional / Demographic variable and for tptal unpaid CL we impute median values.
We should ideally change the dtype of postal code to str/object and impute with mode value.

# Approach 
Performing statistical test to better understand the above variable and we see that ,GGGrade is pretty much dependant on the income of the applicant.Although Grading is done basis applicant's income and assets, there isn't any definite order available in the data.
Thus we might like to encode it as it is in the reverse order to pick up for the model.
 We may bin Experience into 4 buckets as below.thus it may seem fit to bin Home Status into 3 categories .We may remove the redundant variable Postal code, as demography has been already captured by the State field
 There appears some relation of file status with loan approval, can thus safely encode the same with common sensical pointers.
 after that Dummy encoding required on categorical variables. we Transform the data bynusing Power Transformer and then scaling the requisite  numerical variables.After that we prepared our scaled data.
 
 # Model Building and Model Selection
 we build Logistic Regression (LG) as our Base Model. and we also draw DEcision tree and Random Forest and we see that Decision Tree is doing better jona s compared to Random Forest and Logistic regression .After that we tune that Decision Tree by using hyper parameter tuning .
 We also done  feature importance  and feature extraction of tuned decision tree and it will give best features for our further modelling and we Build model by taking a combination of features from Feature Importances as well as SFS .we take the most common features of all the methods use and we observe that  it didn't really do a bad job, but there was no improvement either. We apply XGboost but xgb isn't working here.
 after done different iterations we get to conclude that Random Forest, KNN and xgboost aren't doing good
Only tuned Decision tree and Gaussian Naive bayes performed relatively better,Only tuned DT and Gaussian Naive bayes performed relatively better.
Tuned Decision tree by far gave the best result followed by Gaussian Naive Bayes and SVC . All the 3 can be stacked and checkedand we found that in 1st attempt on Stacking gave best F1 score of 0.5647553 across all other attempted models.
