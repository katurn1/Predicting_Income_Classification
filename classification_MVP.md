My client, a nonprofit is looking to roll out a program country wide in the US to help people future plan. The current median income in the US is 50K so they want to know what 
features will contribute to a person making a minimum <=50k or >50K. I will use census data and create a model using <50k & >50k as the target. With this iformatiom / data the 
nonprofit will be able to create their program and accuratly target the people that need the most help in reaching a median income.

My data is Census data from Kaggle: [Income Classification](https://www.kaggle.com/lodetomasi1995/income-classification)

For the project I decided to use Logistic Regression and accuracy score to maximize interpretability of the data. My target is 'income' (<=50K, >50K). After some cleaning and EDA 
I decided to use data from just the USA (90% of the data comes from the USA) and filtered for people working >=40 hors per week leaving me with 21K rows to work with. 
I then created dummy data for all categorical data.

A false positive or false negative will lead to less accuracy in the model.

### Baseline accuracy score of all data-
Score on train:
0.6962420084203961

Score on val:
0.700420954162769

I chose these key features through EDA.
![boxplot income_education num](https://user-images.githubusercontent.com/87869709/155032488-acf0cd32-fd71-4956-88a3-a03f178793e0.png)
![boxplot income_age](https://user-images.githubusercontent.com/87869709/155032495-64e60d5d-0416-43b2-a7bd-c7bcdbe69418.png)

### Accuracy score when adding a few key features-
Score on val w/ education num:
0.725912067352666

Score on val w/ education num, age:
0.7453227315247896

Score on val w/ education num, age, sex:
0.7628624883068288


I still plan to look at the coefficient of features to help in feature selection. I'm also deciding not to use the feature
fnlwgt: it is the (estimated) weight of people each row in the data represents. The idea is that if two samples have the same(or similar) fnlwgt they have similar characteristics,
demographically speaking. Say a sample 7,120 and 33 are having similar fnlwgt values they are more likely to be of the same race, similar educational and social background, etc., 
but fnlwgt is not standardized across different states.
