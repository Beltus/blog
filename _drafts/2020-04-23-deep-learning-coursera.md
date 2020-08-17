
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

L(y, y_hat) = -(ylog(y) + (1 - y_hat)*log(1 - y_hat))

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
2. Tanh fucntion which ranges from 1 to -1. This function is preferred to sigmoid function. So generally,
we use the tanh activation function for the hidden layers and then sigmoid activation for the output layer since it outputs 0 and 1 similar to labels, y in
binary classification
3. Rectified Linear Unit(ReLu) has gain alot of popularity for hidden layers and is commonly used.

Non-linear activation functions are critical for deep NNs because, they help the network learn more interesting features. Linear activation functions if used results only in the linear combination inputs.

### Random Initialization
It is important to randomly initialize the weights of the NN with very small values. Initializing to zero, is not advisable as the computed activation values of neurons remain the same resulting in a model that doesn't learn with increase number of iterations.


### WEEK 4 HIGHLIGHTS
## Hyperparameters of Deep Learning Neural networks

*Learning parameter
* Number of iterations in the gradient Descent
* Number of layers in model
* Number of units per layers


## COURSE 2: IMPROVING DEEP NEURAL NETWORKS

In machine learning it is advisable to always split your data set to train-dev-test set.
This gives you an unbiased estimate of the model performance.

In some cases, if your model is trained with for example,a set of images that are cleaner and well organized, than
the actual images that will be tested with the model after deployment. This can result in a huge test error.
The advice here is to train your model with the train set , however the dev set should be the same as the test set.

## Bias and Variance in Deep Learning.

Bias and variance terms stem from the train and dev errors. If you have a low training error, and high dev error, then your model has a high variance and hence overfitting. If your model has a high train error and high dev error, then it has low variance and high bias and therefore underfitting.
High train and dev-error implies that your model has low variance and high bias. Conversely, low train and low-dev error results low bias and low variance which is preferable

##Technical Steps to Diagnose DL
After building ur DL model, check if you have high bias i.e high training error. If yes, you can then follow some steps to reduce this error.
After lowering the training error, check if your model has high variance, by testing error on dev set. if yes, follow certain steps towards reducing high variance.
The methods to lowering these bias and variance can be quite different.

In DL, the L2 norm of the cost function J, which is often multiplied with (lambda/ 2m) is called the Frobenius norm and not L2, as it is made
up of the sum of weight matrices for all layers in the network.

###Note: Why and how Does L2 Regularization affect the values of the model parameters or Weights.

When L2 regularization is added to the cost function, this regularization contributes to positively to the partial derivatives of the cost function wrt to the weights.
So during backpropagation and parameter update phase, W =  W - alpha(dW), where dW = dW(without regularization) + lambda/m * W. Hence, this helps to drive the update parameter
faster to zero. The larger the lambda the faster weights decay or go to zero.

## How regularization Prevents overfitting
In addition, to the explanation above. If the regularization term is large, Z = Weights x A + bias will be small leading to activation function(tanh) being Linear
and not capturing complex structures.

## Drop Out regularization
Drop out is a technique for regularization in deep learning. Most common technique for implementing dropout is the inverted technique.
Remember during testing, dropout should be deactivated. As this can randomize your output and you don't want this.

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

# Week 2

For very very large dataset, we implement mini-batch gradient algorithm instead of the normal batch gradient descent. This increases the speed of computing the
model parameters, by splitting the dataset into mini-batches. For each mini-batch, the weights of the model are updated contrary to batch case where weights are
only updated after going through the entire dataset.

* ## Choosing Mini-batch Sizes
If your training examples, m < 2000, just implement the batch gradient descent. If m > 2000, then you can choose mini-batch size to be powers of 2 such as
64, 128, 256, 512, 1024.

## Gradient Descent with Momentum
In this algorithm, the weights and biases of the gradient descent algorithm are updated using the exponentially weighted average of the computed Gradients
instead of using the computed gradients directly. This helps to speed up gradient descent algorithm.
i.e  dW and db is computed, then Vdw = beta * Vdw + (1-beta)*dW; Vdb = beta * Vdb + (1 - beta)*db ;

  then W = W - alpha * Vdw; b = b - alpha * vdb

beta is normally  = 0.9
This technique permits gradient descent to converge faster in a smooth pattern.
For implementation bias correction is often ignored(dont worry about it)


## RMSProp (Root mean square Prop) optimization algorithm
This is another algorithm that can also be used to speed up or optimize batch, SGD and mini batch gradient descent algorithm.
Here we compute the weight and bias gradients dW and dB;
then we compute; Sdw = beta * Sdw + (1-beta)* square(dW) ; Sdb = beta * Sdb + (1-beta)*square(dB)
then update weights and bias with; W = W - alpha * (dW / sqrt(Sdw + epsilon)) ; b = b - alpha * (dB / sqrt(Sdb + epsilon))

beta is normally = 0.999 ; epsilon = 10^-8

## Adam Optimization
This is an optimization algorithm that simply combines the exponentially weighted average and RMSprop algorithm in order to
speed up mini-batch gradient descent algorithm.
## Note:
* The beta hyperparameters of the 2 algorithms are different.
* Bias correction is implemented in Adam optimization

So in Adam optimization, we compute Vdw, Vdb , Sdw, Sdb and then Vdwc, Vdbc , Sdwc, Sdbc (bias corrected terms)
Finally update weights and bias as follows:
W = W - alpha * Vdwc / sqrt(Sdwc + epsilon) ; b = b - alpha * Vdbw / sqrt(Sdbw + epsilon)

Adam means Adaptive moment estimation


* Learning rate decay is also a method that is often used to speed up learning algorithm by slowly decreasing learning rate over time.
alpha =    (1 / (1 - decay_rate * epoch_num)) * alpha


## Week 3

Hyperparameters tuning

Batch normalization is the process for which the Z-values of the neurons of the layers in a neural network are normalized by computing the mean and standard deviations.
In batch norm after computing mean and standard deviation we do perform another computation before fitting these final values to the NN
This helps to speed up the learning algorithm.

Generally after computing Z, we compute batch norm to Z then we pass the final values to activation function. i.e batch norm occurs between Z and activation.

using batch norm eliminates the bias, b terms of your NN. i.e you can set bias = 0
Batch norm has a slight regularization effect.
* Note that batch norm is implemented over each mini-batch

## Batch Norm during test time
Since mean and std deviation is computed for each minibatch during training, using these values during testing with just a single unseen example is incorrect.
Hence, during testing, we compute new mean and standard deviation which is exponentially weighted averages of the means and standard deviations from the minibatches during training. This is then used for normalization and hence finally prediction.

## Multiclass Classification.
In DL NNs, we use softmax activation function at the final output layer to compute the probability that the input X belongs to one of the classes in the dataset.
Softmax activation function has a unique property that it's input is a vector and its output is a vector of same dimension(probabilities). This is contrary to
sigmoid activation that outputs a real number.
A SOFTMAX layer generalizes SIGMOID to when there are more than two classes.

## Introduction to Deep learning frameworks:
Some of the mst popular include, Tensorflow, keras, caffe, pytorch, theanos,






## Course 3: STRUCTURING MACHINE LEARNING PROJECTS


In the evaluation of a machine learning model, it might not be sufficient to evaluate the model using only one single row number metric such as accuracy or F1-Score.
In such cases, it is important to set up optimizing metric(e.g accuracy) and satisficing metric(minimizing running time).


Note: When developing ML models, make sure that,your train and dev sets come from thesame distribution. If not, your model will perform terribly on the dev set or test set.

Split your training data into Train/Dev/Test sets. In modern day deep learning, we use more samples for training and very small proportion is set for Dev and Test sets. For examples if we have a dataset of 1.000.000 datapoints, we can set 98% for training, 1% for Dev and 1% for Test set. This is because deep learning model have so much hunger for data.

In computer vision task, we can use human level error as a proxy for Bayes optimal error.

The Baye's optimal error is the best possible theoretical error that a model can ever attain but can't surpass

Human error percentage gives you an idea of how much you can improve your model performance. So, for example, if humans get a 1% error and your model
get 8% training error, then there is room for improvement of your model. In contrary, if human level error was 7.5% and your model percentage was 8% then your model is actually
doing pretty well.
Based on these analysis you can then focus on using either bias tactics or variance tactics to mitigate and improve the performance of the model.

Human level error gives us a proxy or aproximate of what Baye's optimal error can be.
The difference between the human level error and training error is called the measure of avoidable bias
The difference between train and dev error gives you an idea of variance.

The main thing to note here, is that, in the previous course, we usually compare training error to 0% but here, we are comparing it to human level performance that
can be zero or non-zero. Remember human error performance can be surpassed and it is just a rough estimate of Baye's optimal error

## How to Improve Model Performance
There are 2 fundamental assumptions to consider whenever you buid a supervised learning model
1. That it fits the training set pretty well i.e achieves low avoidable bias
2. That the training performance generalizes well on the dev and test set.

In order to reduce Avoidable bias i.e error between human level error and training error do the following:
1. Train a bigger network
2. Train better/ longer optimization algorithms by maybe applying momentum, RMSPRob or AdamProb

In order to reduce Variance i.e the error between training and dev set, try the following:
1. Use more data for training
2. Applying regularization techniques e.g L2, Drop out, Data augmentation
3. Search for a better NN architecture / hyperparameters better suited for the problem
