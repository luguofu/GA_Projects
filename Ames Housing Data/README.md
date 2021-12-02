## README



```
# Project 2 - Ames Housing Data and Kaggle Challenge

#### Lo Kok Fu DSIF 2

### Problem Statement

We are tasked with creating a regression model to best predict salesprice based on the Ames Housing Dataset. We will conduct an analysis to the datasets provided and provide a recommendation of the best regression model and features selection to best predict the pricing of a house sale price. 
This model will enable home owners or property investors to accurately predict sale prices based on what kind of features the houses have or to improve/enhance to realise the higher potential values of the houses. 

The selection of the model represented will be based on the RMSE score and overfitness %.


### Executive Summary

This project aims to analyse and provide for the best Linear Regression model to best accurately predict the Saleprice of houses based on  Ames Housing historical data provided. The Data were grouped into 4 categories, Namely: 1) Ordinal , 2) Nominal, 3) Discrete, 4) Continuous. These categories enabled us to differentiate their data types into qualitative or quantative data.

During our data cleaning process, A total of 9822 null values were discovered in the train dataset. We had either filled in 0 or None value for numerical columns and None for categorical columns. We have also imputed the missing values of lot Frontage with the mean values. We have also removed/corrected the following obvious outliers: Gr Liv Area, Garage Yr Built, 1st Flr SF, Total Bsmt SF Lot, Area Wood Deck, SF Misc Val. Garage yr built: value of 2207 converted to 2007.

Finally for Feature Engineering, we did a feature mapping for the Ordinal Features, assigning numerical values to its grade and then after we conducted an one hot encoding for the Nominal Features. Similarly for the test data sets, similar changes were implented to the test sets.

For Features Selection, we employed the feature selection using SelectkBest. it was discovered that this result was identical to the sorted correlation list of features to the Saleprice. therefore there was no need to employ the SelectkBest method for feature selection. In the initial feature selection plan, we planned for 2 sets of features to model, namely: 1) 10 most Important Features, 2) 50 most Important features. however after running the Linear Regression models on the features, and experimenting with the no. of features to be included. We discovered that 20 most important Features returns us the best results. Therefore we included the 3rd feature selection of 20 Most Important Features for our analysis comparison.

Our Modelling utilised the Linear Regression models with Ridge and Lasso regularisation to observe which will return us the best results basing on the RMSE scores generated. we also employed gridsearchCV to give us the best parameter to impute for our model best parameters. it was observed that the features with 50 features give us not so ideal results and the 10 features was returning us average results. We then decided to insert features of 20 to further analyse the results. Hence it was deduced that the model with 20 most important features, using Ridge Regression gave us the best ideal result with no overfitting scores. 


### Dataset Dictionary

refer to: https://www.kaggle.com/c/dsi-us-11-project-2-regression-challenge/data for the complete description of the data. generally the data are categorised into 4 categories. 
1. Ordinal
2. Nominal
3. Continous
4. Discrete

### Data
- train.csv -- this data contains all of the training data for our model.
- test.csv -- this data contains the test data for our model. You will feed this data into your regression model to make predictions. * The is no Saleprice column in the test set.
- sample_sub_reg.csv -- An example of a correctly formatted submission (with a random number provided as predictions for SalePrice. Ensure that our submission matches this format.
- train_clean.csv -- cleaned version of the train.csv
- test_clean.csv -- cleaned version of the test.csv
- submission.csv -- predicted values using the best ML model 


### Conclusion

We have used feature engineering, feature selection/elimination and regularization to improve our model performance. we have evaluated 3 sets of features(10, 20, 50) using linear Regression with Ridge and Lasso regularization. We also utilised the GridSearchCV tool to generate the best parameter for our regularization models. 

We have evaluated that the model with 20 most important features and using the Ridge regression with alpha:9.99 gives us the best prescriptive RMSE Score results as possible for our problem statement. 

This model will enable home owners to predict their house saleprice and the influencing features of the house which affects the Sale Price. he/she is also able to make a decision to improve/enhance these targetted features to maximise the higher potential value of their house.


### Recommendations

It is observable that from our data, the features of External Quality adds the most value to a home. this is followed by kitchen and overall quality. For Home owners should strongly target these features to improve/enhance to increase and to unlock the higher potential value of thier homes based on our predictions. 

With the prescriptive values for each features, the Home owner is also able to do a cost benefit analysis to whether its worth forking out the initial sum to pay for the home improvement bills and seeking what value of returns. 

whilst there are some features that are not logical to enhance/improve or are unable to do so. i.e year built, Gr Liv area. we will have to filter these unlogical features out. Taking note that these features like year built, gr living area are somehow fixed and we can't change it. They are also good feature indicators for buyers to analyse and to predict the sale price value of the house. 
```
