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

After data acqusition, cleaning, EDA, and feature engineering I decided to use data from just the USA (90% of the data comes from the USA) and filtered for people working >=40 hors per week leaving me with 21K rows 21,378 rows / 44 columns to work with. 

## Key Insights & Recommendations
1. The median age for a person making <=50k is 38 and the median for a person makeing >50k is 42.

What I gather from this is that the longer a person is in the workforce the more likely they are to make >50k. Most people who are in a carrer tend to move up in salery over time. 

**Recommendation**- 'Grow Smart' could look into targeting and heping people under tne median age of 38.
![boxplot income_age](https://user-images.githubusercontent.com/87869709/175128916-e496fe12-72fd-4162-a462-824037064bfa.png)

2. People who have a median education level of "some college" are more likely to make <=50k. People with a median education level of an associates degree are more likely 
to make >50k.

**Recommendation**- 'Grow Smart' can work on how to best help people reach at least 2 years of college to gain an associates degree.
![boxplot income_education num](https://user-images.githubusercontent.com/87869709/175129818-f2a58e71-626c-4d61-8703-73c9787eb031.png)

3. The majority of people working 40hrs per week make <=50k but even if a person works more than 40hrs they are not more likely to make >50k.
![hist hours per week_edit](https://user-images.githubusercontent.com/87869709/175130548-337299f9-95a7-4f3b-b3c5-addafed70503.png)

4. When it comes to family relationship the husban is the least likely to make <=50k and the most likely to make >50k. The situation is flipped for the wife. 'Other Relative' (nephew, grandparent, etc.) in this catigory, someone not making much or any income, is the most likley out of everyone to be making <=50k and least likely to be making >50k.

**Recommendation**- 'Grow Smart' should look into targeting wives for the program and look deeper into the 'Other Relative' catigory and how best to assist that demographic.
![hist income_relationship_edit](https://user-images.githubusercontent.com/87869709/175344750-19ca7ae4-6a66-497f-8ac7-63fb1beb392d.png)

5. After feature engineering I was left with 43 features. I used the 'devide by 4 rule' to get my coefficients. Marked with the Red arrows are the standout coefficients.
<img width="804" alt="standout coefficients" src="https://user-images.githubusercontent.com/87869709/175346411-a7251357-a457-4721-bcae-5c05d1851c56.png">

Below are the numbers to these standout coefficients.

<img width="804" alt="Screen Shot 2022-06-23 at 12 16 53 PM" src="https://user-images.githubusercontent.com/87869709/175347734-ca064463-cbe1-4ef9-ade3-55d065c89758.png">

Interpretation using the 'divide by 4 rule': 
Using 'Relationship- Wife', a one unit increase (being a wife) will result in no more than a 32% positive difference in the 
probability that they will make >50k.

All of the standout negative coefficients fall under 'Marital Status' (single people). What this is saying is that being single will decrease the the probability that one will make 50k by or up to 40%.

**Recommendationn**- 'Grow Smart' should look into strategies for targeting/ helping individuals that are single within the 'Marital Status' category.

## Modeling Results
I tried several types of models. Scaled data and used grid search to optimize hyper-parameters for Logistic Regression and implemented a Train, Validate, Test Split: 60/20/20

<img width="1079" alt="Screen Shot 2022-06-23 at 12 48 48 PM" src="https://user-images.githubusercontent.com/87869709/175352419-7ff61571-398a-49c5-936a-36df16461b9a.png">

**Final Test Score Used- Logistic Regression**

Accuracy Score on test: 0.802

Logistic Regression Test Data F1: 0.641

## Future Work
- Add more features
- Incorporate more feature engineering

## Tools
- Google Sheets, Pandas and Numpy for data acquisition, EDA, cleaning, and feature engineering
- Imblearn for resampling unbalanced classes
- Sklearn for modeling and parameter tuning
- Grid Search for hyper-parameter optimization
- Matplotlib and Seaborn for data and model visualization
