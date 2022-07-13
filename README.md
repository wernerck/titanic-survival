# Titanic Survival Prediction

This notebook is related to the following Kaggle competition: "Titanic - Machine Learning from Disaster," which can be found at https://www.kaggle.com/c/titanic/overview. The challenge involves building a model to predict Titanic survival given information such as age, ticket class, and sex. The competition data includes a training set with outcomes, a test set, and an additional file that shows example output. 

## Approach
I started with a basic examinination of the training set to look at variables and determine if there were any null values. I followed up by exploring the data frame variables using pairplots and value counts. This allowed me to determine which columns will be useful for the analysis and which columns are made mostly or entirely of unique features. For example, every passenger had a different name, so this will likely be unhelpful for the prediction. 

To prepare the training and test sets, dropped columns with mostly or entirely unique values. I also changed strings to integers. For example, Embarked includes "S," "C," and "Q" values, which I replaced with integers 1-3. I filled NaN values with 0 if the only other value in the column was 1. For cabins, either a cabin name was specified or a passenger did not stay in a cabin. Therefore, I replaced any specified cabin with 1 and NaN values with 0 to delineate which passengers stayed in cabins and which ones did not. Otherwise, I filled NaN values with the column mean. To specify which values were previously NaN, I used feature engineering. I created another column that contained 1s if a value was specified in the original data frame and 0s if no value was specified. I split the training set into X and y. The test set only contains X data. 

I loaded the following models using sklearn and tuned hyperparameters using GridSearchCV: GaussianNB, LogisticRegression, svm.SVC, DecisionTreeClassifier, and RandomForestClassifier. After incoporating the new hyperparameters, I ensembled the models using VotingClassifier and fit X and y from the training set. Finally, I used the ensembled models to make predictions for X_test. I wrote the passenger IDs and predictions to a csv file and uploaded them to Kaggle. 

## Requirements
Use the package manager pip to install packages.

```
pip install numpy, pandas, seaborn, matplotlib
```

## Support
If you have any issues, comments, or questions please contact wernerck@umich.edu.
