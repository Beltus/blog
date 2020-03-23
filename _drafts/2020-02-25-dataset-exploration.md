---
layout: single
published: true
title: Simple Yet Powerful Dataset Exploration Techniques For Machine Learning.
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

***COVID-19 dataset download complete!***. What now? You must be thinking.

That is exactly what I used to think when I started this long yet exciting journey into the planet of datascience.

I will stare at a dataset folder on my computer screen like a sheep that just lost it's sheperd. Lost, confused and utterly frustrated I find myself watching a youtube clip of **Sheldon - Big Bang Theory**. Slowly but surely mission failed.

If you are new to data science, it is daunting and  overwhelming to get started with understanding the contents of any dataset amid the ocean of datasets existing today. Every second that ocean expands further.

It is imperative every rookie in data science familiarize themselves with the very basic techniques of exploring dataset, because it is the fuel that powers AI.

Working on a machine learning project without first of all understanding the dataset you are working with, it is like trying to build a skyscraper without a blueprint. Think about that for a second.

In today's article, I will share a couple of basic yet powerful exploration techniques which you can apply to almost any dataset. These techniques will help you break through datasets. Not only that, you will have a holistic understanding of the dataset you are working with. These should be enough to activate the flow of dopamine in your system so that you can frictionlessly complete your machine project while having fun.


Okay, enough of the talk. Lets get to it.

*** Delete this****
When I started my journey towards data science, I struggled with understanding exactly how to explore a dataset and make some meaningful, intuitive pre-analysis of the contents. Most sources online only provided incomplete or insufficient techniques. This article will give any newbie in data science an idea of the content of their dataset before proceeding ahead.

## Note that, there are lots of terminologies used to describe rows and columns of a dataset. A row is called an instance, datapoint, sample, example. A column can be called a feature, attribute, predictor, etc. I might use any of these interchangeably.

*****

## Prerequisite

 For this article, we will be using [Pandas](https://pandas.pydata.org/pandas-docs/stable/index.html#module-pandas) which is one of the most popular data structure libraries for machine learning. It has many interesting built-in fucntions which we will be exploring shortly.

 Some people use pandas together with [Matplotlib](https://matplotlib.org/index.html) and [Seaborn](https://seaborn.pydata.org/) statistical data visualization purposes. Feel free to check them out.

For those who have never used Pandas library before do not break a sweat over it. I wrote this article with you in mind.

In other to use pandas library, we first need to install it.

```python
 pip install pandas
```

I am using [jupyter notebook]() to run all the codes in this article. If you don't have jupyter notebook setup yet. I got you covered. Check out the [Datacamp site](https://www.datacamp.com/community/tutorials/tutorial-jupyter-notebook?utm_source=adwords_ppc&utm_campaignid=1455363063&utm_adgroupid=65083631748&utm_device=c&utm_keyword=&utm_matchtype=b&utm_network=g&utm_adpostion=&utm_creative=278443377092&utm_targetid=aud-299261629574:dsa-473406581035&utm_loc_interest_ms=&utm_loc_physical_ms=1012782&gclid=CjwKCAjwvOHzBRBoEiwA48i6ApXegXohUEtd-CYIflVV6eQ6vET2cwBXJKakwZSh0BSB0clVntPNmxoC8BsQAvD_BwE)

At the end of this article, I will share a link to my github page where you can access the complete notebook. So stay frosty till the end.

## Import Relevant Libraries
To have access to the amazing pandas functions, we need to import it into our code. I imported it with the alias *pd*

```python
import pandas as pd
import zipfile
```

## Load Dataset into Memory.

The pandas ***.read_csv()*** method reads the dataset file and saves it as a pandas [Dataframe](https://www.geeksforgeeks.org/python-pandas-dataframe/) object. Think of a dataframe as a table with labels rows and columns. Here I am using the COVID-19 Dataset from [Kaggle](https://www.kaggle.com/)

```python
dataset = pd.read_csv('./datasets/corona-virus-report/covid_19.csv')

```
At the end of the article, I will provide links to all the different datasets I used in this article. So fret about it.

## Display the Number of Samples (Observations) in Dataset.
For any dataset you come across, it is important to know the number of data  points or training examples present in your dataset. This is simply the number of rows and columns.

```python
#check number of rows and colums in the dataset

rows, columns = dataset.shape
print("Number of Samples: " , rows)
print("Number of Attributes or Features" , columns)
```
If you interesting knowing just the number of rows, just do this.
```python
#Prints the number of datapoints(rows)
print(len(dataset))
```
## Take a Quick Peak at the Contents of your Dataset
What exactly is the content of your dataset? Pandas ***head() and tail()*** helps you with that. By default ***head()*** prints the **first 5 rows** and ***tail*** the **last 5 rows** of your dataset.

```python
pd.dataset.head() # List the first 10 rows of dataset
#displays the last 5 rows of your dataset
dataset.tail()
```
![](https://beltus.github.io/vision/images/cv_view.png)

You can as well specify the number of rows you want to display by passing the number as an argument to the functions.
```python
#prints the first 10 rows
pd.dataset.head(10) # List the first 10 rows of dataset
#displays the last 10 rows of your dataset
dataset.tail(10)
```

Sometimes your dataset will have a large number of columns such that you won't be able to view them all.Unless you are working with a gigantic computer screen. Luckily, with the code code snippet below, you can scroll left and right to see everything. Cool right?

```python
#permits all the attributes(columns) to be displayed
pd.set_option("display.max_columns" , None) #permits all the attributes(columns) to be displayed
dataset.head()

```
![](https://beltus.github.io/vision/images/extend_column.png)


## Display Interesting Statistical Information.
Lets take a step further into gaining some statistical insights of our dataset. Personally, the  **[.describe()](https://pandas.pydata.org/pandas-docs/stable/reference/api/pandas.DataFrame.describe.html)** method is a *must-know* function.  

It provides some invaluable statistical information such as count, [mean](https://www.wikiwand.com/en/Mean), [standard deviation](https://www.wikiwand.com/en/Standard_deviation), etc of each of the numeric columns found in our dataset.

```python
dataset = pd.describe()

```
![](https://beltus.github.io/vision/images/describe.png)


* **count** row can be especially useful as it gives a clue of any missing values in your data that could negatively affect the performance of your machine learning model.


## Removing Irrelevant Column
In building a machine learning model, some features or columns might have zero contribution to the performance of the prediction. You can eliminate any unwanted column by using the snippet below. *Axis* specifies that it is column.

I dropped the Lat and Long columns in the COVID-19 dataset

```python
clean_dataset = dataset.drop(['Lat' , 'Long'], axis = 1)
clean_dataset.head()
```
![](https://beltus.github.io/vision/images/lat.png)

Note: It is good practice to assign the modified dataset to a new variable.

## Step 7: Number of Unique Samples in Dataset Iris dataset for this example
This next code snippet is often very useful in machine learning especially when we are dealing with classification problems. It helps you to know the number of samples that belong to a particular category. An example is shown below
```python
dataset.groupby('column_name').size()

```
## Renaming Weird Column Names
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

link to Kaggle COVID-19 [Dataset](https://www.kaggle.com/imdevskp/corona-virus-report)

https://realpython.com/pandas-python-explore-dataset/
https://towardsdatascience.com/exploring-the-data-using-python-47c4bc7b8fa2
https://towardsdatascience.com/a-gentle-introduction-to-exploratory-data-analysis-f11d843b8184
https://towardsdatascience.com/introduction-to-data-visualization-in-python-89a54c97fbed
