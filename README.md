The task has been accomplished by using Neural Networks, and uses the idea of <b>Entity Embeddings</b>,
Here is the research paper [Entity Embeddings arxiv](https://arxiv.org/abs/1604.06737), and this project implents that idea

Feature Engineering is not useful for Neural Networks as they are able to do that part by themself, and the missing value imputation was done to apply idea of Entity Embeddings on the categorical features

# Diabetes Prediction

## Table of Content
  * [Overview](#overview)
  * [Motivation](#motivation)
  * [Data](#data)
  * [Frameworks used](#frameworks-used)
  * [Labels](#labels)
  * [Evaluation Metric](#evaluation-metric)
  * [EDA Insights](#eda-insights)
  * [Cross-Validation](#cross-validation)
  * [Model](#model)
  * [Result](#result)

## Overview
This is a simple classification project which uses Xgboost (Not uploaded here) and Deep Neural Network models trained on the top of keras API. The trained model that takes patients vitals and information as input and predict wether the patient has Diabetes-mellitus or not.

## Motivation
Getting a rapid understanding of the context of a patient’s overall health has been particularly important during the COVID-19 pandemic as healthcare workers around the world struggle with hospitals overloaded by patients in critical condition. Intensive Care Units (ICUs) often lack verified medical histories for incoming patients. A patient in distress or a patient who is brought in confused or unresponsive may not be able to provide information about chronic conditions such as heart disease, injuries, or diabetes. Medical records may take days to transfer, especially for a patient from another medical provider or system.

Knowledge about chronic conditions such as diabetes can inform clinical decisions about patient care and ultimately improve patient outcomes.

## Data

To download the data you can go to the following [link](https://www.kaggle.com/c/widsdatathon2021/data) or use the kaggle api by typing the following command in the terminal ```kaggle competitions download -c widsdatathon2021```
The data is from MIT’s GOSSIS (Global Open Source Severity of Illness Score) initiative, it can be found in (`../inputs/wids2021/`)
* TrainingWiDS2021.csv is the training file

## Frameworks-used
1. pandas
2. scikit-learn
3. keras
4. tensorflow


![](https://forthebadge.com/images/badges/made-with-python.svg)<br>
![](https://img.stackshare.io/service/5601/keras.png)
![](https://d2h0cx97tjks2p.cloudfront.net/blogs/wp-content/uploads/sites/2/2019/07/scikit-learn-logo.png)

## Labels
{0 : patient not diagnosed with Diabetes Mellitus,
1: patient diagbosed with Diabetes Mellitus}
 
 ## Evaluation Metric

The Data distribution is very skewed:
label 0: 28,151
label 1: 102,006

The Data has class imbalance, around 20% of people have diabetes and the rest 80% don't have diabetes, also in general, in the world only 8% people have diabetes

So Accuracy was not a good evaluation metric here (as if we predict the most frequent class, we will still get 80% accuracy), So instead of that we will use AUC ROC curves to validate our model.

## EDA-Insights
* There are alot of missing values
* For each patient, vitals are stored at the first hour and after a day
* Around 33% of the data is missing, and many hourly data columns have more than 80% of the data missing in most cases
* Glucose level variable has high correlation to the target variable('diabetes_mellitus') of 0.401, as expected

## Cross-Validation
We are going to use Stratified K Fold cross-validation method, because there is high class imbalance in the dataset. We are using 5 folds.

## Model
We are using Neural Network, which takes numerical features, and categorical features embedding (Entity Embeddings) and 2 Xgboost Models


## Result
We get an AUC ROC score of 0.855307
