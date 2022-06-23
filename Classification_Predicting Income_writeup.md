# Predicting Income

My client, 'Grow Smart' is a nonprofit is looking to roll out a program country wide in the US to help people future plan. They want to help people under the current median 
income to achieve a median US income and for people already above the median income grow into a better financial state. They will use my recommendations to look 
into and/or use key features in building their program for rollout.

### Impact hypothesis

We hypothesize that creating a classification model for 'Grow Smart' will allow them make accurate predictions on how to get people to the goal of making a median income and beyond.

## Data Science Solution

Build a classification model that uses census data to make predictions about making <=50K and >50K.

## Data Description
**Data Specs:**

[Income Classification](https://www.kaggle.com/lodetomasi1995/income-classification): Census data from Kaggle

32,561 rows/ 15 columns

**Target**

Income: 0 = <=50K & 1 = >50K

**Features Key**

- age: continuous.
- workclass: Private, Self-emp-not-inc, Self-emp-inc, Federal-gov, Local-gov, State-gov, Without-pay, Never-worked.
- fnlwgt: continuous.
- education: Bachelors, Some-college, 11th, HS-grad, Prof-school, Assoc-acdm, Assoc-voc, 9th, 7th-8th, 12th, Masters, 1st-4th, 10th, Doctorate, 5th-6th, Preschool.
- education-num: continuous.
- marital-status: Married-civ-spouse, Divorced, Never-married, Separated, Widowed, Married-spouse-absent, Married-AF-spouse.
- occupation: Tech-support, Craft-repair, Other-service, Sales, Exec-managerial, Prof-specialty, Handlers-cleaners, Machine-op-inspct, Adm-clerical, Farming-fishing, 
Transport-moving, Priv-house-serv, Protective-serv, Armed-Forces.
- relationship: Wife, Own-child, Husband, Not-in-family, Other-relative, Unmarried.
- race: White, Asian-Pac-Islander, Amer-Indian-Eskimo, Other, Black.
- sex: Female, Male.
- capital-gain: continuous.
- capital-loss: continuous.
- hours-per-week: continuous.
- native-country: United-States, Cambodia, England, Puerto-Rico, Canada, Germany, Outlying-US(Guam-USVI-etc), India, Japan, Greece, South, China, Cuba, Iran, Honduras,
Philippines, Italy, Poland, Jamaica, Vietnam, Mexico, Portugal, Ireland, France, Dominican-Republic, Laos, Ecuador, Taiwan, Haiti, Columbia, Hungary, Guatemala, Nicaragua, Scotland, 
Thailand, Yugoslavia, El-Salvador, Trinadad&Tobago, Peru, Hong, Holand-Netherlands.

## Algorithms
### Data Cleaning and Feature Engineering
1. I began by making sure Nulls were correctly identified then dropped.
2. Stripped all data empty space.
3. Dropped un-needed columns.
4. Created dummy variables for all categorical features.

After some cleaning and EDA I decided to use data from just the USA (90% of the data comes from the USA) and filtered for people working >=40 hors per 
week leaving me with 21K rows 21,378 rows / 44 columns to work with. 

I decided not to use the feature fnlwgt: it is the (estimated) weight of people each row in the data represents. The idea is that if two samples have the same(or similar) fnlwgt 
they have similar characteristics, demographically speaking. Say a sample 7,120 and 33 are having similar fnlwgt values they are more likely to be of the same race, similar educational 
and social background, etc., but fnlwgt is not standardized across different states.

Train, Validate, Test Split: 60/20/20

### Classification Modeling and Parameter Tuning

I used the divide by 4 rule to get my coefficients.

Scaled data and used grid search to optimize hyper-parameter for Logistic Regression

**Logistic Regression**

I built a baseline logistic regression. 
- Accuracy Score on train: 0.803
- Accuracy Score on val: 0.802
- train F1 score: 0.649
- val F1 score: 0.641

**LogisticRegressionCV**
- Accuracy Score train: 0.804
- Accuracy Score val: 0.801
- train F1 score: 0.649
- val F1 score: 0.638

Used grid search to optimize hyper-parameter for RidgeClassifier

**RidgeClassifier**

- Accuracy Score train: 0.803
- Accuracy Score val: 0.800
- train F1 score: 0.643
- val F1 score: 0.632

**RandomOverSampler**

- Logistic Regression on Oversampled Train Data F1: 0.772
- Logistic Regression on Oversampled val Data F1:  0.671
- Logistic Regression on Oversampled val Data Accuracy:  0.776

- RidgeClassifier on Oversampled train F1: 0.683
- RidgeClassifier on Oversampled val F1: 0.632
- RidgeClassifier on Oversampled val Accuracy: 0.773

- Logistic RegressionCV on Oversampled train F1: 0.691
- Logistic RegressionCV on Oversampled val F1: 0.638
- Logistic RegressionCV on Oversampled val Accuracy: 0.774

**Final Test Score Logistic Regression**

Accuracy Score on test: 0.802

Logistic Regression Test Data F1: 0.641

## Tools
- Google Sheets, Pandas and Numpy for data acquisition, EDA, cleaning, and feature engineering
- Imblearn for resampling unbalanced classes
- Sklearn for modeling and parameter tuning
- Grid Search for hyper-parameter optimization
- Matplotlib and Seaborn for data and model visualization


## Communication
- Presentation slides can be accessed [here](https://github.com/katurn1/Classification_Project).
- Links to files are provided [here](https://github.com/katurn1/Classification_Project).
