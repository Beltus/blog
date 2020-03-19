---
layout: single
published: true
title: Simple Dataset Exploration Techniques For Machine Learning.
collection: sc
author_profile: true
read_time: true
categories: [Blog] #[tutorials]
excerpt : "It is mind-blowing and fascinating how every part of our daily lives is being affected by machine learning driven applications and most of us go by our mundane life routines oblivious to this."
header :
    overlay_image: "https://beltus.github.io/vision/images/galaxy.png"
    teaser: "https://beltus.github.io/vision/images/ml.png"

comments: true
toc: true
toc_sticky: true
---

We live in world where data is millions of new datasets are created and posted per day. The unwieldy challenge that arises is how can we manage this crazy inflow of data and make the most out of it. If you are new to data science, it can be daunting and overly overwhelming to know how to deal with so much information.
in this article, I will like to provide the very basic techniques which will get your feet wet and your saliva inflow activated to dive even deeper in to world of Big Data using the powerful python library pandas.

In this article I share with you the general format for which most datasets are stored with explicitly explanations for each section of the dataset. As an icing to the cake i will provide links to the sites that are considered the big guns of dataset collection You will be able to download your own datasets and perform diligently investigation of its contents and the relationships between the different facets that make it up.

Here is the pitfall
> Never dive head first into using any dataset without properly having a holistic understanding of how it was structured by the creators and how the independent variables relate with the dependent variable. This will cause you painful headaches in the later parts of your machine learning project and no one likes headaches.

Okay, lets get to it

When I started my journey towards data science, I struggled with understanding exactly how to explore a dataset and make some meaningful, intuitive pre-analysis of the contents. Most sources online only provided incomplete or insufficient techniques. This article will give any newbie in data science an idea of the content of their dataset before proceeding ahead.

## Note that, there are lots of terminologies used to describe rows and columns of a dataset. A row is called an instance, datapoint, sample, example. A column can be called a feature, attribute, predictor, etc. I might use any of these interchangeably.

## Step 1: Importing Revelant Libraries
For dataset exploration, we need to import pandas and also numpy for some mathematical manipulations. The former with an alias of pd and latter with an alias of np.
```python
import numpy as np
from sklearn import model_selection
from sklearn import svm
import pandas as pd
import zipfile

```

## Side Step: List all Files in Dataset Folder
```python
from subprocess import check_output
print(check_output(["ls" , "/home/beltus/image/Data Science/datasets"]).decode("utf8")) #List all files in dataset folder
print(check_output(['ls', "/home/beltus/image/Data Science/datasets/"]).decode("utf8"))
```


## Step 2: Load Dataset into Code File - Jupyter NoteBook(For me)

After importing the pandas library, we then use it's ***.read_csv()*** to read the dataset and save it as a Dataframe object in the object ***dataset***
```python
dataset = pd.read_csv("./datasets/airline-safety.csv")

```

## Step 3: Display the number of Observations(Samples) and the number of Features(Attributes) In your Dataset
It is important to know how many datapoints are present in your dataset. This is achieved with the code block below.
```python
#check number of rows and colums in the dataset
rows, columns = dataset.shape
print("Number of Samples or Observations: " , rows)
print("Number of Attributes or Features" , columns)
```

## Step 4: Take a Quick Peak at the contents of your Dataset
What exactly is the content of your dataset? In order to see this, you can use the Dataframe ***head()*** method. Specifying 10 means it shows the first 10 rows of your dataset.
```python
pd.dataset.head(10) # List the first 10 rows of dataset
#displays the last 10 rows of your dataset
dataset.tail(10)
```
* If the dataset has a large number of columns, you won't be able to see all the rows displayed, Unless you are working with a gigantic screen. Luckily, with the code code snippet below, you can scroll along all columns.

```python
pd.set_option("display.max_columns" , None) #permits all the attributes(columns) to be displayed
dataset.head(10)

```

## Step 5: Display Basic Statistics.
Lets take a step further into gaining some statistical insights of our dataset. The ***.describe()*** methods provides some basic statistical information such as mean, standard deviation, etc of each of the numeric columns of our Dataframe

```python
dataset = pd.describe()

```

* **count** row can be especially useful as it gives a clue of any missing values in your data that could negatively affect the performance of your machine learning model.


## Step 6: Removing Irrelevant Features(Columns)
In building a machine learning model, some features or columns might have zero contribution to the performance of the prediction. You can eliminate any unwanted column by using the snippet below


```python
dataset = pd.read_csv("./datasets/airline-safety.csv")

```

## Step 7: Load Dataset into Code File - Jupyter NoteBook(For me

After importing the pandas library, we then use it's ***.read_csv()*** to read the dataset and save it as a Dataframe object in the object ***dataset***
```python
dataset = pd.read_csv("./datasets/airline-safety.csv")

```

## Step 2: Load Dataset into Code File - Jupyter NoteBook(For me)

After importing the pandas library, we then use it's ***.read_csv()*** to read the dataset and save it as a Dataframe object in the object ***dataset***
```python
dataset = pd.read_csv("./datasets/airline-safety.csv")

```



https://realpython.com/pandas-python-explore-dataset/
https://towardsdatascience.com/exploring-the-data-using-python-47c4bc7b8fa2
https://towardsdatascience.com/a-gentle-introduction-to-exploratory-data-analysis-f11d843b8184
