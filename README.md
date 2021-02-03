# Diabetes-Prediction

The task has been accomplished by using Neural Networks, and uses the idea of <b>Entity Embeddings</b>,
Here is the research paper [Entity Embeddings arxiv](https://arxiv.org/abs/1604.06737), and this project implents that idea

Feature Engineering is not useful for Neural Networks as they are able to do that part by themself, and the missing value imputation was done to apply idea of Entity Embeddings on the categorical features


## Objective
Getting a rapid understanding of the context of a patient’s overall health has been particularly important during the COVID-19 pandemic as healthcare workers around the world struggle with hospitals overloaded by patients in critical condition. Intensive Care Units (ICUs) often lack verified medical histories for incoming patients. A patient in distress or a patient who is brought in confused or unresponsive may not be able to provide information about chronic conditions such as heart disease, injuries, or diabetes. Medical records may take days to transfer, especially for a patient from another medical provider or system.

Knowledge about chronic conditions such as diabetes can inform clinical decisions about patient care and ultimately improve patient outcomes.

## Data
The data is from MIT’s GOSSIS (Global Open Source Severity of Illness Score) initiative, it can be found in "../inputs/wids2021/" 
* TrainingWiDS2021.csv is the training file

## Evaluation Criteria
The Data has class imbalance, around 20% of people have diabetes and the rest 80% don't have diabetes, also in general, in the world only 8% people have diabetes

So Accuracy was not a good evaluation metric here (as if we predict the most frequent class, we will still get 80% accuracy), So instead of that we will use AUC ROC curves to validate our model.

## EDA Insights
* There are alot of missing values
* For each patient, vitals are stored at the first hour and after a day
* Around 33% of the data is missing, and many hourly data columns have more than 80% of the data missing in most cases
* Glucose level variable has high correlation to the target variable('diabetes_mellitus') of 0.401, as expected

## Model
We are using Neural Network, which takes numerical features, and categorical features embedding (Entity Embeddings)

## Result
We get an AUC ROC score of 0.855307