
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

Human level error gives us a proxy or approximate of what Baye's optimal error can be.
The difference between the human level error and training error is called the measure of avoidable bias
The difference between train and dev error gives you an idea of variance.

The main thing to note here, is that, in the previous course, we usually compare training error to 0% but here, we are comparing it to human level performance that
can be zero or non-zero. Remember human error performance can be surpassed and it is just a rough estimate of Baye's optimal error

## How to Improve Model Performance
There are 2 fundamental assumptions to consider whenever you build a supervised learning model
1. That it fits the training set pretty well i.e achieves low avoidable bias
2. That the training performance generalizes well on the dev and test set.

In order to reduce Avoidable bias i.e error between human level error and training error do the following:
1. Train a bigger network
2. Train better/ longer optimization algorithms by maybe applying momentum, RMSPRob or AdamProb

In order to reduce Variance i.e the error between training and dev set, try the following:
1. Use more data for training
2. Applying regularization techniques e.g L2, Drop out, Data augmentation
3. Search for a better NN architecture / hyperparameters better suited for the problem


### WEEK 2

#### Error analysis
* Always examine the dev set to see the class images that are being misclassified by your model. This will give you an idea of the particular class that is misclassified most and improve on that  class.

You can use a spreadsheet to make notes of the number of dogs or cats that are being misclassified in the dev set. Then compute the percentages. Also, check number of the images are blurry and kinda indistinguishable. So your columns can be labelled Dogs, Cats, Blurry, Instagram-like filtered Images, Comments.

###Cleaning up Incorrectly Labeled data

* DL models are very robust to random errors but it is not robust to systematic errors e.g if a model keeps misclasifying white dogs as cats, then this is a problem.

#####Advice from Andrew Ng.
Build your first ML or DL system quick and then reiterate. Do this by doing the following:
1. Setup train/dev/test sets and metric
2. Build initial system quickly
3. Use Bias/Variance analysis and error analysis to prioritize the next step.

##### Training and Testing on Different Distributions.
IF your train and dev set are from different sources and hence different distributions, then you...
Option 1:  Combine them and then shuffle to make them same. Then split into train/dev/test set. This is not recommended

Option 2: Consider we 200.000 cat images from web for training and 10.000 cat images from mobile phones making them 2 different distributions; So we can use 205000 cat images for training, 2500 for dev from mobile app and 25000 cat images from mobile app for test set. This is recommended.


### Bias / Variance Mismatched Problems

* The difference between human error and training set error gives avoidable bias estimated
* The difference between training set erro and training-dev set error (from same distribution as trianing set), gives the variance.
* The difference between the training-dev set error and the dev set error gives us an idea of data mismatch
* The difference between dev set error and the test set error gives an idea of the degree of overfitting.


#### Addressing Data Mismatch
* Data mismatch comes from the fact that, training set comes from a different distribution different from Dev and Test set.

To address this, we try to make training data similar to dev set by finding more data. This is can be done by artificial  synthesize data. Artificial data synthesis works in speech recognition, computer vision etc

#### Transfer LEARNING


The concept of training a ANN for a different task and the using the pretrained weights to train a different ANN for a completely different task.

The process of training the first ANN is called Pretraining and the augmented NN is called Fine tuning.

This is usually done by taking out the last layer of the pretraining network and then attaching the new dataset to that layer while using the pretraining weights.


Using a pretrain network is good because, the pretrain model already understands what for example images or voice are, before you use it for your application in an image or speech recognition system.

When does transfer learning make sense?

* Task A and B have thesame input e.g images or voice
* You hae a lot more data for Task A than Task B
* Low level features from A could be helpful for learning B

#### Multitask Level
Here we try to predict multiple objects at thesame time for one single input. E.g an image having multiple labels like a car, pedestrian, traffic sign.
i.e you train one neural network to do four things and not seperate four networks.

### End to End Deep Learning.
It simply bypasses the normal machine learning process of feature extraction and then identifying for example an object. That is, it simply uses alot of data to directly train model from input to output. It learns a direct mapping from input to output.

###Pros of End to End Deep learning/
* Let the data speak i.e
* no design of hand crafted Features

###Cons
* Needs alot of data
* Excludes potentially useful hand design components




COURSE 4: CONVOLUTIONAL NEURAL NETWORKS

### Computer Vision problems
1. Image classification e.g detect if an image has a cat
2. Object Detection e.g SDC by detects and draws boxes around detected objects and multiple objects can be detected
3. Neural Style Transfer e.g Having a content and style by painting the content image in the style of the style image

In CNN, the filters are considered as parameters that the model can learn and then convolve with the image to learn the more complicated features that are a better representation of the image than hand crafted filters such as sobel filter for edge detection.

Convolutional operation without padding results in the image shrinking. Also, lots of information is being lost at the edges of the images. To fix this, we apply padding to the image before applying convolution operation.
Normally we pad with zeros.
For example;  we have an image of n X n dimensions to convolve with a filter of f X f dimensions. Without padding the resulting image will be of dimension, n - f + 1 X n - f + 1

With a padding, p = 1, the dimensions of the output image then becomes; n + 2p - f + 1 X n + 2p - f + 1 ; which maintains the dimensions of the original image.

* Valid Convolution Padding means no padding before Convolution
* Same Convolution Padding means output size equals input size.

Given the filter size, we can solve for p in the equation n + 2p - f + 1 = n ; to know the number of padding to add to the input image

Strided CONVOLUTION

This is when we shift the filter by a number equal to or different from one during the convolution operation.

So let's calculate output image Sizes
Let stride s, and padding be p. input size image is n x n and filter, f x f , then output convolved image will be of dimension [(n + 2p - f + 1 )/s  + 1 ] X  [(n + 2p - f + 1 ) / s  + 1 ]/ 2
If the filter size f x f is even, always round down the padding number.

For RGB images with 3 channels, the filter used for convolution too has to match the number of channels of the image. For example convolving a 6 x 6 x 3 image with a 3 x 3 x 3 filter results in a 4 X 4 image. Not a 4 X 4 X 3 image. Each image channel is convolved with its corresponding filter and then, they're are all summed up to give a single number in the convolved image.

In order to detect different types of edges such as detecting vertical edges, horizontal edges, 45-degrees etc, in an image, we apply the the corresponding filters to this image and then stack each output from each filter convolution to have your final image.

For example, let nc = number of channel or depth, so convolution operation with n X n X nc image with f X f X nc results  in n - f + 1 X n - f + 1 X nc* where nc* is the number of filters.

* As a rule, if you have r - number of filters, then you're convolution output image will have a ( n X n X r) dimensions. Where n = height and width of image after convolution.

####The below paragraph is wrt to a Convolutional Layer

* The analogy of CNN to ANN, is that, the filters in CNN represent the weight matrix in ANN. i.e the number of parameters in a single layer. For example, Given 10 filters that are 3 X 3 X 3 in one layer of  a neural network, the number of parameters in that layer is ( 3 * 3 * 3 + bias) * 10 = 28*10 = 280

Notice that, irrespective of the size of the input image, the number of parameters remain fixed at 280 and can be used to detect vertical edges, horizontal edges etc. This makes cNNs less prune to overfitting

### Pooling layers - Max Pooling layer

*It kinda helps to filter out and keep the most important features in our image while reducing the size of image and therefore complexity. The output size of the max pooling layer is computed using same formula above of convolution operation.

For an input image with nc number channels, the maxpool output layer will have same number of channels, nc. Max pool computation is done independently on each of the channels of the input image.

Another type of pooling is called the Average pooling where the average of each square section of input image is computed and outputed.
* In Pooling, there are no parameters to learn. There are just hyperparameters that you set.

* A layer in a ConNet is defined as Conv layer + Pool layer as a single layer. Sometimes, conv layer and pool layers are regarded as seperate layers

As you go deeper in a CNN, the height and width of the input image decreases. While the number of channels increases. This is general pattern. Also, one or more conv layer followed by pool layers and then one or more conv layer and then pool layer, then fully connected layer and finally softmax. this is another pattern.

Advantages of Conv layers to Fully connected layers is parameter sharing and sparsity of connections


### Note that the filter dimensions has to match the number of channels in the image it is being convolved with. However, the output dimensions of the image is dependent on the number of filters used.

### WEEK 2

## Classic Network Architecture
Some classic Neural Networks include LeNet-5 , AlexNet, VGG

* LeNet-5 was aimed at identifying handwritten digits. This had
K parameters.
* AlexNet was similar to LeNet but much bigger. And was used to detect many objects and had about million parameters
* VGG-16 uses the "same padding" so the image size doesnt decrease as we go deeper into the network, after a convolution operation. This is contrary to the 2 above networks that use "valid padding".
 in VGG means the network has 16 layers with weights in the architecture. We also have VGG-19 which is bigger than VGG-16


 ### ResNets - Residual NETWORKS

 In ResNet, the activation - a[l], of a layer doesnt follow the sequential flow, instead it skips the linear block and moves to a much deep level of the model. It's normally added after the linear part but before the ReLu part. So it's known as skip connection or short cut. Which helps train much deeper networks

 Using 1 X 1 Convolution or Network in Network can help you to strink number of the channels in a NN. Just like pooling layers strinks the width and height of the image


#### Inception Network Motivation
Cost of convolution is measured by mutiplying the output dimensions with the filter dimensions.
Bottle neck layers using  1 X 1 convolution reduces the computational cost. This is implemented in the Inception module.

####Advice for implementation

Always google implementation of architectures open-source code to modify and achieve your own computer vision tasks.

### Transfer LEARNING

* Always download pre-trained weights to use that as a good initialization to your own network and safe you time. i.e transfer learning. Download both code and weights that have been trained on different networks.
sometimes the outputs of these networks can have the output 1000 outputs of the softmax layer. So for your problem, you can remove this softmax layer and replace with your own softmax with maybe just 2 outputs. We then freeze the remaining layers. You do when you have small data set for your original problem.

For the case of larger data set, you can freeze fewer layers and then increase the number of layers your train on top of that using your own data set.

But if you have so much data you can use the thesame architecture and train it from scratch using your own dataset and change the softmax layer to match your problem. Remember this will take more time.

Generally, always consider transfer learning in computer vision task.


### Data augmentation

It's a technique used to improve performance of computer vision task. Having more data in computer vision makes performance better. Data augmentation is true even in the case where you're using transfer learning and pre-trained weights.

##### Common Data Augmentation methods
* Mirroring
* Random Cropping. Mirroring and random Cropping are the most commonly used methods.
* Sometimes we use rotation, shearing or local warping.
* Color Shifting : changing the color channels of the image.

Also, check opensource code to see how people implement data augmentation

### Tips for Doing well on Benchmarks/winning Competitions
1. Ensemble: Train several networks e.g 7 neural networks independently and average their outputs(y_hat)
2. Multi-crop at test time: Run a classifier on multiple versions of test images and average results.


### WEEK 3
#### Object Detection
* Image classification simply tells you if there is a particular object in the image of not e.g car in image
* Image Classification with Localization is the problem is localizing an object(i.e, where in the picture is the detected object) in an image and drawing bounding box around the object.
* Detection is when u can have various instances of different objects with bounding boxes around objects

* In a CNN, the model can use a softmax layer to output the label of the output class(e.g car, pedestrian, motocycle). In classification with Localization the output label, further outputs the object bounding box location(bx, by, bh, bw), where (bx, by) specifies the center of the detected object and (bh, bw) specifies height and width of the object based on the percentage of the entire height and width of the image respectively.

### Formal Definition of y_output of cNN
The output y, is a vector y = [Pc, bx,by,bh,bw, c1, c2, c3, c4, ..]. where Pc is 1 or 0 if there is an object detected or not. For example y = [1 , bx,by,bh,bw, 1 , 0, 0, 0], means that an object is detected and c1 = 1 means an object of class 1(e.g car) is detected. If Pc = 0 , then y = [0, ?, ? , ? , ? ,,,] for don't cares.


### Landmark Detections
*This is we're interested in detecting some important key points also called landmarks of an object using the CNN. e.g for a face you can have landmarks specifying key points of the face e.g eye, mouth, nose. So for example, a the CNN network can be trained to output whether there is a face or not together with key landmarks of the face. e,g y = [face, l1x, l1y, l2x, l2y , .... , l64x, l64y]
These are the building blocked of instagram or snapchat fliters used to draw crowns on the face or warp the face, etc.

* To train such a model, we need a labeled dataset of landmarks where the key landmarks have been laborious annotated. Using this, you can pass in your detected landmarks and hence detect parts of the face or maybe key body parts knee, chest any object of interest. So, NN can be used to annotate the pose of the person.

## Note: To achieve this, the identity of landmarks must be consistent across all the images. i.e landmark 1(l1x, l1y) should always be for example the left corner of the eye across all images
