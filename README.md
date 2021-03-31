# Executive Summary
The Intensive Care Unit (ICU) in a hospital is a battlefield and the ability to predict who lives or dies is very challenging. The Exploratory Data Analyis of this dataset revealed that only the Body Mass Index (bmi) and Weight(kg) had any sort of correlation among the many features.
In the first modelling iteration, approximately 89% of the data was used and the ~11% was discarded due to missing values. This first modelling iteration produced high accuracy scores but low recall and F-1 Scores due to the imbalanced target. However, the second modelling iteration improved the scores with the LightGBM Model performing the best among the six algorithms with improved AUC scores as well. This could be atributted to the filling the missing values and some advanced feature engineering.
In the future, I would be looking to balance the dataset before modelling using SMOTE as well as fine tune the hyperparameters by gridsearching for the best.

## Problem Statement
The Intensive Care Unit in a hospital is a special department that provides intensive care medicine. It caters to patients with severe of life threatening illneses and injuries which require constant care and in most cases close supervision with life support equipment and medication. Given how precious time and attention in the ICU can be, focusing on patients who do not require immediate care can lead to the death of another who does.

## Why is this important?
It is important to be able to predict who lives or dies in an ICU unit to be able to reduce mortality rates as well as shift resources and attention to where they are needed the most.

## Built With
* [Numpy](https://numpy.org)-Numerical Computing Tool
* [Pandas](https://pandas.pydata.org/)-Data Analysis and Manipulation Tool
* [Scikit-learn](https://scikit-learn.org/stable/)-Machine Learning Library
* [Seaborn](seaborn.pydata.org)-Data Visualization Library

## Prerequisites
* Python version 3.0 and above
* Jupyter notebook

## Data
* The data used for this project was obtained from [Uplevel](dataprojects.uplevel.work) and can be downloaded from [here](https://dataprojects.uplevel.work/store/p/pre-order-python-for-healthcare-hospital-survival-and-machine-learning)

* A description of the data dictionary can be downloaded from [here](https://uplevelsg.s3-ap-southeast-1.amazonaws.com)

## Model Performance
The dataset contained highly imbalanced target variables, thus making the accuracy metric unusable for evaluation of the model. However, the Area Under the ROC curve was used for evaluation together with recall and F-1 Score. Below are the tables summmarizing the performance of the models for two modelling iterations.

### First Modelling Iteration

|Estimator|Test Accuracy|F-1 Score|AUC|
|---------|-------------|---------|---|
|Baseline|0.85|0.07|0.49|
|LogisticRegression|0.92|0.00|0.50|
|DecisionTreeClassifier|0.84|0.10|0.51|
|K-NearestNeighborsClassifier|0.91|0.03|0.51|

### Second Modelling Iteration
|Estimator|Test Accuracy|F-1 Score|AUC|
|---------|-------------|---------|---|
|Baseline|0.84|0.09|0.49|
|GradientBoostingClassifier|0.93|0.45|0.89|
|RandomForestClassifier|0.93|0.41|0.88|
|DecisionTreeClassifier|0.88|0.35|0.64|
|GaussianNaive Bayes|0.83|0.40|0.83|
|AdaBoost|0.92|0.45|0.88|
|LightGBMClassifier|0.93|0.47|0.66|


## Conclusion/Recommendation
The EDA showed how highly unbalanced the target variable was which made a lot of sense as fewer people from a sample population died during stay in the ICU. In terms of the age distribution, most of those admitted were between 50 and 85 years old with some sort of pre-existing medical condition. In terms of race and ethnicity, Caucasians accounted for the most of the population followed by Blacks while  Native Americans were almost none existent. Most of the features did not have any form of relationship except for the bmi and weight.

The first modelling iterations produced high accuracy scores but very poor f1-scores as a result of the imbalanced target variables. There was however a remarkable improvement in the second modelling iteration after some advanced feature engineering. The `LightGBMClassifier` model produced the best f1-metric with 0.47 with hyperparameter tuning, which is still quite low given the "life or death" situation in the ICU ward. This can be improved upon by balancing the dataset using SMOTE in future modelling iterations.

Survival in the ICU ward is challenging not only for those who are admitted, but also for those who have to constantly make decisions about the kind of interventions or care to give the patients in the ward. The goodnews is that with Machine Learning, we can try to predict the survival of the patients and hopefully make better decisions regarding the kind of care to administer. While this is not 100% certain, it is a step in the right direction to saving more lives. 
