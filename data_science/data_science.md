# Data Science Interview Questions

### 1. Pet Detection
A classifier that predicts if an image contains only a cat, a dog, or a llama produced the following confusion matrix:

 	True values    
          Dog	Cat	Llama
Predicted values    	Dog	14	2	1
                      Cat	2	12	3
                      Llama	5	2	19
What is the accuracy of the model, in percentages?

**Soluition:**
``` python
```



### 2. Petri Dish
Two bacteria cultures, A and B, were set up in two different dishes, each covering 50% of its dish. Over 20 days, bacteria A's percentage of coverage increased to 70% and bacteria B's percentage of coverage reduced to 40%:

**Soluition:**
``` python
```



### 3. Login Table (x)
A company stores login data and password hashes in two different containers:

- DataFrame with columns: Id, Login, Verified.
- Two-dimensional NumPy array where each element is an array that contains: Id and Password.

Elements on the same row/index have the same Id.

Implement the function login_table that accepts these two containers and **modifies id_name_verified DataFrame in-place**, so that:

- The Verified column should be removed.
- The password from NumPy array should be added as the last column with the name "Password" to DataFrame.

For example, the following code snippet:
``` python
id_name_verified = pd.DataFrame([[1, "JohnDoe", True], [2, "AnnFranklin", False]], columns=["Id", "Login", "Verified"])
id_password = np.array([[1, 987340123], [2, 187031122]], np.int32)
login_table(id_name_verified, id_password)
print(id_name_verified)
```
Should print:
```
   Id        Login   Password
0   1      JohnDoe  987340123
1   2  AnnFranklin  187031122
```

**Soluition:**
``` python
import pandas as pd
import numpy as np

def login_table(id_name_verified, id_password):
    """
    :param id_name_verified: (DataFrame) DataFrame with columns: Id, Login, Verified.   
    :param id_password: (numpy.array) Two-dimensional NumPy array where each element
                        is an array that contains: Id and Password
    :returns: (None) The function should modify id_name_verified DataFrame in-place. 
              It should not return anything.
    """ 
    id_name_verified.drop(['Verified'], axis=1, inplace=True)
    id_name_verified['Password'] = id_name_verified['Id'].map(dict(id_password))

id_name_verified = pd.DataFrame([[1, "JohnDoe", True], [2, "AnnFranklin", False]], columns=["Id", "Login", "Verified"])
id_password = np.array([[1, 987340123], [2, 187031122]], np.int32)
login_table(id_name_verified, id_password)
print(id_name_verified)
```



### 4. Election Poll
Each day during 2019 an agency asked a hundred randomly selected people which party they would vote for if elections were held that day. Results of the poll were recorded in the following file. The Workers' Party asked for the report which they plan to use to improve their strategy for upcoming elections.

Fill in the missing values in the report for 2019:

- The arithmetic mean of votes for the Workers' Party is: __ (rounded to one decimal place)
- The median of votes for the Workers' party is: __ (rounded to closest integer)
- The standard deviation of votes for the Workers' party is: __ (rounded to one decimal place)
- The difference between the largest and the smallest number of votes for the Workers' party for March is: __
- The largest number of votes that any party received on any day is: __ votes.
- That maximum was achieved on 2019-__-__ by __.
- The party with the largest difference between the maximum and minimum number of votes is _______. That difference is __ votes.

**Soluition:**
``` python
```



### 5. Iris Classifier
As a part of an application for iris enthusiasts, implement the train_and_predict function which should be able to classify three types of irises based on four features.

The train_and_predict function accepts three parameters:

- train_input_features - a two-dimensional NumPy array where each element is an array that contains: sepal length, sepal width, petal length, and petal width.
- train_outputs - a one-dimensional NumPy array where each element is a number representing the species of iris which is described in the same row of train_input_features. 0 represents Iris setosa, 1 represents Iris versicolor, and 2 represents Iris virginica.
- prediction_features - two-dimensional NumPy array where each element is an array that contains: sepal length, sepal width, petal length, and petal width.

The function should train a classifier using train_input_features as input data and train_outputs as the expected result. After that, the function should use the trained classifier to predict labels for prediction_features and return them as an iterable (like list or numpy.ndarray). The nth position in the result should be the classification of the nth row of the prediction_features parameter.

**Soluition:**
``` python
import numpy as np
from sklearn import datasets,svm
from sklearn.model_selection import train_test_split
from sklearn import metrics

def train_and_predict(train_input_features, train_outputs, prediction_features):
    """
    :param train_input_features: (numpy.array) A two-dimensional NumPy array where each element
                        is an array that contains: sepal length, sepal width, petal length, and petal width   
    :param train_outputs: (numpy.array) A one-dimensional NumPy array where each element
                        is a number representing the species of iris which is described in
                        the same row of train_input_features. 0 represents Iris setosa,
                        1 represents Iris versicolor, and 2 represents Iris virginica.
    :param prediction_features: (numpy.array) A two-dimensional NumPy array where each element
                        is an array that contains: sepal length, sepal width, petal length, and petal width
    :returns: (list) The function should return an iterable (like list or numpy.ndarray) of the predicted 
                        iris species, one for each item in prediction_features
    """
    model = svm.SVC(random_state=0)
    model.fit(train_input_features,train_outputs)
    return model.predict(prediction_features)

iris = datasets.load_iris()
X_train, X_test, y_train, y_test = train_test_split(iris.data, iris.target,
                                                    test_size=0.3, random_state=0)

y_pred = train_and_predict(X_train, y_train, X_test)
if y_pred is not None:
    print(metrics.accuracy_score(y_test, y_pred))
```



### 6. AB Test
Your company is running a test that is designed to compare two different versions of the company’s website.

Version A of the website is shown to 60% of users, while version B of the website is shown to the remaining 40%. The test shows that 8% of users who are presented with version A sign up for the company’s services, as compared to 4% of users who are presented with version B.

If a user signs up for the company’s services, what is the probability that she/he was presented with version A of the website?

**Soluition:**
``` python
```



### 7. Dog Classification
The following .csv file contains the data from a classifier model that predicts if an image contains a dog: predictions.csv 

The first column contains information if the dog is in the image or not. The second column contains the classifier prediction, which is in the interval 0-100, with higher values meaning that the classifier is more confident that image contains a dog.

What is the value of the decision boundary that will maximize the accuracy of the model? Values greater than or equal to the decision boundary will be treated as positive.

**Soluition:**
``` python
```



### 8. Marketing Costs (x)
Implement the desired_marketing_expenditure function, which returns the required amount of money that needs to be invested in a new marketing campaign to sell the desired number of units.

Use the data from previous marketing campaigns to evaluate how the number of units sold grows linearly as the amount of money invested increases.

For example, for the desired number of 60,000 units sold and previous campaign data from the table below, the function should return the float 250,000.

Previous campaigns
Campaign	Marketing expenditure	Units sold
#1	300,000	60,000
#2	200,000	50,000
#3	400,000	90,000
#4	300,000	80,000
#5	100,000	30,000

**Soluition:**
``` python
import numpy as np
from sklearn import linear_model

def desired_marketing_expenditure(marketing_expenditure, units_sold, desired_units_sold):
    """
    :param marketing_expenditure: (list) A list of integers with the expenditure for each previous campaign.
    :param units_sold: (list) A list of integers with the number of units sold for each previous campaign.
    :param desired_units_sold: (integer) Target number of units to sell in the new campaign.
    :returns: (float) Required amount of money to be invested.
    """
    marketing_expenditure = np.asarray(marketing_expenditure).reshape(-1,1)
    units_sold = np.asarray(units_sold).reshape(-1,1)
    model = linear_model.LinearRegression()
    model.fit(marketing_expenditure,units_sold)
    
    return (desired_units_sold-model.intercept_)/model.coef_

#For example, with the parameters below, the function should return 250000.0
print(desired_marketing_expenditure(
    [300000, 200000, 400000, 300000, 100000],
    [60000, 50000, 90000, 80000, 30000],
    60000))
```



### 9. Stock Prices (x)
You are given a list of tickers and their daily closing prices for a given period.

Implement the most_corr function that, when given each ticker's daily closing prices, returns the pair of tickers that are the most highly (linearly) correlated by daily percentage change.

**Soluition:**
``` python
import pandas as pd
import numpy as np

def most_corr(prices):
    """
    :param prices: (pandas.DataFrame) A dataframe containing each ticker's 
                   daily closing prices.
    :returns: (container of strings) A container, containing the two tickers that 
              are the most highly (linearly) correlated by daily percentage change.
    """
    corr = prices.pct_change().corr().unstack()
    corr = corr[corr != 1]
    return corr.idxmax()

#For example, the code below should print: ('FB', 'MSFT')
print(most_corr(pd.DataFrame.from_dict({
    'GOOG' : [
        742.66, 738.40, 738.22, 741.16,
        739.98, 747.28, 746.22, 741.80,
        745.33, 741.29, 742.83, 750.50
    ],
    'FB' : [
        108.40, 107.92, 109.64, 112.22,
        109.57, 113.82, 114.03, 112.24,
        114.68, 112.92, 113.28, 115.40
    ],
    'MSFT' : [
        55.40, 54.63, 54.98, 55.88,
        54.12, 59.16, 58.14, 55.97,
        61.20, 57.14, 56.62, 59.25
    ],
    'AAPL' : [
        106.00, 104.66, 104.87, 105.69,
        104.22, 110.16, 109.84, 108.86,
        110.14, 107.66, 108.08, 109.90
    ]
})))
```
