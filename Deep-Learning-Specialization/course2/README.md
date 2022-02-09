# Course2: Improving Deep Neural Networks: Hyperparameter tuning, Regularization and Optimization
The second course for [Deep Learning Specialization on Coursera](https://www.coursera.org/specializations/deep-learning).


## Objectives:

1. Implement different types of **initialization**, L2 and dropout **regularization**, **Batch normalization** and **gradient checking**, check their corresponding performance.
2. Implement and apply a variety of optimization algorithms, **Stochastic Gradient Descent(SGD)**, **mini-batch gradient descent**, **Momentum**, **Adam**, and check for their convergence. 
3. Implement a neural network in **TensorFlow**. 

## Assignments & Quiz:

* [week1](https://github.com/zyunsg/deep-learning/tree/master/course2/week1) 
* [week2](https://github.com/zyunsg/deep-learning/tree/master/course2/week2)
* [week3](https://github.com/zyunsg/deep-learning/tree/master/course2/week3)

## Summary:

1. **Initialization**: a well initialization can speed up the convrgence of gradient descent and increase the odds of gradient descent converging to a lower training error.
   * Different initializations lead to different results (Zero/Random/He initialization)
   * The weights should be initialized randomly to break symmetry, while the biases can be initialized to zeros. Random initialization is used to break symmetry and make sure different hidden units can learn different things.
   * Don't intialize to values that are too large
   * He initialization works well for networks with ReLU activations. 
2. **Regularization**: reduce overfitting.
   * Regularization will drive weights to lower values.
   * L2 regularization and Dropout are two very effective regularization techniques.
   * L2 regularization: the term is added to the cost, extra term in backpropagation, weight decay.
   * Dropout: use only during training, not during test time; apply both during forward and backward propagation; scale neurons value (by dividing keep_prob).

3. **Gradient Checking**: prove the implemented backpropagation is actually working.
   * Gradient checking verifies closeness between the gradients from backpropagation and the numerical approximation of the gradient (computed using forward propagation).
   * Gradient checking is slow, so don't run it in every iteration of training, and usually run it only to make sure code is correct, then turn it off and use backprop for the actual learning process.

4. **Tensorflow**: tensorflow framework in deep learning, try to be familiar with it, the following tutorial will be quite helpful.
   * Other tutorials: [stanford cs20si: Tensorflow for Deep Learning Research](https://web.stanford.edu/class/cs20si/)



