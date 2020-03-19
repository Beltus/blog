## Some key points of Regression Analysis.

In linear regression the objective is to find values of model parameters (b0, b1, ..., bn) that minimizes the cost function (J(b0, b1, .... , bn)).

The cost function is the sum of square difference of the predicted output values and the actual output values.

So generally, the problem is a linear programming minimizing problem where the objective function is the cost function and the decision values are (b0, b1,..., bn).

Efficient algorithms exist to help use find the values of model parameters that generates the minimum value of the cost function

Gradient Descent is a general algorithm that is used to minimize any function. In linear regression we use gradient descent algorithm to automatically and simultaneauosly update the model parameters. For each update, the cost function is calculated until hopefully convergence is reached, i.e the local minimum.

b0  = b0 - alpha * d/db(J(b0, b1, ... , bn))
b1 = b1 - alpha * d/db(J(b0, b1, ... , bn))

Two fundamental things that make up gradient descent is the learning rate (size of the step-(alpha hyperparameter) , and direction of steepest slope - (partial derivative of the cost function)

Remember the derivative of a  function at a particular point is the slope of the line tangent to the function that passes through that point. For a one variable regression problem(has just one model parameter-b1), if the slope is positive b1 decreases, and vice versa,

If alpha is too small, gradient descent becomes too slow, as the it takes a lot of time to converge to local minimum. This is because the updated b-parameters are increased by tiny baby steps down the hill. If the alpha is too large, we might overshoot and even diverge. That is we might jump over the minimum value and never converge.

Gradient descent has a cool hidden feature, as it can converge with a fixed learning rate. This is because as the algorithm processes towards a local minimum, the partial derivative terms becomes smaller and smaller and multiplied by alpha result in a small value and hence small step.

This is generally called the Batch gradient descent as the algorithm uses all the training samples in every update iteration process of the model parameters

* Feature scaling aims at adjusting the ranges of all features to be thesame or close to each other. This helps the gradient descent algorithm to converge much more faster and with fewer iterations and also correctly. If the range is too small. scale up and scale down otherwise.
* Mean Normalization is technique mostly used for feature scaling i.e scaled_x = (x - x_mean)/max_x. max_x can be replaced by the (max_x - min_x) or by standard_deviation of X. All the methods work properly. So feel free to chose which soothes you.

* A plot of cost function J(b) against the number of iterations is a good practical way to determine if gradient descent has converged. 
