# Advanced House Price Regression
> A US-based housing company named Surprise Housing has decided to enter the Australian market. The company uses data analytics to purchase houses at a price below their actual values and flip them on at a higher price. For the same purpose, the company has collected a data set from the sale of houses in Australia. The data is provided in the CSV file. The company is looking at prospective properties to buy to enter the market. The company wants to know:
> - Which variables are significant in predicting the price of a house, and how well those variables describe the price of a house.
> - How accurately can we predict the house price?
> - What is the optimal price at which the company should buy the house and then sell it to get a maximum profit?
> - The company wants to know the following things about the housing market:
> - Which properties are the best to buy?
> - Which properties are best to invest in?
> - Which properties are best to sell?

## Table of Contents
* [General Info](#general-information)
* [Technologies Used](#technologies-used)
* [Observation](#observation)
* [Conclusions](#conclusions)

## General Information
- This assignment is based on the house price regression dataset. The dataset contains the information about the sale of houses in Australia.
- The objective of this assignment is to perform an exploratory data analysis of the house price regression dataset. The analysis will help in understanding the patterns and trends in the house price regression dataset. The analysis will also help in understanding the factors that affect the price of a house. The analysis will also help in predicting the price of a house accurately. The analysis will also help in determining the optimal price at which the company should buy the house and then sell it to get a maximum profit. The analysis will also help in determining the properties that are the best to buy, invest in, and sell.
- The analysis will be performed using the Python programming language and its libraries for data analysis and visualization. The analysis will be performed using the Jupyter Notebook environment. The analysis will be performed using the following steps:
  - Data Preprocessing
  - Data Visualization
  - Feature Selection
  - Model Building
  - Model Evaluation
  - Conclusion


## Technologies Used
- Python - version 3.9
- Jupyter Notebook - version 6.6.3
- Pandas - version 2.2.0
- Numpy - version 1.26.3
- Matplotlib - version 3.8.2
- Seaborn - version 0.13.2
- Sklearn - version 1.4.0
- Statsmodels - version 0.14.1

## Observation
- We Read the housing data first and analysed it after dividing the features into numerical and categorical types.
- SalePrice is the target column here.
- Analyzed complete set of features with missing data handling, outlier detection and data cleaning. Also analyzed and observed the change of SalePrice w.r.t. individual features.
- New features are extracted, redundant features dropped and categorical features are encoded accordingly.
- Further the housing data is split into train and test data and also the feature scaling is performed
- Target variable SalePrice is right skewed. Natural log of the same is Normal distributed, hence for model building, natural log of SalePrice is considered.
- Creating dummy variables increased the number of features greatly, highly imbalanced columns are dropped.
- Top 45 features are selected through RFE and adjusted R-square. 45 features : ['LotArea', 'OverallQual', 'OverallCond', 'YearBuilt', 'YearRemodAdd', 'BsmtFinType1', 'BsmtFinSF1', 'BsmtFinSF2', 'HeatingQC', 'CentralAir', '1stFlrSF', '2ndFlrSF', 'BsmtFullBath', 'BsmtHalfBath', 'HalfBath', 'KitchenQual', 'Functional', 'FireplaceQu', 'GarageArea', 'GarageQual', 'MSZoning_RL', 'MSZoning_RM', 'Neighborhood_Edwards', 'Neighborhood_NAmes', 'Neighborhood_NWAmes', 'Neighborhood_NridgHt', 'Neighborhood_OldTown', 'Neighborhood_Somerst', 'Condition1_Norm', 'RoofStyle_Gable', 'Exterior1st_HdBoard', 'Exterior1st_MetalSd', 'Exterior1st_VinylSd', 'Exterior1st_Wd Sdng', 'Exterior2nd_Plywood', 'Exterior2nd_Wd Sdng', 'Foundation_PConc', 'GarageType_Attchd', 'GarageType_Detchd', 'GarageType_Not_applicable', 'PavedDrive_Y', 'SaleType_New', 'SaleCondition_Normal', 'SaleCondition_Partial']
- Ridge and Lasso Regression Model are built with optimum alpha calculated in GridSearchCV method. Optimum alpha = 20.0 for ridge and 0.001 for lasso model.
- Model evaluation is done with R2 score and Root Mean Square Error.
- Lasso Regression is chosen as final model for having slightly better R-square value on test data.
- Out of 45 features in the final model, top 10 features in order of descending importance are ['1stFlrSF', '2ndFlrSF', 'OverallQual', 'OverallCond', 'LotArea', 'SaleCondition_Normal', 'SaleType_New', 'BsmtFinSF1', 'Condition1_Norm', 'YearBuilt']
- Model coefficients are listed in a table along with the corresponding features , for example natural log of SalePrice will change by 0.13697 with unit change in the feature '1stFlrSF' when all the features remain constant. Negative sign in the coefficient signifies negative correlation between the predictor and target variable.
- Predicted value of SalePrice is tranformed into its original scale by performing antilog.

## Conclusions
- The final model is Lasso Regression with R2 score of 0.90 and RMSE of 0.12.
- The top 10 features that affect the SalePrice are ['1stFlrSF', '2ndFlrSF', 'OverallQual', 'OverallCond', 'LotArea', 'SaleCondition_Normal', 'SaleType_New', 'BsmtFinSF1', 'Condition1_Norm', 'YearBuilt'].