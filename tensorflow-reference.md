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


- Placeholder nodes get assigned a new value each time we make a calculation, so you initialize with placeholder and
a type. 

Example Addition Graph: Define the model, create a session, pass in data, and then send it off to the TensorFlow 
execution engine for the result. 
```
import os
import tensorflow as tf

# Turn off TensorFlow warning messages in program output
os.environ['TF_CPP_MIN_LOG_LEVEL'] = '2'

# Define computational graph
X = tf.placeholder(tf.float32, name="X")
Y = tf.placeholder(tf.float32, name="Y")

addition_node = tf.add(X, Y, name="addition")

# Create the session
with tf.Session() as session:
    result = session.run(addition_node, feed_dict={X: [1, 2, 10], Y: [4, 2, 10]})
    print(result)
```

- Once you have a session, you can ask it to run operations on the computational graph by calling session.run, and 
passing in the operation we want to run. 
- Return values will be tensors, because we're operating on tensors! 

## Loading Data 
1. Can preload into memory (arrays- don't need tf-specific functions, but constrained by available memory), 
feed data in step by step, or create custom pipeline, tf-specific method. 
2. Use scaling to ensure that we don't have a mix of large and small numbers- MinMaxScaler in sklearn is good for this.
Use 'fit_transform' to scale training data, and 'trabsform' for testing data 

## Glossary
1. Epoch - one full training pass over the dataset. 
Parameter training_epochs defines how many times we run over the data in our training loop to traint the data.
2. Session - state in which we can ask TensorFlow to execute commands 


## Resources
1. https://www.lynda.com/Google-TensorFlow-tutorials/Building-Deploying-Applications-TensorFlow/601800-2.html (Defining the Model Strucure, 
in part 3, is perhaps the most useful 


Hosting TF Models on the Cloud
```
gcloud ml-engine models versions create version_name \
    --model model_name
    --origin gs://my/trained/model/path
    --runtime-version 1.4
```

1. gsutil mb -l us-central1 gs://project-name
2. gsutil cp -R exported_model/* gs://project-name/modelname_v1/
3. gcloud ml-engine models create modelname --regions us-central1 
- Creates the model named earnings (placeholder)
4. gcloud ml-engine versions create v1 --model=modelname --origin=gs://project-name/earnings_v1/ --runtime-version=1.4
- Create first version of the model, specify its files
