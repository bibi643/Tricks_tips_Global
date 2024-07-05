# Function to master

![Static Badge](https://img.shields.io/badge/Python-red) 
![Static Badge](https://img.shields.io/badge/Important_functions-white)

# Source
- TechWithTim:
  - [YT_link](https://www.youtube.com/watch?v=kGcUtckifXc&list=WL&index=1)
- Sergio A Giraldo:
  - [YT_link](https://www.youtube.com/watch?v=_u-3pwdbHeg) > entry_point
  - [YT_link](https://www.youtube.com/watch?v=pdiU4hKfZ7Y&list=WL&index=2) > lambda
  - [YT_link](https://www.youtube.com/watch?v=94Bn5B_-Fsc&list=WL&index=5) > zip
  


# Entrypoint __name__ = __main__


## Example
```python
# In a file modulo.py lets create a function factorial
def factorial(n):
...
...
...
  print(f)
  return f

if __name__ == '__main__':
  factorial(7)
  a=factorial(5)

```
In a new file called entry_point.py
```python
# we want to use the factorial function from modulo.py
from modulo import factorial
def run():
  f=factorial(4)
if __name__ ==' __main__':
  run()

>>>4! = 4*3*2*1
```

Basically the entry point in the modulo.py makes that the factorial(7) and facotrial(5) would only be exectuted if we run factorial() from the modulo.py file.

# Lambda

1 - Is Anonymous > cannot be named.

2 - Can contain the number of  needed arguments.

3 - Has to fit in a single line of code.

```note
lambda arguments: expression
```

```python
strings =['my','world','apple','pear']

s= map(lambda x: x + 's', strings) # 
list(s) # we need to convert into a list

>>> ['mys','worlds','apples','pears']

```

```python
def suma(a,b):
  return a+b

result= suma(a,b)

# Transformation into a lambda function

results= lambda a,b: a+b #results is the identificador

valor = results(a,b) # identificador(argumentos)

```

# zip() and "unzip()"
## zip()

- Creates an iterable object combining different iterable object (**can be of different lenght**) together and automatically handle when one iterable object has more objects than the other.
- This prevents for out of bounds error.
- The created iterable stopped when the shortest input iterable is done.

```python
names =['Tim','Bob', 'Alice','Tom']
ages=[30,13,34]
gender= ['male','male']

combined = list(zip(names,ages,gender))
for name, age in combined:
  print(f'{name} is [age} years old, and is a {gender}")

```
In this case it will only returns 2 elements.

## "unzip()"
unzip() does not exist in python. To unzip, we use *.

```python
pairs=[(1,a),(2,b),(3,c)]
numbers, letters =zip(*pairs) # zip((1,'a'), (2,'b'), (3,'c')) > zip is seeing 3 iterables.

>>> numbers
(1,2,3)
letters
('a','b','c')
```



# map()

Apply a funtion to every single element/item in an iterable object.
```python
strings =['my','world','apple','pear']

lengths= map(len, strings) # Apply len to each item of strings
list(lengths) # we need to convert into a list

>>> #return the length of each element
>>> [2, 5, 5, 4]
```
# filter()

Kind of similar to map(). 
1- Take all the items in the iterable object. 
2- Pass it the a compatible function.
3- If the function returns True, it will keep the item, otherwise it removes it from the results.

```python
def longer_than_4(string):
  return len(string) >4

string = ['my','worlds', 'apple', 'pear']
filtered= filter(longer_than_4, string)
list(filtered)
>>> ['worlds','apple']
```
# enumarate()
Returns a list of tuples (index,value).

[(index_1,value_1),(index__2,value2), (index_n,value_n)]
```python
tasks=['Write', 'Meeting', 'Review']
for index, value in enumerate(tasks):
  print (f'{index + 1}. {tasks}')
```


# sorted()

Sort an iterable object in ascending or descending order depending on our demands.

```python
numbers= [2,4,5,1,8]
sorted_nums =sorted (numbers, reverse=True)

people= [
{'name': 'Alice', 'age':30},
{'name':'Bob','age':23},
{'name':'Jacques', 'age':45}
sorted_people =sorted (people, reverse=True,key= lambda person: person['age']) # Will sort the people list by the age.

```


# help()

Will read the docstring of a function, aka the documentation. Work with built in functions or homemade functions too.

```python
help(name_of_function)
```

# model_selection by GridsearchCV
There are 2 ways to import the module.
Datas are train_test_splited first and then normalised.
In the first example we work with SVM.

```python
from sklearn import svm,model_selection, preprocessing
from sklearn.model_selection import train_test_split
# Creation of the base model
clf=svm.SVC(gamma=0.01,kernel='poly')

# Parameter grid we want to try during the optimisation
parametres={'C':[0.1,1,10],
           'kernel':['rbf','linear','poly'],
           'gamma':[0.001,0.1,0.5]}


# Grid of models with those parameters
grid_clf = model_selection.GridSearchCV(estimator=clf, param_grid=parametres,scoring='accuracy')

# Returns the best parameters of the model with the highest or best scoring.
print(grid_clf.best_params_)

#training of the grid on the train sets

grille = grid_clf.fit(X_train_scaled,y_train)


#Prédiction and confusion matrix
y_pred = grid_clf.predict(X_test_scaled)
pd.crosstab(y_test, y_pred, rownames=['Classe réelle'], colnames=['Classe prédite'])

```


```python
from sklearn.model_selection import GridSearchCV,train_test_split, cross_val_score # This implies GridSearch can be called directly
clf_lr=LogisticRegression(max_iter=1000)
params_lr={'solver':['liblinear','lbfgs'],
          'C':[10**(i)for i in range (-4,3)]}

gridcv=GridSearchCV(estimator=clf_lr,param_grid=params_lr,scoring='accuracy',cv=3)

#training of the new best classifier
gridcv.fit(X_train,y_train)

# Dataframe showing the results 
pd.DataFrame(gridcv.cv_results_)[['params','mean_test_score','std_test_score']]

# Print best params
print(grid_cv.best_params_)

```

If needed check **Nested CV**. Basically it takes different grids and different clfs and returns for each the accuracy etc etc.


# CrossValidation

It exists different types of cross validations
 - Kfold
 - Group Kfold
 - Stratified Kfold
 - Shuffle split

## Kfold

**Cons**: Be careful with unbalenced classes. 
**Pros**: Good for regression.
```python

#KFold
from sklearn.model_selection import KFold

cv_type = Kfold(n_fold,random_state=42) # 5 is usually the number
cross_val_score(model,X,y,cv=cv_type)
```

## Shuffle split
This is a **godd alternative to KFold**
**Cons**: Same as before with Unbalanced claasses.

```python
from sklearn.model_selection import ShuffleSplit
cv_type= ShuffleSplit(n_split,test_size=0.2)
cross_val_score(model,X,y,cv=cv_type)

```

## Stratified KFold
Usually it is the default choice. It makes sure that all the classes are fairly represented in each KFold
```python

from sklearn.model_selection import StratifedKFold
cv_type= StratifiedKfold(n_split)
cross_val_score(model,X,y,cv=cv_type)
```

## Group KFold

**SUPER IMPORTANT**


```python

from sklearn.model_selection import GroupFold
cv_type= GroupKfold(n_train).get_n_split(X,y,groups=X[:,0])
cross_val_score(model,X,y,cv=cv_type)
```
