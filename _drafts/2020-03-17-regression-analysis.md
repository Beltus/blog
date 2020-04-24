## Some key points of Regression Analysis.

In linear regression the objective is to find values of model parameters (b0, b1, ..., bn) that minimizes the cost function (J(b0, b1, .... , bn)).

The cost function is the sum of square difference of the predicted output values and the actual output values.

So generally, the problem is a linear programming minimizing problem where the objective function is the cost function and the decision values are (b0, b1,..., bn).

##Note: The number of model parameters = the number of features + 1 i.e for example if we have 4 features in a regression problem, the our hypothesis is h(x) = b0 + b1x1 + b2x2 + b3x3 + b4x4 where bi = model parameters

The difference between the hypothesis and the cost function is that. the hypothesis is a function of x-input value while the cost function is a function of the model parameters b0,b1...bn

Each value of theta(b) represents a seperate hypothesis. and for each value of theta we calculate the corresponding cost function.i.e, the value of the theta corresponds to a line or curve in the hypothesis but in the cost function it corresponds to a single point.

Efficient algorithms exist to help use find the values of model parameters that generates the minimum value of the cost function

Gradient Descent is a general algorithm that is used to minimize any function. In linear regression we use gradient descent algorithm to automatically and simultaneauosly update the model parameters. For each update, the cost function is calculated until hopefully convergence is reached, i.e the global optima

b0  = b0 - alpha * d/db(J(b0, b1, ... , bn))
b1 = b1 - alpha * d/db(J(b0, b1, ... , bn))

Two fundamental things that make up gradient descent is the learning rate (size of the step-(alpha hyperparameter) , and direction of steepest slope - (partial derivative of the cost function)

Remember the derivative of a  function at a particular point is the slope of the line tangent to the function that passes through that point. For a one variable regression problem(has just one model parameter-b1), if the slope is positive b1 decreases, and vice versa,

If alpha is too small, gradient descent becomes too slow, as the it takes a lot of time to converge to local minimum. This is because the updated b-parameters are increased by tiny baby steps down the hill. If the alpha is too large, we might overshoot and even diverge. That is we might jump over the minimum value and never converge.

Gradient descent has a cool hidden feature, as it can converge with a fixed learning rate. This is because as the algorithm processes towards a local minimum, the partial derivative terms becomes smaller and smaller and multiplied by alpha result in a small value and hence small step.
![](https://beltus.github.io/vision/assets/images/gd.png)

This is generally called the Batch gradient descent as the algorithm uses all the training samples in every update iteration process of the model parameters

1 point
## WEEK TWO

### Multivariate Linear Regression - Multiple Features
Multivariate simply means we got multiple variables or features which we are using to try and predict the output value

When we have more than a single feature in our training data to use for prediction, each of the training example now becomes a vector instead of a single value. To be specific, in such cases, each training example becomes an n-dimensional feature vector where n = number of features in the training set.

This also changes the hypothesis from a linear line equation to that shown below

h(x) = b0 + b1x1 + b2x2 + . . . . + bnxn

This means that, a unit change in a feature i, corresponds to a change, bi in the hypothesis. E,g price of houses.

Hypothesis function doesn't necessarily need to be linear

In Gradient Descent for Multivariate Linear Regression, the cost function J, simply changes by the number of model parameters b,

* Feature scaling is one of the 2 common techniques that aims at adjusting the ranges of all features to be thesame or close to each other. This helps the gradient descent algorithm to converge much more faster and with fewer iterations and also correctly. If the range is too small. scale up and scale down otherwise.
* Mean Normalization is another technique mostly used for feature scaling i.e scaled_x = (x - x_mean)/max_x.  max_x can be replaced by the (max_x - min_x) or by standard_deviation of X. All the methods work properly. So feel free to chose which soothes you.

* A plot of cost function J(b) against the number of iterations is a good practical way to determine if gradient descent has converged.

A small value of learning rate results in a very slow convergence i,e it takes so much time to reach the local minimum of the cost function.
On the other hand if the learning rate is too large, cost function may not decrease on every iteration and can even diverge

* Normal equation is a technique used to solve for the values of the model parameters which mininizes the cost function analytically. It doesnt perform an iterative process like gradient descent. We do not choose any learning rate.

The foundation of the Normal equation is based on computing the partial derivatives of the cost function wrt to each model parameter, setting it to zero and solving for the parameter. This has been simplified by the following equation
θ=(XTX)−1 XTy




For a large number of features i.e n = 10000+ it is computational expensive as we need to compute matrix inverse which is a quite expensive process for large matrices.In this case gradient descent is best choice.

## Note
If the XTX - matrix of the normal equation is non-invertible i.e it is singular or degenerate, then this implies 2 main things
* Redundant Features - Linearly dependent Features
* Too many features


### WEEK THREE

## Classification
###Logistic Regression

It is a classification algorithm that is based on the sigmoid or logistic function . g(z) = 1/(1+exp(-z)) whose values are squashed between 0 and 1

The way our logistic function g behaves is that when its input is greater than or equal to zero, its output is greater than or equal to 0.5:

In binary classification the output is either 0 or 1, so it is necessary for the hypothesis to also be within the range 0 and 1 contrast to the case of linear regression. That is why we use the logistic or sigmoid function for the hypothesis. It is then interpreted as a probability. e.g h(x) = 0.7 for a ham or spam email classification problem where 0 = ham and 1 = spam, means that, there is a probability of 0.7 the email is spam.

h(x) = g(b0 + b1x1 + b2x2 + .... + bnxn)

## Decision Boundaries
It is boundary that seperates the dataset into its various classes. The decision boundary is the line that separates the area where y = 0 and where y = 1. It is created by our hypothesis function.

Note that, It's properties are totally based on the model parameters(thetas) and not on the training data(X). When model parameters are calculated, the decision boundary is known. It is evaluated as z = b0x0 + b1x1 + ... + bnxn = 0 i.e setting
* Non-linear decision boundaries can also be used in classification tasks to obtain better models

## Cost Logistic regression

We use a different cost function for Logistic regression as the cost function of linear regression if used will be wavy with many local optima i,e it is not a convex function

## Multiclass Classification
We use the one-vs-all(or one-vs-rest) classification technique where by we train n binary logistic classifiers for n classes in the dataset. During prediction, the input is ran across all n-classifiers. The input belongs to class whose model outputs the highest probability.

##Solving the Problem of OVerfitting
Underfitting is also called high bias occurs when we have very minimum data for training.
Overfitting also called high-variance and occurs when we have to many features in our dataset.
There are two main options to address the issue of overfitting:

1) Reduce the number of features:
  * Manually select which features to keep.
  *  Use a model selection algorithm (studied later in the course).
2) Regularization
     * Keep all the features, but reduce the magnitude of parameters \theta_jθj.
Regularization works well when we have a lot of slightly useful features.



### WEEK 5

We use the Backpropagation algorithm to calculate the gradients for each layer in a Neural Network. Back propagation comes from the fact that, we begin the algorithm by computating the gradient(error-term(delta)) of the output layer, then use the results to compute the gradient term of the previous activation layer and so on till we get to the gradient of the first hidden layer. We dont calculate the gradient of input layer.

Each Delta for a particular layer is a vector of same length as number of the units in that layer, where each element of delta vector is the error of the corresponding unit in that layer.

"Backpropagation" is neural-network terminology for minimizing our cost function, just like what we were doing with gradient descent in logistic and linear regression.The goal is to minimize J(THETAs)

Back propagation is a method used to compute the partial derivatives of the cost function J wrt to the theta-values(model-parameters). Together with the cost function, backpropagation can then be used by gradient descent algorithm or as a parameter to the optimization minimization algorithms such as fminunc() or fmincg in Octave to evaluate the optimum thetas (model parameters). This is the training phase and results in the high performance model parameters.


### Gradient Checking is a method that is used to verify if our implementation of backpropagation is working properly.
We manually compute the estimate of the gradients of our cost function and then check if it is approximately equal with what the advanced Back propagation algorithm is giving.

## Note  
For neural networks we do not initialize the model parameters with zeros, as this results in the same values of the activation units for any particular hidden layer. Also, after gradient descent update of the model parameters(thetas or weights), the new updated thetas are still same for every unit of a layer, ie model is not learning. This is called symmetric weight problem

For neural networks we perform Random initialization of the model parameters to avoid this draw back. This is called symmetry breaking.

In training a neural network, we need to first decide on the network architecture. The network architecture is simply, the connectivity pattern between neurons, i.e the choice of the number of hidden layers to use. Note that the number of input units is the dimension of features, x(i). Also, the number of output units is determined by the number of classes for the case of a classification problem.

It is also great practice to use same number of units in every hidden layer in your neural network. Default number of hidden layers is 1. The greater the hidden units the better performance of the model but increase in computational complexity,

### Training a Neural Network

1. Randomly initialize the weights
2. Implement forward propagation to get hΘ(x(i)) for any x^{(i)}x(i)
3. Implement the cost function
4. Implement backpropagation to compute partial derivatives
5. Use gradient checking to confirm that your backpropagation works. Then disable gradient checking.
6. Use gradient descent or a built-in optimization function to minimize the cost function with the weights in theta.

When we perform forward and back propagation, we loop on every training example:




## WEEK 6 HIGHLIGHTS


### Debugging a Learning algorithm

If your training model is not doing well on test data here is what you can do
* Get more training examples
* Try smaller sets of Features
* Try getting more additional features
* Try polynomial Features
* Decrease or Increase the lambda of the regularized term

## Evaluating a Hypothesis
Split your data into training and test split. Train your model using the training split to obtain the optimized model parameters(thetas). Use the trained model
parameters to evaluate the test set error(cost function J(theta)) using only the test examples- This is the case of linear regression. This is will give you an idea of the performance of your model on unseen data. Also mis-classification error is another metric that is often used to evaluate how well hypothesis is performing for the case of classification.

Generally it is good practice to split data into train, validation and test set. This helps to decide which degree polynomial hypothesis model performs best in case of linear
regression. Compute model parameters (thetas) with train set for the different degree hypothesis function, use the validation set to compute the difTo check if model is underfitting or
ferent validation error
(J_cv(theta)). Choose model with least cross validation error, then using the test set, compute the test error(J_test) to choose model with least error.

If your trained model performance is quite low, it could be as a results of either High bias(underfitting) or high variance(Overfitting). To identify which of these your model is suffering from, check the Error on both Train and Validation set.
If Train error and validation error is high, it implies model is underfitting(high-bias). If training error is low while validation error is high, it means model is overfiiting(high variance)

High bias (underfitting): both Jtrain(Θ) and JCV(Θ) will be high. Also, JCV(Θ)≈Jtrain(Θ).

High variance (overfitting): Jtrain(Θ) will be low and JCV(Θ) will be much greater than Jtrain(Θ).

Use Learning curves to diagnose if your learning algorithm is suffering from a bias or variance problem,

If your algorithm is suffering from high bias, increasing the training examples doesn't help reduce the training and cross validation error value.

Conversely, if your learning algorithm is suffering from high variance, getting more training examples can likely help improve its performance as, Jcv(theta) will keep reducing with more training examples

Our decision process can be broken down as follows:

* Getting more training examples: Fixes high variance
* Trying smaller sets of features: Fixes high variance
* Adding features: Fixes high bias
* Adding polynomial features: Fixes high bias
* Decreasing λ: Fixes high bias
* Increasing λ: Fixes high variance.

Precision and recall are good evaluation metrics for classification models as it can help pinpoint the effect of skewed dataset. e.g A dataset with far greater
negative negatives could result in a very low recall.

By changing the threshold value for the hypothesis function of a logistic classifier for example i.e h(theta) > threshold , we can obtain different values for precision and recall on the cross validation set

High precision and recall means learning algorithm performance is good
## Precision
It is a classification metric which is evaluated thus. What fraction out of the total positive predictions(TP + FP) by our model is truely positive.
Precision = TP / (TP + FP)

## Recall
It evaluates what fraction from the actual number of positive examples in our dataset (TP + FN) is actually positive
Recall = TP / (TP + FN)

To choose which classifier is best, based on precision and recall values, we can evaluate the **Average** of precision and recall i.e (P + R) / 2. However, this is not a great way to decide which model is best as either a high precision or high recall of a particular model can lead to high average value.

To solve this drawback of the average evaluation, we use the F1-Score evaluation metric which is calculated as follows;

F1-Score = 2 * (PR)/ (P + R)

So if either P or R is very low, F1-score will be low. A high F1 score is only achieved by P and R are relatively high. Best model has highest F1 score.


### WEEK 7  HIGHLIGHTS

Support Vector Machines.
SVM is another interesting type of classifier similar to logistic regression wrt to cost function. SVM's don't suffer from local minima problems as it's cost function is purely convex.
General cost function is

Minimize J(theta) = C * A + B, where c is cte, just like lambda in regularized logistic regression cost function where we instead have,

Minimize J(theta) = A + lambda * B

The hypothesis of SVM outputs a 1 for positive class and zero for negative class directly, converse to Logistic regression which outputs a probability (0 to 1).

Similarity functions for example Kernels(e.g Gaussian kernels ) can be used with SVMs to develop complex non-linear SVM models. It is based on selecting random points called landmarks on our training datasets and then, generating new features , f, based on the gaussian distribution equation
f = exp( - (x-l).^2 / 2*(sigma).^2); where l = vector of random landmarks and x = training example.
Based on the number of landmarks, for each training example we evaluate f, then use that in our hypothesis to train and predict our model.

The idea of using kernels is just to create new features using our original training examples then train an SVM classifier using these new features instead
of the original training dataset features.
Landmarks are usually selected at same position as the training examples. Hence, if your training set has m examples, then you have m number of landmarks.
This results in a new feature vector f of length m + 1 and consequently, your model will have model parameters(theta) of same size as f, i.e m + 1. This includes the
intercept term(theta-zero). The new hypothesis becomes predict, y = 1 , if Theta' * f > 0

Kernels can be used with linear regression but this is computational expensive and it is discouraged.

In SVM, we have the hyperparameter,C which plays a role of C = 1 / lambda in the case of linear regression regularized cost function. This means that, if C is large, lambda is very small and hence, model parameter are penalized less, leading high complexity and therefore overfitting. If C is small, lambda becomes large, resulting in high penalization of the
model parameters which decreases model complexity leading to underfitting.

Another hyperparameter of SVMs is sigma in the gaussian kernel function. Large sigma results in a gentle sloping gaussian curve corresponding to low variance and high bias
as the features, f vary smoothly. Small sigma, results in a more steeper gaussian function, leading to high variance and consequently low bias as the features f, vary sharply.

Using SVMs with very large datasets, is computational expensive as the number of new features created using kernel equals the size of dataset examples.
SVM with no kernel is also called a linear SVM and this is simply a standard SVM linear classifier


For multi-classification using SVM, we use the one vs all method to distinguish between the different classes. if we have K-classes, we simply train K  SVM classifiers
for each class by setting the corresponding class to y = 1, and the all other classes to y = 0. Prediction on an example is done by choosing SVM with the highest hypothesis value.

## Logistic Regression Vs SVMs
If the number of features, n is relatively larger than the number of training examples, m (e,g n = 10000 , m = 10 - 1000) use logistic regression or SVM with linear kernel

If number of features n is small, and m is intermediate e.g (n = 1 - 1000, m = 10 - 10000), use SVM with Gaussian kernels

If n is small and m is very large e.g (n = 1 -1000, m = 50000+), its smart to use logistic regression or sVM with linear kernel.

For all the above cases, neural networks tend to work well. Just a little bit slower.

## Week 8 Highlights

## Unsupervised Learning

Clustering algorithm are popularly used for unsupervised machine learning task.

K-means clustering algorithm is the most used clustering algorithm. Its inner workings is based on 2 main steps,that are iterative.

Cluster Assignment step which assigns training examples to each clusters based on proximity of training example to cluster.

Move cluster centroid step which relocates each centroid to the average or mean of its cluster subset.

Then again we perform cluster assignment step and so on.

The initialization of cluster centroids is done by assigning k-cluster centroids to randomly chosen k-training examples.

## Dimensionality Reduction is another type of unsupervised learning algorithm. The most common dimensionality reduction algorithm is Principal Component Analysis(PCA)

PCA aims at finding a lower k-dimensional feature hyperplane (surface) on which to project the training examples of higher dimension in such a way as to minimize the squared projection error(distance from each training example to the projection surface)

In choosing the number of principal components k for PCA. it is good practice to choose smallest value of k for which 99%of the variance is retained.

We apply PCA in supervised learning problems with very large number of features. This is applied only to the input training set of your dataset and not on the cross validation or test set of the dataset. PCA finds a mapping from training example x(i) to z(i), where z(i) is the new feature vector obtained after running PCA. So PCA can be considered a preprocessing for supervised learning algorithms.

PCA has two major applications,
#### 1. Compression: To reduce the memory/disk to store data and speed up learning algorithms

#### 2. Visualization applications where number of principal components k can be 1, 2 or 3 for easy visualization.



## WEEK 9  HIGHLIGHTS

Anomaly Detection is mostly used in Fraud detection. Here we use our dataset to build a probabilistic model. Then use that to detect
any abnormal or fraudulent activities.
Manufacturing also using Anomaly detection to determine if their products are faulty or not.

Monitoring computers or servers in a datacenter.
Gaussian distribution is used for anomaly detection where we estimate
the mean and variance of the distribution using the training set data


In an anomaly detection algorithm, we estimate the average(mean) and variance of individual features in our dataset which gives us the model parameters. Given a new example example, we simply compute the probability , p(x) using the gaussian distribution parameters by the estimated mean and variance. if p(x) < epsilon , then we say it is anomalous. p(x) is calculated based on the assumption of the independence of features. i.e p(x) is the product of probability of each feature.

In building Anomaly detection systems, the dataset is often skewed so, we recline from using classification accuracy as a performance metric which can be very high. Its preferably to use F1-score metric

We use Anomaly detection instead of supervised learning alorithm when we have very very few positive examples
examples(anomalous) and lots of negative examples(normal). Makes it challenging for the learning algorithm to learn from such very small examples.

When interested in capturing some correlation between features we
can use a multivariate Gaussian model estimate the parameters(mean vector and covariance matrix)

## Recommender Systems
Lets take the example of content-based recommender system. We have collected information of the ratings given by users after watching certain movies on our website.
Recommender system takes this information, and tries to predict the possible rating value a user could have given to a movie he hasn't watch yet.
Based on the estimated rating value, the system decides to suggest propose this movie to you.

## Collaborative Filtering for Recommender systems
This  method used to automatically learn relevant features for a recommender system. In collaborative Filtering algorithm, given model parameters(thetas) for each user
, we get features relevant features by minimizing the cost function wrt to the features. These features can then be used to minimize the cost function for the
model parameters for each user. This iterative process increases the performance of the model. This minimization is done more effficiently by simultaneaously minimizing
both cost functions.

##Note that in a recommender system each user has its own unique set of model parameters(thetas). So the number of users equals the number of linear regression
models that have to be trained.

low rank matrix factorization is just a synonym for the Collaborative filtering algorithm. The matrix of predictions can be obtained by X * THETA_transpose.

## Finding related products using the low rank matrix factorization matrix.
If a user just watched movie i, and we wanna recommend 5 other similar movies to this user, we simply, find 5 movies with least least feature difference with the xi(feature vector of xi) i.e

(xi - xj)

Final note. Collaborative filtering algorithm's objective is to use the ratings for every customer i and learn a set of features X, which it then uses uses to learn the model parameters for each user. With these parameters. Based on these learned features X, and parameters, theta, the recommender can predict the ratings for movies without any ratings. Also, the learned parameters can be used to compare features of the different movies and based on difference and then recommend movies to its users.

Mean Normalization is sometimes used to enhance performace of model espeacially when there exist users without no ratings for products.


## WEEK 10 HIGHLIGHTS

##### Large Scale Machine learning

As the size of training dataset increases to millions of examples, gradient descent i.e batch gradient descent algorithm for finding best model parameters becomes
very inefficient due to computational time involved. Stochastic Gradient Descent algorithm is prefered in such cases as it is much faster. In SGD, we shuffle training data, the update the model parameters for each training example contrary to Gradient descent where a single update involves going thru entire dataset.

* Mini-batch gradient descent uses a mini-batch size, b, of our training dataset in each iteration to update model parameters.Contrast to SGD that uses a single example.

## Map Reduce - Data parallelism Approach
A very large training dataset is split into k-subsets and each machine computes the partial sum over a subset. A centralized machine then combines the results from the multiple computers and then perform model parameter updates. Map reduce is also possible for multicore machines, where parallelism is done across the different cores.

### WEEk 11 HIGHLIGHTS

Machine learning pipeline for real projects with the example of a photo OCR(optical character recognition)
Getting lots of data by artificial synthetic methods. This helps improve the performance of
your model only when the model has a low bias. Low bias can be seen via plotting learning curves.
## Note for machine learning problems it is important to first of check using Learning
curves is ur model is suffering from low bias using learning curves. Then second, ask the question, what will it take to get 10-times of more data than what you currently have.

<<<<<<< HEAD
* A plot of cost function J(b) against the number of iterations is a good practical way to determine if gradient descent has converged.

* Normal equation is a technique used to solved for the values of the model parameters which mininizes the cost function analytically. It doesnt perform an iterative process like gradient descent. We do not choose any learning rate. For a large number of features it is computational expensive as we need to compute matrix inverse which is a quite expensive process for large matrices.In this case gradient descent is best chose.
=======
Ceiling analysis use to estimate error of each block of a project pipeline
>>>>>>> fd96c5673e74f770e853c93a7a1c5af931326147
