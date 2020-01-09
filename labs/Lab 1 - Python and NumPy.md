---
jupyter:
  jupytext:
    formats: ipynb,md
    text_representation:
      extension: .md
      format_name: markdown
      format_version: '1.1'
      jupytext_version: 1.2.4
  kernelspec:
    display_name: Python 3
    language: python
    name: python3
---

# Name(s)
Anya Houk


**Instructions:** This is an individual assignment, but you may discuss your code with your neighbors.


# Python and NumPy

While other IDEs exist for Python development and for data science related activities, one of the most popular environments is Jupyter Notebooks.

This lab is not intended to teach you everything you will use in this course. Instead, it is designed to give you exposure to some critical components from NumPy that we will rely upon routinely.

## Exercise 0
Please read and reference the following as your progress through this course. 

* [What is the Jupyter Notebook?](https://nbviewer.jupyter.org/github/jupyter/notebook/blob/master/docs/source/examples/Notebook/What%20is%20the%20Jupyter%20Notebook.ipynb#)
* [Notebook Tutorial](https://www.datacamp.com/community/tutorials/tutorial-jupyter-notebook)
* [Notebook Basics](https://nbviewer.jupyter.org/github/jupyter/notebook/blob/master/docs/source/examples/Notebook/Notebook%20Basics.ipynb)

**In the space provided below, what are three things that still remain unclear or need further explanation?**
1. Does each user have a separate kernel?
2. Is there a way to start up jupyter notebooks locally without using docker? (docker doesn't appear to have linux support)
3. Do just .ipynd files run as separate processes or all files open in jupyter?


## Exercises 1-7
For the following exercises please read the Python appendix in the Marsland textbook and answer problems A.1-A.7 in the space provided below.


## Exercise 1

```python
import numpy as np
a = 2*np.ones((6,4), dtype=int)
print(a)
```

## Exercise 2

```python
b = np.ones((6,4), dtype=int) + 2*np.eye(6,4, dtype=int)
print(b)
```

## Exercise 3

```python
#a * b multiplies two matrices together element-wise
# hoever, np.dot(a,b) takes the dot-product which multiplies row by column elements and then sums
#so the shape 6X4 and 6x4 are not compatible because the row number of a should match the column number of b
```

## Exercise 4

```python
#a is transposed from 6x4 to 4X6
#taking the dot-product of a4X6 and b6X4 results in a 4x4 (row size of a and col size of b) matrix
print(np.dot(a.transpose(), b))

#b is transposed from 6x4 to 4X6
#taking the dot-product of a6X4 and b4X6 results in a 6x6(row size of a and col size of b) matrix
print(np.dot(a, b.transpose()))

```

## Exercise 5

```python
def func():
    print("a func that prints")
func()
```

## Exercise 6

```python
def randArr(low, high, size):
    arr = np.random.randint(low, high, size)
    print("Random Array Stats: ")
    print("min: ", arr.min())
    print("max: ", arr.max())
    print("sum: ", arr.sum())
    print("mean: ", np.mean(arr))

randArr(0, 22, 5)
randArr(0, 22, 5)
randArr(0, 22, 5)

    
```

## Exercise 7

```python
#loops
def numOnes(arr):
    count = 0
    for row in arr:
        for elem in row:
            if (elem == 1):
                count+=1
    return count

#where
def useWhere(arr):
    res = np.where(arr == 1)
    return np.size(res[0]) 
    

arr = np.ones((6,4), dtype=int) + 2*np.eye(6,4, dtype=int)
print(numOnes(arr))
print(useWhere(arr))


```

## Excercises 8-???
While the Marsland book avoids using another popular package called Pandas, we will use it at times throughout this course. Please read and study [10 minutes to Pandas](https://pandas.pydata.org/pandas-docs/stable/getting_started/10min.html) before proceeding to any of the exercises below.


## Exercise 8
Repeat exercise A.1 from Marsland, but create a Pandas DataFrame instead of a NumPy array.

```python
import pandas as pd

a = pd.DataFrame(2*np.ones((6,4), dtype=int))
print(a)
```

## Exercise 9
Repeat exercise A.2 using a DataFrame instead.

```python
b = pd.DataFrame(np.ones((6,4), dtype=int) + 2*np.eye(6,4), dtype=int)
print(b)
```

## Exercise 10
Repeat exercise A.3 using DataFrames instead.

```python
a * b

#a.dot(b)
#this does work for the same reason stated in A.3
```

## Exercise 11
Repeat exercise A.7 using a dataframe.

```python
#loops
def numOnes(arr):
    count = 0
    for row in arr:
        for elem in row:
            if (elem == 1):
                count+=1
    return count

#where
def useWhere(arr):
    res = np.where(arr == 1)
    return np.size(res[0]) 
    

a = pd.DataFrame(2*np.ones((6,4), dtype=int))
print(numOnes(arr))
print(useWhere(arr))
```

## Exercises 12-14
Now let's look at a real dataset, and talk about ``.loc``. For this exercise, we will use the popular Titanic dataset from Kaggle. Here is some sample code to read it into a dataframe.

```python
titanic_df = pd.read_csv(
    "https://raw.githubusercontent.com/dlsun/data-science-book/master/data/titanic.csv"
)
titanic_df
```

Notice how we have nice headers and mixed datatypes? That is one of the reasons we might use Pandas. Please refresh your memory by looking at the 10 minutes to Pandas again, but then answer the following.


## Exercise 12
How do you select the ``name`` column without using .iloc?

```python
titanic_df['name']
```

## Exercise 13
After setting the index to ``sex``, how do you select all passengers that are ``female``? And how many female passengers are there?

```python
titanic_df.set_index('sex', inplace=True)
titanic_df.loc['female']
titanic_df.loc['female'].shape[0]
```

## Exercise 14
How do you reset the index?

```python
titanic_df.reset_index()
```

```python

```
