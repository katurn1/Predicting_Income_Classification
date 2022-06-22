# Classification Project: Predicting Income
Kyle Turner

## The Scenario
It's 2005 and the median U.S. income is 50k. My client 'Grow Smart', a nonprofit, is looking to roll out a program nation wide in the U.S. to help people future plan. 
They want to help people under the current median income to achieve a median U.S. income and for people already above the median income grow into a better financial state.
They will use my recommendations to look into and/or use key features in building their program for rollout.

## Methodology
I hypothesized that creating a classification model for 'Grow Smart' would allow them make accurate predictions on how to get people to the goal of making a median 
income and beyond. Using census data I built a classification model to make predictions on weather an indevidual would make <=50K or >50K.

## Data Description
**Data Specs:**

[Income Classification](https://www.kaggle.com/lodetomasi1995/income-classification): Census data from Kaggle

32,561 rows/ 15 columns

**Target**

Income: 0 = <=50K & 1 = >50K

**Features Key**

- age: continuous.
- fnlwgt: continuous.
- education: Bachelors, Some-college, 11th, HS-grad, Prof-school, Assoc-acdm, Assoc-voc, 9th, 7th-8th, 12th, Masters, 1st-4th, 10th, Doctorate, 5th-6th, Preschool.
- education-num: continuous.
- marital-status: Married-civ-spouse, Divorced, Never-married, Separated, Widowed, Married-spouse-absent, Married-AF-spouse.
- occupation: Tech-support, Craft-repair, Other-service, Sales, Exec-managerial, Prof-specialty, Handlers-cleaners, Machine-op-inspct, Adm-clerical, Farming-fishing, 
Transport-moving, Priv-house-serv, Protective-serv, Armed-Forces.
- relationship: Wife, Own-child, Husband, Not-in-family, Other-relative, Unmarried.
- race: White, Asian-Pac-Islander, Amer-Indian-Eskimo, Other, Black.
- sex: Female, Male.
- hours-per-week: continuous.
- native-country: United-States, Cambodia, England, Puerto-Rico, Canada, Germany, Outlying-US(Guam-USVI-etc), India, Japan, Greece, South, China, Cuba, Iran, Honduras,
Philippines, Italy, Poland, Jamaica, Vietnam, Mexico, Portugal, Ireland, France, Dominican-Republic, Laos, Ecuador, Taiwan, Haiti, Columbia, Hungary, Guatemala, Nicaragua, Scotland, 
Thailand, Yugoslavia, El-Salvador, Trinadad&Tobago, Peru, Hong, Holand-Netherlands.

After data acqusition, cleaning, EDA, and feature engineering I decided to use data from just the USA (90% of the data comes from the USA) and filtered for people working >=40 hors per 
week leaving me with 21K rows 21,378 rows / 44 columns to work with. 

I decided not to use the feature fnlwgt: it is the (estimated) weight of people each row in the data represents. The idea is that if two samples have the same(or similar) fnlwgt 
they have similar characteristics, demographically speaking. Say a sample 7,120 and 33 are having similar fnlwgt values they are more likely to be of the same race, similar educational 
and social background, etc., but fnlwgt is not standardized across different states.
