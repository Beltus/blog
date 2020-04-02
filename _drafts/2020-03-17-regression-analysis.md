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
