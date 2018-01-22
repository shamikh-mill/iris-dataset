# TensorFlow Reference Guide 

- Any data processed with tensorflow has to be stored in a multidimensional array, called a Tensor. 
- To run operations on the dataset, construct a computational graph. We're defining how data, or tensors, will flow
through the system. 

To build a model in TensorFlow: 
1. Define each layer of the neural network and connect them together for data to flow from first to last layer. 
2. Then, add the placeholder code that represents the data that will be fed in as input to the neural network, and 
another placeholder node that represents the output (values predicted by the neural network). 
3. Next, we need a way to measure the accuracy of the neural network's predictions. For each prediction, we'll compute 
a loss function. Loss function gets added to the graph as its own operation. 
4. Then, we need create an optimizer function that tells tf how we want to train the model (usually with gradient 
descent). Running this function performs one training step on the model. This function trains the NN by looking at the
results of the loss function and using that to adjust the weights of each layer in the neural network until they 
produce the correct output. The computational graph has no strict start or end, we can start processing at any node. 
5. If we want to run one step of training, we can run the training operation. If we want to make a prediction for new 
data, we can run the output operation. 
6. The machine learning algorithm is fully defined as a computational graph, and we can train after creating a session.
7. A session is the object in tf that runs operations on the graph, and tracks the state of each node in the graph. 
Once a session is created, we can ask it to run any operation on the graph. Training the model will call the training 
operation over and over. Each time the training operation runs, we'll pass in new training data that will be used for 
that training pass, and check current accuracy by calling the loss function. Training can be visualized in TensorBoard.
8. Testing- we pass in test data and measure accuracy with the loss function. Loss function checks error in predicted 
and actual values. 
9. Once happy with the accuracy, we can save the model to a file, writing out a copy of the graph and all nodes in the 
graph. Loading later restores to this previous state. 
10. When using the NN to make new predictions, the loss and training functions can be left out. All we'd need are the 
nodes that build up the neural network itself. So when we deploy it, we can strip out the parts of the computational
graph that we don't need. 









## Glossary
1. Epoch - one full training pass over the dataset. 
Parameter training_epochs defines how many times we run over the data in our training loop to traint the data.
2. Session - state in which we can ask TensorFlow to execute commands 


## Resources
1. https://www.lynda.com/Google-TensorFlow-tutorials/Building-Deploying-Applications-TensorFlow/601800-2.html (Defining the Model Strucure, 
in part 3, is perhaps the most useful 
