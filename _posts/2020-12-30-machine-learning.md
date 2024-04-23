---
layout:       post
title:        "Machine Learning"
author:       "Salomon"
header-style: text
catalog:      true
tags:
    - Python
    - R
    - DataScience
    - MachineLearning
---

> Here has some projects about machine learning algorithm; they're all a script, following a pattern.


## [Customer Churn](https://github.com/salomaoalves/DataScience_MachineLearning/tree/main/CustomerChurn)
I created a logistic regression model, using Python, to predict whether or not a customer would cancel their cell phone plan - along with the percentage of each possibility. *Proposed by Data Science Academy*

First, some data munging (checking null values, label encode and a normalization with **sklearn** and data balancing with `RandomOverSample()` function from **imblearn**) is done. Then a visualization with **matplotlib** is done for some columns. Follow by a feature selection, with **sklearn** using the `SelectKBest` function to get the best features to the model - use `LogisticRegression` to get the best ones.

Finally, a logistic regression algorithm (from **sklearn**) is apply to train the data. Use `GridSearchCV` to get the best parameters and make a confusion matrix, accuracy, sensibility and precision to evaluate the model.

## [Customer Satisfaction](https://github.com/salomaoalves/DataScience_MachineLearning/tree/main/CustomerSatisfaction)
Python notebook to predict customer satisfaction of a banking institution. *Proposed by Data Science Academy*

First, some mugning (remove constants columns, create new columns, remove outlier with `IQR` and `ZScore` method) is done. Then explore (use **matplotlib** and **seaborn** to plot the graphics) the data columns. A feature selection (with `correlation` method) to get the best columns to the model.

Finally, a ML model is created (can be a Logistic Reg, Naive Bayes, Random Forest, SVC or XGBC Class from **sklearn** lib) to train the data. Use `GridSearchCV` to get the best parameters and make a confusion matrix, accuracy, sensibility and precision to evaluate the model.

## [Energy](https://github.com/salomaoalves/DataScience_MachineLearning/tree/main/Energy)
Algorithm in Python to predict household energy usage. *Proposed by Data Science Academy*

First, a munging (to remove date and constants colunms) is done, then a visualization with **seaborn** is done. Apply normalization and label encoder (from **sklearn**) into the data. A feature selection with `DecisionTreeRegressor` is done. Finally, a ML algorithm (Linear Reg, Lasso, Random Forest and XGB Reg) is executed, use RMSE, MAE, MEDAE and Cross Validation to evalute the model.

## [Fraud Detection](https://github.com/salomaoalves/DataScience_MachineLearning/tree/main/FraudDetection)
Using R and data about clicks (in ads), I did a ML script to predict click fraud in companies advertising online. *Proposed by Data Science Academy*

First, munging the data (drop na data, data type transformation, replace feature values and delete column). Then a feature selection using `randomForest` function is done, followed by a machine learning algorithms (SVM and Random Forest).
