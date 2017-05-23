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