# Course1: Neural Networks and Deep Learning
The first course for [Deep Learning Specialization on Coursera](https://www.coursera.org/specializations/deep-learning).


## Objectives:

1. Be familiar with **Python(mainly Numpy)**. For python tutorials, you can also check [here](https://github.com/zyunsg/Python).
2. To know the general steps and relus when building a model, develop a model with separate module functions.
3. To undestand and implement **deep neural network** (structure, blocks, applications).

## Assignments & Quiz:
* [week1](https://github.com/zyunsg/deep-learning/tree/master/course1/week1) 
* [week2](https://github.com/zyunsg/deep-learning/tree/master/course1/week2) 
* [week3](https://github.com/zyunsg/deep-learning/tree/master/course1/week3)
* [week4](https://github.com/zyunsg/deep-learning/tree/master/course1/week4)

## Summary:

1. **Python Basics with numpy**: numpy matrix/vetor operations; broadcasting, working in iPython notebooks. 
   * numpy.xx: np.sum, np.dot, np.multiply, np.exp, np.reshape,etc...
   * sigmoid function and its gradient
   * image2vector
   * broadcasting concept
   * L1 and L2 loss definition 
   
2. **Logistic Regression with a Neural Network mindset**: it can be summarized and divided into following steps: 1.data preprocesing, 2.initialization, 3.propagate, 4.optimization, 5.prediction, which can be regarded as a general learning steps and rules to follow as well:)
   * build function separately: initialize(), propagate(), optimize(), predict(), then merge them to build model()
   * initialize(): initialize the weights w and bias b (w, b)
   * propagate(): forward, backward propagation
   * optimize(): optimize loss function iteratively by learning (w,b): step1: compute cost and gradient; step2: update parameters and its gradient descent
   * predict(): used above learned (w, b) to predict test dataset
   * learning rate choice: choose the one better minimized the cost function, 0.1, 0.01, 0.001... note their influence
   
3. **Planar data classification with a hidden layer**: understand NN model building steps and build a 2-layer NN.
   * hidden layer and its size impact. (a single hidden layer was applied in the assignment)
   * non-linear activation function, tanh
   * cross entropy loss
   * forward and backward propagation
   
4. **Building Deep Neural Network**: to undestand and implement deep neural network. 
   * Deep Neural Network Structure: ![deep NN structure](https://github.com/zyunsg/deep-learning-coursera/blob/master/course1/week4/images/final_outline.png) 
   * initialization: initialize (w, b) in all layers
   * L forward: L-1 linear relur forward, Lth layer linear sigmoid forward
   * cost function: compute cross-entropy cost J
   * L backward: Lth layer sigmoid -> linear, L-1 relu -> linear
   * update parameters with gradient descent
   
 5. **Deep Neural Network for Image Classification Application**. See how it works. 


   
