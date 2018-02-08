---
layout: post
title:  "Notes on machine learning"
date:   2017-05-22 10:00:38 -0500
categories: ml
---
These are my notes and personal references for machine learning algorithms and methodologies in my attempt to better understand the field, its techniques and workflows this summer. I will be starting with "the" fundamental gateway course, Machine Learning by Andrew Ng on Coursera. 

Lesson 1: Introduction to Machine Learning

- The field of study that gives computers the ability to learn without being explicitly programmed. Divided into two major fields:
- Supervised Learning: The method used when the "right" answers are given to the algorithm, and the algorithm is told to find more right answers using these. Examples of the desired outputs are given to the algorithm. 
- Classification: Used for discrete, categorical data. (spam or not spam)
- Regression: Used for numerical, continuous data. (prices)  

- Unsupervised Learning: Used with unlabeled data, the desired outcome is not provided and exploratory techniques are used to find trends. 
- Clustering, segmentation etc. 

Method for estimating house price from size:  
Training set -> Learning algorithm: size of house (x) -> input into hypothesis (function) -> Estimated price (y)  
h(x) = ax + b  
j(a) = v (cost function when b is constant and a is the only parameter), forms a parabola cost function graph  
We minimize a certain cost functionn which changes according the problem situation. For the model above, we find a value of a that minimizes the value of j(a), v, and this "a" value gives the line of best fit.  
  
j(a, b) = n (cost function when a and b are both parameters), forms a 3D curve graph which we can describe instead as a contour plot.  
This is made up of contour lines, which are the collection of the points a, b that satisfy j(a, b) = c for some fixed constant c. We now find the a, b that get the minimal value on this cost function to find the line of best fit. 

Improving Deep Neural Networks: Hyperparameter tuning, Regularization and Optimization

ML is a highly iterative process. Things we change to see what works best:
1. Number of layers 
2. Number of hidden units 
3. Learning rate 
4. Activation functions 

Train/dev/test sets  
- Take all data, carve out some to be training set, hold-out/cross validation set, and a test set. Train models, test iteratively on cross-validation set to see which is doing better, and then test final model on test set for unbiased estimate (never before seen) of accuracy. Since the model trains iteratively on dev set and test set, the performance becomes biased. 
- Smaller dataset: 60/20/20, Larger dataset: 98/1/1
- Cross validation development set and test set should come from the same distribution. 

Bias/Variance 
- "Tradeoff" between bias and variance is less present in deep learning. We can reduce bias and variance individually without really hurting/increasing the other. 
- Low bias, low variance is what we want. 
- High bias = underfit (straight line through data). High error on both test and train -> high bias problem.
- High variance = overfit (complex, curvy line through data). Low error on train but high on test -> high variance problem. 

Basic Recipe for ML
1. After training first model, check for high bias- performance on training data
- If we have high bias:  
- Try a bigger network (almost always helps). A big enough network should be able to at least fit or overfit on the training set if the problem is suitable (humans have low error in doing it themselves)
- Train longer (sometimes helps)
- Search for different architecture NN 
2. Next, check dev set performance- was our model able to generalize from training to dev set? 
- If we have high variance:  
- Try more data
- Try regularization 
- Search for different architecture NN 

Note that more training data will not help if we have a bias problem! More data will usually lower variance and doesn't change bias much. 

Regularization- technique for reducing variance (may increase bias a little bit, but not too much for a large network), especially if we don't have more training data.
- L2: Used much more often than L1 (Usually helps more)- Add a regularization parameter to the loss function used during training. 
- Usually this is lambda (regularization parameter)/2m * norm(w^2). L2 norm is called Frobenius norm of the matrix 
- norm(w^2) = wTw = squared Euclidian norm of the parameter vector W. W (usually pretty high dimensional parameter vector) contains all the parameters that are being overfit. So we usually don't need to a b regularization. 
- "Weight decay"- multiplying weight matrix with a number slightly less than one as well as doing the normal backpropogation algorithm. 
- L1: Add a term lambda/m x norm(w), just the l1 norm of the parameter vector W. Using this causes W to be sparse (lots of 0s) which helps compress the model (helps memory usage).  
- lambda, reg parameter to be tuned, should be set using the dev set (see what works best) 


