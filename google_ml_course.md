## Google ML Crash Course 

Convenient Loss Function for Linear Regression- 
L2 Loss - Squared Error -> Square difference between prediction and label: (observation - prediction(x))^2 =  (y-y')^2. 
Mean Squared Error (MSE): sum up all the squared losses for individual examples and then divide by the number of examples:

Training a model simply means learning (determining) good values for all the weights and the bias from labeled examples. In supervised learning, a machine learning algorithm builds a model by examining many examples and attempting to find a model that minimizes loss; this process is called empirical risk minimization. 

In Gradient Descent, we take a direction of "negative gradient" and move in the direction that minimizes the loss in each iteration, and then recalculate the loss. The step size is determined by the learning rate. We are taking the gradient of the loss function, and the negative gradient tells us which direction we should go to update the model parameters to reduce loss. Imagine x,y coordinate with Loss on the y-axis, and the model parameter theta on the x axis, and use GD to get to the minimum. 
When there are multiple weights, the gradient is a vector of partial derivatives with respect to the weights.
In convex problems, our weights/paramters can start anywhere, and eventually get to the (single) minimum if we use gradient descent somewhere in the 'bowl' shape
Non-convex problems- Neural Networks are notoriously non-convex, and so there are more than one minima, and there is a strong dependency on the initial values of the parameters in terms of where GD takes us. 

Stochastic Gradient Descent and Mini-Batch GD 
While we could compute the gradient over the entire dataset in each iteration, this is unnecessary/a lot of computation.   
We can instead compute the gradient on small, randomized data samples. 
1. SGD- one example at a time 
2. Mini-Batch- batches of 10-1000, and the loss/gradients are averaged over the batch. 

Usually, you iterate until overall loss stops changing or at least changes extremely slowly. When that happens, we say that the model has converged.