# Creating a Credit Scorecard using Logistic Regression

Capstone project from General Assembly's Machine Learning with Python course.

### Table of Contents:
  1) Background and Dataset
  2) Problem Statement and Hypothesis
  3) Exploratory Data Analysis
  4) Running the Logistic Regression and Random Forests model
  5) Compiling the Credit Scorecard
  6) Conclusion
_______________
### Background and Dataset
Modern lending is  increasingly relying on automated systems to evaluate borrowers and assess risk levels. Using LendingClub’s dataset I perform an exploratory analysis and run it through a logistic regression model to assess if we can use results to predict the likeliness of loan default, and creating a subsequent scorecard to assess borrowers based on the model's results.

I am going to explore the dataset which includes over 1.3 million loan files and over 100 variables which include:
 - Basic borrower information (brief demographics)
 - Borrower credit history (credit score, income, debts, open accounts, etc.)
 - Loan information (terms, rates, payments, etc.)
 - Loan performance (status, i.e. collections, default, PIF)
______________
### Problem Statement
Given a predefined set of borrower credit history and characteristics, can we separate low risk from high risk borrowers and ultimately predict if a borrower will have trouble paying back a loan?

### Hypothesis
I think that employing a classification learner such as logistic regression or random forests, we’ll be able to classify a loan into a binary category, ultimately extracting features that predict loan performance from a predefined set of loan application features.
______________
### Exploratory Data Analysis
Within LendingClub’s website you can select as many features as you want to assess a borrowers application. In this project I select certain features and clean the dataset, followed by several charts to visualize their features. 

Cleaning the Dataset: https://github.com/dvasva5/lendingclub_analysis/blob/master/final_cleaningdata_notebook.ipynb
Visualizing the Features: https://github.com/dvasva5/lendingclub_analysis/blob/master/final_visualizingdata_notebook.ipynb
_______________
### Running the Logistic Regression and Random Forests model
Due to the final and skewed dataset of 400,489 files, the baseline score or split between default and non-defaulted loans is 106,687 and 293,802 respectively, showing 35.98% of the loans are defaulted loans. The logistic regression's confusion matrix results showing actual and predicted values are as follows:
![Confusion Matrix](http://Users/dennisvasquez/logreg_creditscorecard_github/ScreenShot.png?raw=true "Optional Title")
