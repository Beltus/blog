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
