## My Take About the Course

I like the fact it was designed with python with an inbuilt ipython notebook. This removes the stress of setting up a python environment for beginners.






# Neural Networks and Deep Learning Course.

## Neural Networks for Supervised Learning.


## WEEK ONE HIGHTLIGHTS
Applications of Neural networks
* Real estimate
* Online Advertising
* Photo Tagging
* Speech recognition
* Machine Translation
* Autonomous Driving

Examples of Neural networks
* Standard Neural networks
* CNN
* RNN

### Why deeplearning is taking off
* Increase in data
* Computation power CPU and GPU
* Efficient and elegant algorithms for faster computation.
* We have access to a lot more computational power.

* Deep learning has resulted in significant improvements in important applications such as online advertising, speech recognition, and image recognition.
* We have access to a lot of data



## WEEK TWO HIGHLIGHTS


## Binary Classification.

## Logistic regression

In logistic regression we want that, given an input X, we will like to find the probability that output,y is one.

It is defined based on the sigmoid function shown below

It's parameters are W and b, where W is an nx dimensional vector and b is a real Number

## Cost Function for Logistic Regression

To train the parameters W and b of the logistic regression model, we need to first define the cost function.

We can define a Loss function, L(y, y_hat) for a single training example as

L(y, y_hat) = -(ylog(y) + (1 - y)*log(1 - y_hat))

and the cost function is the average error over the entire training Examples
J(W, b) = 1 / m * sum(L(y, y_hat))

The loss function computes the error for a single training example; the cost function is the average of the loss functions of the entire training set.

## Gradient Descent
We want to find W and b that minimizes the cost function.

* Using Computation graphs to compute derivatives

* Logistic Regression Gradient descent


## Note this One Step of Gradient Descent
For each model parameter W(i) , we compute the average(sum / m) of the partial derivative of the Loss function(dJ/dW(i)) with respect to W(i) for all training examples.

We also compute the partial derivative of cost function (dJ/db) wrt to the bias, b.

Then we update the model parameters by computing

W(i) = W(i) - alpha * dJ/dW(i)

b = b - alpha * dJ/db

After this we perform the next iteration of Gradient Descent


*** dW1 is the average of the derivative of the feature 1 of all examples.
*** dw2 = is the average of the derivative of the features 2 of all examples.



## WEEK 3 HIGHLIGHTS


In neural networks, we dont count input layer as a layer. So a 2 layer NN has 1 hidden layer and 1 output layer
Vectorization in Neural Networks

## Activations functions in Neural networks
1. Sigmoid function
2. Tanh fucntion which ranges from 1 to -1. This function is preferred to sigmoid fucntion. So generally,
we use the tanh activation function for the hidden layers and then sigmoid activation for the output layer since it outputs 0 and 1 similar to labels, y in
binary classification
3. Rectified Linear Unit(ReLu) has gain alot of popularity for hidden layers and is commonly used.

Non-linear activation functions are critical for deep NNs because, the help the network learn more interesting features. Linear activation functions if used results only in the linear combination inputs.

### Random Initialization
It is important to randomly initialize the weights of the NN with very small values. Initializing to zero, is not advisable as the computated activation values of neurons remain thesame resulting in a model that doesnt learn with increase number of iterations.


###WEEK 4 HIGHLIGHTS
## Hyperparameters of Deep Learning Neural networks

*Learning parameter
* Number of iterations in the gradient Descent
* Number of layers in model
* Number of units per layers


### COURSE 2: IMPROVING DEEP NEURAL NETWORKS

In machine learning it is advicable to always split your dataset to train-dev-test set.
This gives you an unbiased estimate of the model performance.

In some cases, if your model is trained with for example,a set of images that are cleaner and well organised, than
the actual images that will be tested with the model after deployment. This can result in a huge test error.
The advice here is to train your model with the test set , however the dev set should be the same as the test set.

## Bias and Variance in Deep Learning.

Bias and variance terms stem from the train and dev errors. If you have a low training error, and high dev error, then your model has a high variance and hence overfitting. If your model has a high train error and high dev error, then it has low variance and high bias and therefore underfitting.
High train and dev-error implies that your model has high variance and high bias. Conversely, low train and low-dev error results low bias and low variance

##Technical Steps to Diagnose DL
After building ur DL, check if you have high bias i.e high training error. If yes, you can then follow some steps to reduce this error.
After lowering the training error, check if your model has high variance, by testing error on dev set. if yes, follow certain steps towards reducing high variance.
The methods to lowering these bias and variance can be quite different.

In DL, the L2 norm of the cost function J, which is often multiplied with (lambda/ 2m) is called the Frobenius norm and not L2, as it is made
up of the sum of weight matrices for all layers in the network.

###Note: Why and how Does L2 Regularization affect the values of the model parameters or Weights.

When L2 regularization is added to the cost function, this regularization contributes to positively to the partial derivatives of the cost function wrt to the weights.
So during backpropagation and parameter update phase, W =  W - alpha(dW), where dW = dW(with regularization) + lambda/m * W. Hence, this helps to drive the update parameter
faster to zero. The larger the lambda the faster weights decay or go to zero.

## How regularization Prevents overfitting
In addition, to the explanation above. If the regularization term is large, Z = Weights x A + bias will be small leading to activation function(tanh) being Linear
and not capturing complex structures.

## Drop Out regularization
Drop out is a technique for regularization in deep learning. Most common technique for implementing dropout is the inverted technique.
Remember during testing dropout should be deactivated. As this can randomize your output and you don't want this.

Other method of regularization include data augmentation but distorting training examples by maybe rotations functions.
Also we have early stopping technique.

## Normalization of Input Features.
This makes it easier for the cost function J  to be optimized.i.e gradient descent easily converge.

## Vanishing and Exploding Gradients.
Deep learning models suffer from the problem of vanishing and exploding gradients.
* If the initial weights are slightly greater than 1 or the Identity matrix, for very deep neural networks, then the weights tend to grow exponentially.
* If the initial weights are slightly less than 1 or ID matrix for very deep neural networks, then the weights tend to decrease exponentially.

Some techniques exist to help to mitigate the vanishing and exploding problem of weights in DL neural NETWORKS
* By setting the variance of the weights to (2 / n) where n is the number of neurons for that particular layer, and then using it to randomly initialize
the weights,  helps prevent weights from Exploding or vanishing.
* Also, based on the activation used such as sigmoid, tanh or Relu, the variance expression changes.
* Xavier initialization is another technique used to mitigate this problem.
* He initialization is another technique used for Initialization
* The method of initialization affects the performance of the DL

We use Gradient Checking only for debugging purposes. This helps to know if your backpropagation implementation is correctly implemented.
Gradient checking doesnt work with dropout.
