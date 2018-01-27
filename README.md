# ExploringAProblem

## Domain of the Problem :
  
   Source: The data set we use for this exercise is the Adult Dataset from https://archive.ics.uci.edu/ml/machine-learning-databases/adult/ which is from the census.
   
   Time : 1994, so this might not be still relevant as the target variable can now be affected by different factors than is provided in the set.
   
  There are 2 datasets:
  
  A test dataset adult.test
  A train dataset adult.data
  

## How has data science or machine learning been used to solve this or similar problems in the past?

We have from the site itself this description :

 Algorithm               Error
| -- ----------------        -----
| 1  C4.5                    15.54
| 2  C4.5-auto               14.46
| 3  C4.5 rules              14.94
| 4  Voted ID3 (0.6)         15.64
| 5  Voted ID3 (0.8)         16.47
| 6  T2                      16.84
| 7  1R                      19.54
| 8  NBTree                  14.10
| 9  CN2                     16.00
| 10 HOODG                   14.82
| 11 FSS Naive Bayes         14.05
| 12 IDTM (Decision table)   14.46
| 13 Naive-Bayes             16.12
| 14 Nearest-neighbor (1)    21.42
| 15 Nearest-neighbor (3)    20.35
| 16 OC1                     15.04
| 17 Pebls                   Crashed.  Unknown why (bounds WERE increased)

People have tried many differrent methods and ensembles since when the results above were released.
It's hard to say what the best model is until after trying it as is suggested in this paper:
https://cseweb.ucsd.edu/classes/wi17/cse258-a/reports/a120.pdf

That is an ambitious paper to try. For now we will try a solution we are familair with.

# Problem Statement

## The inputs

Off the top the train set has 16 columns and 32560 rows
The test set has 15 columns and 16281 rows, but a sample shows just one column because of how the file is organized.

33% of the data is in the test set.
The usual partition is 25/75, but we could use the 33 percent for test and validation which is recommended.

It is important to make sure the partitions are similar. If the train set is not similar to test set, this may bring about an incorrect model. Since in the description it says "used MLC++ GenCVFiles to partition to test and data" , we assume the two sets are controlled.

There is also a variable *fnlwgt* which is similar for demographics with similar characteristics within a state.

The test and train set has different number of columns and is stated as reasonably clean. 
So we need to look at each of the columns and check for data incompleteness, errors and omit what we don't need after assessing how omitting affects the data.

Before using this data for regression or classification we need to see if each of these variables are nominal , ordinal or interval, so the model does not interpret the data incorrectly.


## The type of data science or machine learning you intend to do

The description of the problem itself says "Prediction task is to determine whether a person makes over 50K a year"
So there is a target and hence we need to use supervised learning.
If the question was to predict how much a person makes, then we would probably use regression, but since the question is
to see if someone makes 50K, there are two classes <50K and >50K.
So this is a classification task.

We can also use clustering just to explore the data before starting on the prediction task.

## The outputs

- The benchmark or an initial goal on what would be considered worthy enough to have a model predict this as opposed to basic methods of estimation.
- The train set and the fit on the train set.
- The test set's fit and 
- A classification matrix.

## According to Tom Mitchell's rigorous definition of a machine learning problem:

A computer program is said to learn from 
experience E (in this case the training census data)
with respect to some class of tasks T (salary earned)
and performance measure P (fit, accuracy wrt test and validation data), 
if its performance at tasks T, as measured by P, improves with experience E.

# A description of the dataset including:
## The types of the data :

age: continuous. 
workclass: Private, Self-emp-not-inc, Self-emp-inc, Federal-gov, Local-gov, State-gov, Without-pay, Never-worked. 
fnlwgt: continuous. 
education: Bachelors, Some-college, 11th, HS-grad, Prof-school, Assoc-acdm, Assoc-voc, 9th, 7th-8th, 12th, Masters, 1st-4th, 10th, Doctorate, 5th-6th, Preschool. 
education-num: continuous. 
marital-status: Married-civ-spouse, Divorced, Never-married, Separated, Widowed, Married-spouse-absent, Married-AF-spouse. 
occupation: Tech-support, Craft-repair, Other-service, Sales, Exec-managerial, Prof-specialty, Handlers-cleaners, Machine-op-inspct, Adm-clerical, Farming-fishing, Transport-moving, Priv-house-serv, Protective-serv, Armed-Forces. 
relationship: Wife, Own-child, Husband, Not-in-family, Other-relative, Unmarried. 
race: White, Asian-Pac-Islander, Amer-Indian-Eskimo, Other, Black. 
sex: Female, Male. 
capital-gain: continuous. 
capital-loss: continuous. 
hours-per-week: continuous. 
native-country: United-States, Cambodia, England, Puerto-Rico, Canada, Germany, Outlying-US(Guam-USVI-etc), India, Japan, Greece, South, China, Cuba, Iran, Honduras, Philippines, Italy, Poland, Jamaica, Vietnam, Mexico, Portugal, Ireland, France, Dominican-Republic, Laos, Ecuador, Taiwan, Haiti, Columbia, Hungary, Guatemala, Nicaragua, Scotland, Thailand, Yugoslavia, El-Salvador, Trinadad&Tobago, Peru, Hong, Holand-Netherlands.

All of this needs to be transformed

## Other questions from this topic can be found in the notebook
The size of the dataset both in terms of rows and columns, but also in memory (ipynb)
identify the features and the target (ipynb)
summary statistics of the data (ipynb)
distribution of the target class (if applicable) and a few key features (ipynb)

# A proposed solution 
Multivariate Logistic Regression

# A benchmark model
From the census data given it is seen that 75% of the sample have salaries < 50K
If I said "All of the sample population had a salary of < 50K", I would be right 75% of the time and wrong 25% of the time.
If the model I build can be more accurate that that, then it is worth something.

# A performance metric used to assess the performance of your proposed solution
 AUROC, 
 f-score(not even distributed), 
 accuracy(even distribute)

Here, F-score should be used as a performance metric since the target is not evenly distributed.




