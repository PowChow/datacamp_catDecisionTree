---
title       : Evalute Car Features
description : Introduces categorical variables and methods to encode for Decision Tree

--- type:MultipleChoiceExercise lang:python xp:50 skills:2 key:7840cf4c0c
## Identify Categorical Values

**Categorical variables** are used to describe everything around us. For example, categorical variables that describe people are: 

- gender, 
- occupation, 
- blood type, and 
- marital status

As a data scientist, you will translate categorical variables into numerical variables for analysis, visualization, and modeling. Many python packages are not able to analyze categorical values in string formats.

Here is context for the `cars` dataset. An online car broker wants to understand what features influence customer car ratings. On their site, customers rate cars as 'unacceptable', 'acceptable', 'good', and 'very good' and is captured in the `cars` dataset along with other car features. At the end of this section, the goal is to use a decision tree model to predict customer ratings based on car features. Initially, the `cars` dataset must be cleaned before the model may be run in your workspace.  

Explore the `cars` data, which is available in your workspace: 

- Print out the first few rows and all columns by using `head()`
- Print out list of all columns variables by using `columns`

By looking at column names alone, which `cars` dataset variables are categorical?

*** =instructions
- Buying Price
- Number of Doors
- Customer Rating
- all of the above

*** =hint
- Type "cars" into command line to print out all the values of cars. 
- The correct syntax are `DataFrame.head()` and `DataFrame.columns`. Substitute the `cars` dataset in for DataFrame.

*** =pre_exercise_code
```{python}
#pre load the dataset into the exercise
import pandas as pd

cars = pd.read_csv('http://s3.amazonaws.com/assets.datacamp.com/production/course_1742/datasets/cars_dataset_updated.csv')
```

*** =sct
```{python}
msg1 = "Great!"
msg2 = "Sorry, try again."
test_mc(4, [msg2, msg2, msg2, msg1])
```

--- type:NormalExercise lang:python xp:100 skills:2 key:7d067101e2
## Find Categorical Variables

It is not always intuitive to find categorical variables. 

Pandas `describe()` can print out summary statistics for categorical variables. Unique values of each column can be printed through the `unique()` function. 

__Notice__: If datasets are of mixed type, continuous and categorical variables, then the `describe()` function defaults to displaying statistics for continous variables only. In this case, split columns by variable types before showing summary statistics.

*** =instructions
- Print summary statistics for the `cars` dataset
- We are interested in the range of customer ratings given to cars in this dataset. Print out the unique values for the `cusomter_rating` and `safety_level` columns. 

*** =hint
- The correct syntax for summary statsitics is `DataFrame.describe()`. Substitute your dataset for DataFrame. Notice the features provide by the output of `describe()`, such as count of unique categorical variables, most frequent category appearing in that columns, total frequency.
- The pandas `unique()` function applies to Series or columns in pandas dataframes. The correct syntax for `unique()` if `df['column_name'].unique()`.

*** =pre_exercise_code
```{python}
import pandas as pd

cars = pd.read_csv('http://s3.amazonaws.com/assets.datacamp.com/production/course_1742/datasets/cars_dataset_updated.csv')
```

*** =sample_code
```{python}
# Print summary statistics of `cars` dataset with describe()


# Print the unique categorical values for 'customer_rating' column


# Print the unique categorical values for 'safety_level' column

```

*** =solution
```{python}
# Print summary statistics of `cars` dataset with describe()
print(cars.describe())

# Print the unique categorical values for 'customer_rating' column
cars['customer_rating'].unique()

# Print the unique categorical values for 'safety_level' column
cars['safety_level'].unique()
```

*** =sct
```{python}
success_msg("Great work!")
```
--- type:NormalExercise lang:python xp:100 skills:2 key:cbb6428a5f
## Encode Categorical Variables

Converting categories from text to numbers means that unqiue strings are encoded into unique integers. For example, `gender` may have the values ['male', 'female', 'nontraditional'] and can be encoded as [0, 1, 2]. 

Since the car broker wants to know which car features influence the `customer_rating`, this column becomes the target values for the Decision Tree model. 

*** =instructions
- Print the output of `cars['customer_rating'].unique()`. Then use these values to explicitly `map` strings to unique numbers with a dictionary.
- Write a function that converts strings in the `customer_rating` column to unique numerical values. We will use the output of your function operator as the target value for our decision tree. Use python's built-in `map` function.    

*** =hint
- Use the `map` function and dictionary of `string:int` to convert each category from string to integer.  
- The correct syntax for `map` is `df.columns_name.map({'category_1': 0, 'category_2':1 })`. Substitute values that are relevant for your function. 

*** =pre_exercise_code
```{python}
# I read the data in here again, just in case
import pandas as pd

cars = pd.read_csv('http://s3.amazonaws.com/assets.datacamp.com/production/course_1742/datasets/cars_dataset_updated.csv')
#print('cars dataset available to workspace')
#print('Print unique values for customer_rating in cars dataset: ', cars['customer_rating'].unique())
```

*** =sample_code
```{python}
# function operator to map category strings from customer_rating to values
```

*** =solution
```{python}
# solution code
print(cars['customer_rating'].unique())
cars['customer_rating'] = cars.customer_rating.map({'unacc':0, 'acc':1, 'vgood': 2, 'good': 3})

```

*** =sct
```{python}
success_msg("Great work!")
```
--- type:NormalExercise lang:python xp:100 skills:2 key:717bf0d477
## Convert Categories to Dummies

Another method to convert string category values to numeric values is the pandas `get_dummies` function. The function returns a new column for each unique category values. The new column contains 0 (False) or 1 (True) to represent whether the row has the attributed category value.

For example, three sample records in `cars` dataset

| index  |safety_level   |  
|---|---|
| 0  | low  | 
| 1  | med  |  
| 2  | high  |  

through `pandas.get_dummies()` the `level_safety` column will be translated into the following table:

| index  | low  | med  | high  |
|---|---|---|---|
| 0  | 1  | 0  | 0  |
| 1  | 0  | 1  | 0  |
| 2  | 0  | 0  | 1  |

*** =instructions
Create a feature set of categorical variables with `get_dummies` with all columns except for `customer_rating` with the following steps:

1. Create a new dataframe without `customer_rating` (target columns)
2. Create an `X` dataframe with `get_dummies`
3. Keep the column names of X dataframe to `feature_col_names`
4. Print the first few rows of new dummies dataframe, X

*** =hint
- Columns can be explicitly excluded with `pd.drop(DataFrame.drop(column_name, axis=1, inplace=False))`
- The correct syntax for `get_dummies` is `pd.get_dummies(dataset)`
- Print the first few rows of any dataframe with `df.head()`

*** =pre_exercise_code
```{python}
# I read the data in here again, just in case
import pandas as pd

cars = pd.read_csv('http://s3.amazonaws.com/assets.datacamp.com/production/course_1742/datasets/cars_dataset_updated.csv')
```

*** =sample_code
```{python}
# 1. Create a new dataframe without `customer_rating` (target columns)
new_df = 

# 2. Apply `get_dummies` to new dataframe
X = 

#3. Keep the column names of X dataframe to `feature_col_names`

feature_col_names = 

# 4. Print the first few rows of new dummies dataframe, X

```

*** =solution
```{python}
# 1. Create a new dataframe without `customer_rating` (target columns)
new_df = cars.drop('customer_rating', axis=1)

# 2. Apply `get_dummies` to new dataframe
X = pd.get_dummies(new_df)

# 3. Keep the column names of X dataframe to `feature_col_names`
feature_col_names = X.columns

# 4. Print the first few rows of new dummies dataframe, X
X.head()


```
*** =sct
```{python}
success_msg("Great work!")
```

--- type:NormalExercise lang:python xp:100 skills:2 key:421f80076b
## What Car Features are Most Important? 

You have succesfully cleaned the `cars` dataset and converted all string categorical to unique numbers. The features and target variables may be used to run a decision tree in python `sklearn` package. 

*** =instructions
Run the code provide in the sample section. What are the leading 2 features that influence a customer to give a car the 'very good' rating? 

*** =hint
hint comes here

*** =pre_exercise_code
```{python}
import pandas as pd

cars = pd.read_csv('http://s3.amazonaws.com/assets.datacamp.com/production/course_1742/datasets/cars_dataset_updated.csv')
```

*** =sample_code
```{python}
import pandas as pd
from sklearn.tree import DecisionTreeClassifier
#below packages do not work
#from sklearn.tree import export_graphviz
#from sklearn.externals.six import StringIO
#import pydot

# Encoded categorical features
X = pd.get_dummies(cars.drop('customer_rating', axis=1))
feature_col_names = X.columns

Y = cars.customer_rating.map({'unacc':0, 'acc':1, 'vgood': 2, 'good': 3})

treeclf = DecisionTreeClassifier(max_depth=3, random_state=1)
treeclf.fit(X, Y)

# prints decision tree, packages are not available in workspace at this time
#dot_data = StringIO()  
#export_graphviz(treeclf, out_file=dot_data,  
#                feature_names=feature_cols,  
#                filled=True, rounded=True,  
#                special_characters=True)  
#graph = pydot.graph_from_dot_data(dot_data.getvalue())  
#Image(graph.create_png())  

# print the most important
pd.DataFrame({'feature':feature_col_names,
              'importance':treeclf.feature_importances_}).sort('importance', ascending=False).head()
```

*** =solution
```{python}
#solution code 
```

*** =sct
```{python}
success_msg("Great work!")
```

