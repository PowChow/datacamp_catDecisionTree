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

As a data scientist, you will may need to translate categorical variables into numerical variables for analysis, visualization, and modeling. Many python packages are not able to analyze categorical values in string format. 

Explore the `cars` data: 

- Print out the first few rows and all columns by using `head()`    
- Print out list of all columns variables by using `columns`
- 
By looking at columns names alone, which `cars` dataset variables are categorical?
*** =instructions
- Buying Price
- Number of Doors
- Customer Rating
- all of the above

*** =hint
- The `cars` dataset has been preloaded in this exercise as a pandas dataframe. Type "cars" into command line to print out all the values of cars. 
- Do you remember the panda's syntax for head() and columns? It is `DataFrame.head()` and `DataFrame.columns`. Substitute your dataset in for DataFrame.

*** =pre_exercise_code
```{python}
#pre load the dataset into the exercise
import pandas as pd

cars = pd.read_csv('http://s3.amazonaws.com/assets.datacamp.com/production/course_1742/datasets/cars_dataset_updated.csv')
print('cars dataset available to workspace')
```

*** =sct
```{python}
test_mc(5) # if 2 is the correct option.
success_msg("This one can be tricky!")

```

--- type:NormalExercise lang:python xp:100 skills:2 key:7d067101e2
## Find Categorical Variables

Sometimes it is not intuitive to see which variables are categorical by simply eyeballing a few rows or inferring from the column names. 

Pandas `describe()` can help identify categorical variables through quick summary statistics. You can also determine all the unique values by column with `unique()` function. 

__Notice__: If you have a mixed type dataset with both continuous and categorical variables. The `describe()` function will default to showing summary statistics for continous variable. In cases of mixed type, the data set can be split up between variable types.  


*** =instructions
- Print summary statistics of `cars` dataset with describe()
- We are interested in the range or ratings customers gave to cars in this dataset. Print out the unique values for the `cusomter_rating` and `safety_level` columns. 

*** =hint
- What is the syntax using `describe()` pandas dataframes? DataFrame.describe()
- The pandas `unique()` function applies to Series or columns in pandas dataframes. What is the syntax for using `unique()`? df['column_name'].unique()

*** =pre_exercise_code
```{python}
# I read the data in here again, just in case
import pandas as pd

cars = pd.read_csv('http://s3.amazonaws.com/assets.datacamp.com/production/course_1742/datasets/cars_dataset_updated.csv')
print('cars dataset available to workspace')
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
# for categorical variables describe() provides the count of unique categorical variables, most frequent category appearing in that columns, total frequency

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
## Convert Categorical to Numerical Values 

Use pandas get_dummy method to convert any one variables and join back to dataframe

*** =instructions
- instruction 1
- instruction 2

*** =hint
hint comes here

*** =pre_exercise_code
```{python}
# pec
```

*** =sample_code
```{python}
# sample code
```

*** =solution
```{python}
# solution code
```

*** =sct
```{python}
success_msg("Great work!")
```
--- type:NormalExercise lang:python xp:100 skills:2 key:1b317f1a80
## Find Categorical Variables

Sometimes it is not intuitive to see which variables are categorical by simply eyeballing a few rows or inferring from the column names. ## ADD THE PLOTTING FEATURE ONLY 

Pandas `describe()` can help identify categorical variables through quick summary statistics. 

As well as plotting the relationships between every variable and distribution of columns through seaborn `pairplot()` can further illustrate variable types. However, it is difficult to plot categorical variables as strings so let's do this after we convert these to numbers. 

*** =instructions
- Generate summary statistics of `cars` dataset
- Visualize pairwise relationship of variables using seaborn, remember to import the package

*** =hint
- What is the syntax using `describe()` with a pandas dataframe? DataFrame.describe()
- Did you remember to import the seaborn package before you tried to plot? 
- seaborn.pairplot method can provide some assistance with your plot

*** =pre_exercise_code
```{python}
# pec
```

*** =sample_code
```{python}
# Generate summary statistics of dataset

# visualize pairwise relationship of variables using seaborn

```

*** =solution
```{python}
# print summary statistics of dataset
# for categorical variables describe() provides the count of unique categorical variables, most frequent category appearing in that columns, total frequency
cars.describe()

# visualize variables with seaborn
import seaborn as sns

sns.pairplot(cars) #insert dataset here
```

*** =sct
```{python}
success_msg("Great work!")
```


--- type:NormalExercise lang:python xp:100 skills:2 key:421f80076b
## Use dataframe with created categorical variables to produce a decision tree

Use decision tree with dummy values to determine what categories produce higher ratings

*** =instructions
- instruction 1
- instruction 2

*** =hint
hint comes here

*** =pre_exercise_code
```{python}
# pec
```

*** =sample_code
```{python}
# sample code
```

*** =solution
```{python}
# solution code
```

*** =sct
```{python}
success_msg("Great work!")
```

