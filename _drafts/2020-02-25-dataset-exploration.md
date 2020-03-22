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

If you just clicked the download button of that dataset for your machine learning project and have no modicum of clue what is in your dataset, what to do with the data, where to start, then look no further.


We live in world myriads of new datasets are created on a daily basis. The unwieldy challenge that arises is how can we manage this crazy onslaught of data and make the most out of it. If you are new to data science, it can be daunting and overly overwhelming to get started with understanding what you have in hand. I faced same problem, as I could not find a comprehensible article that explain what I could do with datasets after downloading.

It is imperative every rookie in data science familiarize themselves with data, because that is fundamental backbone of AI. Being able to download datasets and just explore them for fun can be of immense benefit to any aspiring data scientist.

in this article, I provide the very basic techniques and methods that you can apply in order to have a holistic idea of what the contents of your dataset look like. The relationship between some attributes , etc. This should be enough to get your mouth wet and activate the flow of dopamine in your system so that you frictionlessly dive even deeper in to the universe of datascience.

*****Delete from here down

In this article I share with you the general format for which most datasets are stored with explicitly explanations for each section of the dataset. As an icing to the cake i will provide links to the sites that are considered the big guns of dataset collection You will be able to download your own datasets and perform diligently investigation of its contents and the relationships between the different facets that make it up.

Here is the pitfall
> Never dive head first into using any dataset without properly having a holistic understanding of how it was structured by the creators and how the independent variables relate with the dependent variable. This will cause you painful headaches in the later parts of your machine learning project and no one likes headaches.

Okay, lets get to it

When I started my journey towards data science, I struggled with understanding exactly how to explore a dataset and make some meaningful, intuitive pre-analysis of the contents. Most sources online only provided incomplete or insufficient techniques. This article will give any newbie in data science an idea of the content of their dataset before proceeding ahead.

## Note that, there are lots of terminologies used to describe rows and columns of a dataset. A row is called an instance, datapoint, sample, example. A column can be called a feature, attribute, predictor, etc. I might use any of these interchangeably.


## Prerequisite

[Pandas](https://pandas.pydata.org/pandas-docs/stable/index.html#module-pandas) is an open source, BSD-licensed library providing high-performance, easy-to-use data structures and data analysis tools for the Python programming language.

 For this article that is what I will be using as it is one of the most popular libraries for machine learning. Sometimes we also use Matplotlib and Seaborn for visualization purposes. For those those who have never used Pandas library do not break a sweat over it. I wrote this article with you in mind.

 Install Pandas
 pip install pandas

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
Lets take a step further into gaining some statistical insights of our dataset. The ***.describe()*** methods provides some basic statistical information such as mean, standard deviation, etc of each of the numeric columns of found in our dataset.

```python
dataset = pd.describe()

```

* **count** row can be especially useful as it gives a clue of any missing values in your data that could negatively affect the performance of your machine learning model.


## Step 6: Removing Irrelevant Features(Columns) - Iris dataset for this example
In building a machine learning model, some features or columns might have zero contribution to the performance of the prediction. Infact they are totally worthless in solving the task at hand. I consider these noise that needs to be removed. You can eliminate any unwanted column by using the snippet below

```python
clean_dataset = dataset.drop(["name of column to remove"] , axis = 1)
clean_dataset.head()
```
Note assigning it to a new variable(clean_dataset) is the smart move, as the*drop()* method doesn't delete the column permanently ffrom the dataset for which the function is called. You can test this by trying *dataset.help()*. Thesame dataset, with all its columns.

## Step 7: Number of Unique Samples in Dataset Iris dataset for this example
This next code snippet is often very useful in machine learning especially when we are dealing with classification problems. It helps you to know the number of samples that belong to a particular category. An example is shown below
```python
dataset.groupby('column_name').size()

```
## Renaming the Column Headers
Datasets can be messy at times with wierd column names given by the creators of the datasets. You don't have to stick with these. If you dont like it, just change it like so.

```python
#list of column names
new_col_names = ['ID' , 'Region' , 'Country' , 'Latitude', 'Longitude' , 'Dates' , 'Confirmed_Cases' , 'Fatal']

# assign the names to your dataset
dataset.columns = new_col_names

```
Sometimes, you just need to change that specific column name that sounds like gibberish to your ears. Just do this


```python
dataset.rename(columns = {'old_col_name': 'new_col_name'}, inplace = True)

```

## Histogram Plot.
Lets spice things up a little, with visualizations.The first and most commonly use visualization tool is the [histogram](https://www.wikiwand.com/en/Histogram). We can optional pass bin size as the only argument. That's it.

```python
dataset["column_name"].plot.hist()

```
If you are curious and interested in visualizing the histogram plots of all your features, you can generate generate multiple plots as indicated below. *Subplot* creates a histogram plot for each column and *layout* specifies the number of plot per row and column.


```python
dataset.plot.hist(subplots = True, layout = (2,2) , figsize = (10,10) , bins = 20)

```
![](https://beltus.github.io/vision/images/multiplot.png)


## Bar Plot
This is an interesting visualization tool. Here is an example of the bar plot in the COVID-19 dataset.
```python
dataset.groupby('country').ConfirmedCases.mean().sorted_value(ascending=False)[:5].plot.bar()
```
I Grouped data by country and calculated the mean of the confirm cases and ordered it in descending order, then finally plotting a bar chart of the countries with the highest confirmed cases.

![](https://beltus.github.io/vision/images/covid.png)

## Scatter plot
Last but far from least is the scatter plot. Generally used to show the relationship between 2 columns or feature in your dataset. Note that only numeric columns can be plotted. 

```python
dataset.plot.scatter(x='ConfirmedCases' , y = 'Fatalities' , title = "Corona Dataset")

```



https://realpython.com/pandas-python-explore-dataset/
https://towardsdatascience.com/exploring-the-data-using-python-47c4bc7b8fa2
https://towardsdatascience.com/a-gentle-introduction-to-exploratory-data-analysis-f11d843b8184
https://towardsdatascience.com/introduction-to-data-visualization-in-python-89a54c97fbed
