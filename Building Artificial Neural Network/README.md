# ANN
* __Input:__ A banking data which shows the the customers who are leaving the bank(Churn rate)
* __Output:__ To identify which customers are going to leave the bank based on several different factors.
* __Accuracy(Training):__ Accuracy achieved using ANN on training data: __84%(Approx)__
* __Accuracy(Test):__ __83%(Approx)__


**Dummy Variable Trap**: The Dummy Variable trap is a scenario in which the independent variables are multicollinear — a scenario in which two or more variables are highly correlated; in simple terms one variable can be predicted from the others.
So the thumb rule is: “The number of dummy variables necessary to represent a single attribute variable is equal to the number of levels (categories) in that variable minus one.”

### Building a ANN:
After Importing keras we need two modules:
**Sequential module**: It is required to initialise our ANN
**Dense Module**: Required to build layers of our ANN
	
### Choose the right number of Hidden layer node
There is no rule of thumb, but it is observed that the hidden layer should have an average of input and output layer nodes. 

### Dense()
* __units__: Number of nodes in the hidden layer
* __kernel_initializer__: It initialize the weights of the connections. 
  * uniform: Initialize the weights with a small number close to zero but not zero.
* __activation__: Defines what would be the activation function  of the node. 
  * relu: Rectifier function(recommended for the hidden layers)
  * sigmoid: recommended for the output layer.
  * Softmax: recommended when there are multiple categorical output

### classifier.compile()
* __Optimizer__: An algorithm to find the optimal set of weights in the neural network after initial weights have been assigned. Gradient descent is one of the  optimizer. There are different implementation of this algorithm. Eg: ‘adam’
* __Loss__ : If the activation function is sigmoid the loss function is logarithmic loss function. If the output variable is binary output is called as binary_crossentropy and if the output is categorical then it is called as categorical_crossentropy.
* __Metrics__:  A criteria to evaluate our model. Majorly we use ‘accuracy’. So basically the weights are updated after each observation or each set of observations, the model use this accuracy criterion to improve the model performance.

### Epoch:
The number of time ANN is trained on the whole dataset.

### classifier.fit():
* __Batch_size__: number of records to be taken at a time
* __Epochs__: number of the the ANN should be run on whole dataset
