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

As a data scientist, you will may need to translate categorical variables into numerical variables for analysis, visualization, and modeling. 

Explore the `cars` data: 

- Print out the first few rows and all columns by using `head()`    
- Print out list of all columns variables by using `columns` 

*** =instructions
By the columns names alone, which `cars` dataset variables are categorical?
- buying_price
- number_of_doors
- luggage_capacity
- customer_rating

*** =hint
- The `cars` dataset has been preloaded in this exercise as a pandas dataframe. Type "cars" into command line to print out all the values of cars. 
- Do you remember the panda's syntax for head() and columns? It is df.head() and df.columns. Substitute your dataframe for "df".

*** =pre_exercise_code
```{python}
#pre load the dataset into the exercise
import pandas as pd

cars = pd.read_csv('./datasets/cars_dataset_updated.csv')
print('cars dataset available to workspace')
```

*** =sct
```{python}
test_mc([1,2,3,4]) # if 2 is the correct option.
```

--- type:NormalExercise lang:python xp:100 skills:2 key:7d067101e2
## Find Categorical Variables

Sometimes it is not easy to eyeball categorical variable just by looking at  

Use panda functions to determine which variables are categorical - describe() and unique() and plot to check

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

--- type:NormalExercise lang:python xp:100 skills:2 key:a9baf21993
## Create panda series categorical values; pandas 'categorical' var type

Explictly identify categorical variables in your dataframe. If not, you'll need to individually take variables 

use pandas categorical method to create a series of categorical variables

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

--- type:NormalExercise lang:python xp:100 skills:2 key:cbb6428a5f
## Convert variables into categorical values using Get_Dummy

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

