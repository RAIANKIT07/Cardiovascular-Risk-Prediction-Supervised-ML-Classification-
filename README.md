# Cardiovascular-Risk-Prediction-Supervised-ML-Classification-

📋 Summary
The primary goal of this research is to create a supervised machine learning model to predict the risk of heart disease in individuals. There are 3390 rows and 17 columns in the data. It is based on an ongoing research project in Framingham, Massachusetts.
The project was completed in five steps:

Data Cleaning
Exploratory Data Analysis (EDA)
Construction and Evaluation of Data Transformation Models
Tuning of Hyperparameters
Engineered a crucial aspect of pulse pressure utilising systolic and diastolic blood pressure.

The end result is an XGBoost model with over 87% accuracy, 89% precision, and 84% recall.

![image](https://user-images.githubusercontent.com/116347910/210876739-0af7e74d-ca68-47da-b8b2-8a9c830847b8.png)


1. Introduction:

Cardiovascular diseases (CVDs) are the leading cause of death globally. CVDs killed 17.9 million people in 2019, accounting for 32% of all global fatalities, according to WHO.
Though CVDs are incurable, forecasting the disease's risk and adopting the required precautions and treatments might assist to avert severe symptoms and, in some circumstances, death.
As a result, precisely predicting the risk of heart disease is crucial in order to prevent as many deaths as possible.
The purpose of this study is to create a categorization model that, based on demographic, lifestyle, and medical history, can predict whether a patient is at risk of coronary heart disease (CHD) during a 10-year period.

2. EDA Summary:

The dependent variable is unbalanced, with only ~15% of the patients who tested positive for CHD.
All the continuous variables are positively skewed except age (which is almost normally distributed)
Majority of the patients belong to the education level 1, followed by 2, 3, and 4 respectively.
There are more female patients compared to male patients.
Almost half the patients are smokers.
100 patients under the study are undertaking blood pressure medication.
22 patients under the study have experienced a stroke.
1069 patients have hypertension.
87 patients have diabetes.
The risk of CHD is higher for older patients than younger patients.
18%, 11%, 12%, 14% of the patients belonging to the education level 1, 2, 3, 4 respectively were eventually diagnosed with CHD.
Male patients have significantly higher risk of CHD (18%) than female patients (12%)
Patients who smoke have significantly higher risk of CHD (16%) than patients who don't smoke (13%)
Patients who take BP medicines have significantly higher risk of CHD (33%) than other patients (14%)
Patients who had experienced a stroke in their life have significantly higher risk of CHD (45%) than other patients (14%)
Hypertensive patients have significantly higher risk of CHD (23%) than other patients (11%)
Diabetic patients have significantly higher risk of CHD (37%) than other patients (14%)
Above is the correlation heatmap for all the continuous variables in the dataset.
The variables ‘systolic BP’ and ‘diastolic BP’ are highly correlated.
To handle high correlation between two independent variables, we can introduce a new variable ‘pulse_pressure’
--

3. Modelling Summary:

3.1. Logistic Regression:

In statistics, the (binary) logistic model is a statistical model that models the probability of one event (out of two alternatives) taking place by having the log-odds (the logarithm of the odds) for the event be a linear combination of one or more independent variables.
This can be considered as the baseline model to obtain predictions since it is easy to explain.
Logistic Regression train recall: 0.69
Logistic Regression test recall: 0.66

3.2. K-nearest Neighbors:

The k-nearest neighbors algorithm, also known as KNN, is a non-parametric, supervised learning classifier, which uses proximity to make classifications or predictions about the grouping of an individual data point.
Best hyperparameters: K = 55
K nearest neighbors train recall: 0.83
K nearest neighbors test recall: 0.69

3.3. Naïve Bayes:

Naive Bayes classifiers are a collection of classification algorithms based on Bayes’ Theorem. It is not a single algorithm but a family of algorithms where all of them share a common principle, i.e., every pair of features being classified is independent of each other.
Best hyperparameters: var_smoothing= 0.657933224657568
Naïve Bayes train recall: 0.53
Naïve Bayes test recall: 0.50

3.4. Decision Tree:

A Decision tree is a flowchart-like tree structure, where each internal node denotes a test on an attribute, each branch represents an outcome of the test, and each leaf node (terminal node) holds a class label.
Best hyperparameters: max_depth: 1, min_samples_leaf: 0.1, min_samples_split: 0.1
Decision tree train recall: 0.86
Decision tree test recall: 0.77
3.5. Support Vector Machine:

Support Vector Machine (SVM) is a supervised machine learning algorithm used for both classification and regression. The objective of SVM algorithm is to find a hyperplane in an N-dimensional space that distinctly classifies the data points.
Best hyperparameters: C: 1, gamma: 0.01, kernel: rbf
SVM train recall: 0.74
SVM test recall: 0.69
3.6. Random Forests:

Random Forest is an ensemble technique capable of performing both regression and classification tasks with the use of multiple decision trees and a technique called Bootstrap and Aggregation, commonly known as bagging. The basic idea behind this is to combine multiple decision trees in determining the final output rather than relying on individual decision trees.
Best hyperparameters: max_depth: 2, min_samples_leaf: 0.1, min_samples_split: 0.1, n_estimators: 500
Random forests train recall: 0.70
Random forests test recall: 0.66

3.7. XG Boost:

In this algorithm, decision trees are created in sequential form. Weights play an important role in XGBoost. Weights are assigned to all the independent variables which are then fed into the decision tree which predicts results. The weight of variables predicted wrong by the tree is increased and these variables are then fed to the second decision tree. These individual classifiers/predictors then ensemble to give a strong and more precise model. It can work on regression, classification, ranking, and user-defined prediction problems.
Best hyperparameters: max_depth: 1, min_samples_leaf: 0.1, min_samples_split: 0.1, n_estimators: 500
XG boost train recall: 0.78
XG boost test recall: 0.60
--

4. Results:

Sl. No.	Classification Model	Train Recall (%)	Test Recall (%)
1	Logistic Regression	69.87	67.32
2	K Nearest Neighbors	83.17	71.24
3	Naive Bayes	58.11	52.94
4	Decision Tree	85.95	77.12
5	Support Vector Machines	76.52	66.66
6	Random Forests	69.97	64.70
7	XG Boost	79.45	61.43
--

5. Conclusions

Predicting the risk of coronary heart disease is critical for reducing fatalities caused by this illness. We can avert deaths by taking the required medications and precautions if we can foresee the danger of this sickness ahead of time.
It is critical that the model we develop has a high recall score. It is OK if the model incorrectly identifies a healthy patient as a high risk patient because it will not result in death, but if a high risk patient is incorrectly labelled as healthy, it may result in fatality.
We were able to create a model with a recall of just 0.77 because of lack of data and limitations in computational power availability.
Recall of 0.77 indicates that out of 100 individuals with the illness, our model will be able to classify only 77 as high risk patients, while the remaining 33 will be misclassified.
Future developments must include a strategy to improve the model recall score, enabling us to save even more lives from this disease.
This may include more such studies, and collect more data. Include more people with hypertension, diabetes, BP medication, etc to better understand the effect of these disease on the risk of CHD. Also, with better computational abilities, it will be possible to get the best hyperparameters that yield the best predictions.
