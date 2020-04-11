## Some key points of Regression Analysis.

In linear regression the objective is to find values of model parameters (b0, b1, ..., bn) that minimizes the cost function (J(b0, b1, .... , bn)).

The cost function is the sum of square difference of the predicted output values and the actual output values.

So generally, the problem is a linear programming minimizing problem where the objective function is the cost function and the decision values are (b0, b1,..., bn).

##Note: The number of model parameters = the number of features + 1 i.e for example if we have 4 features in a regression problem, the our hypothesis is h(x) = b0 + b1x1 + b2x2 + b3x3 + b4x4 where bi = model parameters

The difference between the hypothesis and the cost function is that. the hypothesis is a function of x-input value while the cost function is a function of the model parameters b0,b1...bn

Each value of theta(b) represents a seperate hypothesis. and for each value of theta we calculate the corresponding cost function.i.e, the value of the theta corresponds to a line or curve in the hypothesis but in the cost function it corresponds to a single point.

Efficient algorithms exist to help use find the values of model parameters that generates the minimum value of the cost function

Gradient Descent is a general algorithm that is used to minimize any function. In linear regression we use gradient descent algorithm to automatically and simultaneauosly update the model parameters. For each update, the cost function is calculated until hopefully convergence is reached, i.e the local minimum.

b0  = b0 - alpha * d/db(J(b0, b1, ... , bn))
b1 = b1 - alpha * d/db(J(b0, b1, ... , bn))

Two fundamental things that make up gradient descent is the learning rate (size of the step-(alpha hyperparameter) , and direction of steepest slope - (partial derivative of the cost function)

Remember the derivative of a  function at a particular point is the slope of the line tangent to the function that passes through that point. For a one variable regression problem(has just one model parameter-b1), if the slope is positive b1 decreases, and vice versa,

If alpha is too small, gradient descent becomes too slow, as the it takes a lot of time to converge to local minimum. This is because the updated b-parameters are increased by tiny baby steps down the hill. If the alpha is too large, we might overshoot and even diverge. That is we might jump over the minimum value and never converge.

Gradient descent has a cool hidden feature, as it can converge with a fixed learning rate. This is because as the algorithm processes towards a local minimum, the partial derivative terms becomes smaller and smaller and multiplied by alpha result in a small value and hence small step.
![](https://beltus.github.io/vision/assets/images/gd.png)

This is generally called the Batch gradient descent as the algorithm uses all the training samples in every update iteration process of the model parameters


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
