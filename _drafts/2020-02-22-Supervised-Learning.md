---
layout: single
published: false
title: Supervised and Unsupervised Learning Demystified
collection: sc
author_profile: true
read_time: true
categories: [Blog] #[tutorials]
excerpt : "It is mind-blowing and fascinating how every part of our daily lives is being affected by machine learning driven applications and most of us go by our mundane life routines oblivious to this."
header :
    overlay_image: "https://beltus.github.io/vision/images/supervised.png"
    teaser: "https://beltus.github.io/vision/images/ml.jpg"
comments : true
toc: true
toc_sticky: true
---

## Supervised and unsupervised Learning
In my previous article on [Machine Learning Explained]() I gently introduced what machine learning was and mentioned that it could be categorized broadly into Supervised and unsupervised learning. In this article, while keeping things simple, I will dive a little deep into explicitly explaining what exactly these 2 categories of machine learning mean.
As usual my objective is to explain these concepts in such a way that even a beginner or non-tech person can digest the information without getting constipated by it's complexities.
With that out of the way,I guess its time to start answering the big questions of the day.

## What is Supervised Learning?

Supervised machine learning involves the training of computer system using data that is explicitly **Labeled**. Labeled data here means that the input and desired output (target) is known. The machine learning algorithm (model) learns from this labeled data through an iterative process which then enables it to perform future predictions.
For example,

Let's imagine that machine learning algorithms are like math students who are given vast amounts of practice problems(data) and instructed to find methods for solving them by finding patterns between the information within these problems and their associated answers(output). The objective then becomes to be able to find the most effective data (practice problems) to feed to the most effective algorithms (learning styles), in order to obtain the best performance.

Supervised learning problems are further divided into 2 sub-classes - **Classification and Regression**. The only difference between these 2 sub-classes is the types of output or target the algorithm aims at predicting which is explained below. 

## 1. Classification Problem
## image of classification
In classification, the objective is to identify which category an object (input) belongs to. For example, we can be interested in determining if an image contains a **dog or cat**, color red or black, email spam or genuine, patient has **HIV** or **Not**. Classifications problems in which the categorical target takes only 2 classes as mentioned in the examples above are known as **Binary Classification problems**. On the other hand, if the target output takes more than 2 values  it is a **Multiclass classification** problems. For example; classifying types of flowers, types of cars etc



## 2. Regression Problem

## image of regression
A regression problem is when the output variable to be predicted is a real or continuous value. This is contrary to the classification as seen above. Let's take for example, you might be interesting in determining the **weights** of men living in Kumbo (google it :) ), **salaries** of teachers in Cameroon etc. Weights and salaries are numeric values for example 80.5kg for weight or $5000 for salaries


Many different models can be used, the simplest is the linear regression. It tries to fit data with the best hyper-plane which goes through the points.


## Just for Fun
I promise this is going to be a very simple exercise just to get your brains stimulated and cement the differences between Regression and Classification. If you are up for this lets go...

> Which of the following is/are classification problem(s)?
 1. Predicting the gender of a person by his/her handwriting style
 2. Predicting house price based on area
 3. Predicting whether monsoon will be normal next year
 4.Predict the number of copies a music album will be sold next month

At the end of this article Im gonna provide the answers so stay frosty lets keep going.



## Supervised Machine Learning Algorithms For Classification and Regression.

Think of these algorithms inline with the class analogy stated above, as the different methods that students developed from solving loads of problems(labeled input data). Which of these algorithms performs best in a specific classification and regression problem, is your responsibility.

Staying true to my word of keeping things simple. Here is a list of the most common algorithms used to solve supervised machine learning problems based on specific characteristics of the problem.

* [Support Vector Machines](https://www.wikiwand.com/en/Support_Vector_Machines)
* Linear regression
* Logistic regression
* Naive Bayes
* Linear discriminant analysis
* Decision trees
* Random Forest
* K-nearest neighbor algorithm
* Neural Networks (Multilayer perceptron)
* Similarity learning


For more information on the different algorithms, Check out the [scikit-learn website](https://scikit-learn.org/stable/supervised_learning.html#supervised-learning) and also the reference links at the end of the article.


Some interesting applications of classification problems are in spam detection, Image Recognition, Speech recognition among others.

Lets chill on brains with this mind-blowing fact before we head on..
>Pharaoh Ramesses II is the only Egyptian Pharaoh that was ever issued a [passport](https://www.ancient-origins.net/history-famous-people/mummy-passport-0010944) and boarded a plane to France. If you in doubt check out his passport below.

##image of Pharaoh Ramesses II


## Unsupervised Machine learning
Contrary to supervised machine learning, in unsupervised machine learning, the model is fed with data that has no human pre-existing labels. It is up to the algorithm to find hidden structure, patterns or relationships in the data.

Let me share this analogy with you.
>Imagine you have no modicum of a clue how to swim and unfortunately your friends take you out for a pool party and intentionally push you in. You are required to figure out how to swim and get yourself out of that freezing pool.

In this analogy, **you** are the **model(algorithm)** and the **pool** is the **data**. There is no swimming instructor to teach you how to swim, hence the name **unsupervised**


Just like supervised learning, unsupervised learning can be split into 2 types i.e

## 1. Clustering Analysis Technique
![](https://beltus.github.io/vision/images/cluster.jpeg)

In Clustering Analysis, the algorithm is fed with unlabeled data and it aims at dividing the data into groups called clusters based on some similarity or dissimilarity criteria. Data points that are similar are grouped under the same cluster, just as is illustrated in the image above.  

Clustering  can be classified into **Exclusive Clustering, Overlapping Clustering, Hierarchical Clustering, Probabilistic Clustering** which I will not go into this in this article but more information can be found in the links at the end of the article.

Here are some of the most commonly used clustering algorithms in machine learning.
* Hierarchical clustering
* K-means clustering
* K-NN (k nearest neighbors)
* Principal Component Analysis
* Singular Value Decomposition
* Independent Component Analysis

For the curious reader, please refer to the links at the end of the article for more information on these techniques.


## 2. Association Rule Technique

In association problems, the model learns the relationship between data and then comes up with certain rules. This unsupervised technique is about discovering interesting relationships between variables in large databases. For example, people that  a new home most likely to buy new furniture.

Many algorithms for generating association rules have been proposed. Some well-known algorithms are: Links are included below for interested readers.
* Apriori algorithm
* Eclat algorithm and
* Frequent Pattern-Growth


## Applications of Unsupervised Learning Techniques.
subgroup of cancer patients grouped by their gene expression measurements
Groups of shopper based on their browsing and purchasing histories
Movie group by the rating given by movies viewers







Solution : Predicting the gender of a person Predicting whether monsoon will be normal next year. The other two are regression.

References
https://towardsdatascience.com/explaining-machine-learning-in-laymans-terms-9b92284bdad4

https://medium.com/@Mandysidana/machine-learning-types-of-classification-9497bd4f2e14
https://medium.com/datadriveninvestor/classification-algorithms-in-machine-learning-85c0ab65ff4
https://towardsdatascience.com/unsupervised-learning-and-data-clustering-eeecb78b422a
https://www.guru99.com/unsupervised-machine-learning.html#7
https://www.wikiwand.com/en/Unsupervised_learning
https://www.wikiwand.com/en/Association_rule_learning
