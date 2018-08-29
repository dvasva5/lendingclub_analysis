# Creating a Credit Scorecard using Logistic Regression

**Capstone project from General Assembly's Machine Learning with Python course**

### Table of Contents:
  1) Background and Dataset
  2) Problem Statement and Hypothesis
  3) Exploratory Data Analysis
  4) Running the Random Forests and Logistic Regression Models
  5) Compiling the Credit Scorecard
  6) Conclusion
_______________
### Background and Dataset
Modern lending is  increasingly relying on automated systems to evaluate borrowers and assess risk levels. Using LendingClub’s dataset I perform an exploratory analysis and run it through a logistic regression model to assess if we can use results to predict the likeliness of loan default, and creating a subsequent scorecard to assess borrowers based on the model's results.

I am going to explore the dataset which includes over 1.3 million loan files and over 100 variables which include:
 - Basic borrower information (brief demographics)
 - Borrower credit history (open accounts, bankcard credit limits, income, debts, etc.)
 - Loan information (terms, rates, payments, etc.)
 - Loan performance (post funding status, collections info, payments, etc.)
______________
### Problem Statement
Given a predefined set of borrower credit history and characteristics, can we separate low risk from high risk borrowers and ultimately identify features that will be indicative in predicting their loan performance?

### Hypothesis
I think that employing a classification learner such as random forests and logistic regression, we’ll be able to classify a loan into a binary category, ultimately extracting features that predict loan performance.
______________
### Exploratory Data Analysis
**Cleaning the Dataset code notebook: https://github.com/dvasva5/lendingclub_analysis/blob/master/final_cleaningdata_notebook.ipynb** 

**Visualizing the Features code notebook: https://github.com/dvasva5/lendingclub_analysis/blob/master/final_visualizingdata_notebook.ipynb**

Within LendingClub’s website you can select as many features as you want to assess a borrowers application. In this project I select certain features and clean the dataset while displaying graphs to visualize the data. The following charts are just some samples: 

![Annual Income Data](https://github.com/dvasva5/lendingclub_analysis/blob/master/Annual%20Income%20data.png "Annual Income Data")

![Total Current Balance by Loan Performance](https://github.com/dvasva5/lendingclub_analysis/blob/master/Total%20Current%20Balance%20by%20Loan%20Performance.png "Total Current Balance by Loan Performance")
_______________
### Running the Random Forests and Logistic Regression model
**Running the Models code notebook: https://github.com/dvasva5/lendingclub_analysis/blob/master/final_runningthemodels_notebook.ipynb**

I ran a random forests model to rank the importance of and narrow the list of features to use on the logistic regression model. The final rank and list of features used on the logistic regression model are the following: ![Random Forest features](https://github.com/dvasva5/lendingclub_analysis/blob/master/rf_featuresrank.png)

Due to the final and skewed dataset of 400,489 files, the baseline score or split between default and non-defaulted loans is 106,687 and 293,802 respectively, showing 35.98% of the loans are defaulted loans. The logistic regression's confusion matrix results showing actual and predicted values are as follows:

![Confusion Matrix](https://github.com/dvasva5/lendingclub_analysis/blob/master/confusion_matrix_screenshot.png)

- TN: 71,892 = predicted no they're not defaults (will perform good), and they were not defaults (performed good).
- FP: 1,446 = predicted yes they are defaults (will perform bad), but they were not actual defaults (performed good) (Type I error).
- FN: 24,980 = predicted no they're not defaults (will perform good), and they were defaults (they performed bad) (Type II error).
- TP: 1,805 = predicted yes they are defaults (will perform bad), and they were actual defaults (performed bad).

The recall score which shows when the model predicts defaults and it's actually a default or TP/actual yes is: 7%.

The ROC curve which shows the relationship between the FPR (false positive rate) and the TPR (true positive rate or recall) has an AUC (area under the curve) score of: 66.2% 

![ROC Curve](https://github.com/dvasva5/lendingclub_analysis/blob/master/roc_curve.png)
_______________
### Compiling the Credit Scorecard
**Compiling the Scorecard code notebook: https://github.com/dvasva5/lendingclub_analysis/blob/master/Scorecard%20build.ipynb**

After referring to Naeem Siddiqi's book "Credit Risk Scorecards Developing and Implementing Intelligent Credit Scoring" he outlines a formula to bucket and score features to compile a scorecard to assess individual borrowers against. I used Sundar Krishnan python code to bucket and compute the features into WoE and IV values, you can find his code here: https://github.com/Sundar0989/WOE-and-IV/blob/master/WOE_IV.ipynb 

![Scorecard_sheet](https://github.com/dvasva5/lendingclub_analysis/blob/master/scorecard_sheet.png) 

This scorecard is a simple template to assess borrowers and could be improved if based on a more comprehensive dataset and more indicative features to derive coefficients from. Considering the cut-off scores, the median score was arbitrarily chosen as the cut-off instead of a more analyitcal approach taking the whole pool of borrowers and perecentage of acceptance considering the underlying business's risk tolerance and ROI.

You can use the scorecard on this excel sheet: https://github.com/dvasva5/lendingclub_analysis/blob/master/final_creditscorecard.xlsx
______________
### Conclusion
Given the unsatisfactory recall score from the logistic regression model and its inability to predict default loans from the test set we're given unreliable coefficients to classify features between the non-default and default loans dataset. Originally, the LendingClub dataset included more features but only accounted for approximately 20% of the used set - meaning this study took quantity of loans over quality of features used.
