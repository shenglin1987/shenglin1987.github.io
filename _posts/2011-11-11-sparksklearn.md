## This page introduces how to use sparksklearn to accelerate the parameter tuning by scikit-learn. 

Code is the best way to talk. 

## this is the code using gridsearch to tune a random forest classier in scikit learn
-----------------------------------------------------------
...
from sklearn import grid_search, datasets
from sklearn.ensemble import RandomForestClassifier
from sklearn.grid_search import GridSearchCV
digits = datasets.load_digits()
X, y = digits.data, digits.target
param_grid = {"max_depth": [3, None],
              "max_features": [1, 3, 10],
              "min_samples_split": [1, 3, 10],
              "min_samples_leaf": [1, 3, 10],
              "bootstrap": [True, False],
              "criterion": ["gini", "entropy"],
              "n_estimators": [10, 20, 40, 80]}
gs = GridSearchCV(RandomForestClassifier(), param_grid=param_grid)
gs.fit(X, y)
...
-----------------------------------------------------------
## accelerate via spark_sklearn ##
...
from sklearn import grid_search, datasets
from sklearn.ensemble import RandomForestClassifier
# Use spark_sklearn’s grid search instead:
from spark_sklearn import GridSearchCV
digits = datasets.load_digits()
X, y = digits.data, digits.target
param_grid = {"max_depth": [3, None],
              "max_features": [1, 3, 10],
              "min_samples_split": [1, 3, 10],
              "min_samples_leaf": [1, 3, 10],
              "bootstrap": [True, False],
              "criterion": ["gini", "entropy"],
              "n_estimators": [10, 20, 40, 80]}
gs = GridSearchCV(RandomForestClassifier(), param_grid=param_grid)
gs.fit(X, y)
...
-----------------------------------------------------------
###We do not need to change the body code. Just import new APIs from spark_sklearn
