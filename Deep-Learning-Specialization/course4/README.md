# Course4: Convolutional Neural Networks
The **fourth** course for [Deep Learning Specialization on Coursera](https://www.coursera.org/specializations/deep-learning).


## Objectives

1. To understand the convolution, pooling operation, and some terms: padding, stride, filter.
2. To know some classic networks, build DNN with [Keras](https://keras.io/).
3. Implement a Residual network.
4. To understand object detection with YOLO algorithm.
5. To learn Face verification & recognition.
6. To understand & implement Neural Style Transfer algorithm: generate artistic images

## Assignments & Quiz

* [week1](https://github.com/zyunsg/deep-learning/tree/master/course4/week1) 
* [week2](https://github.com/zyunsg/deep-learning/tree/master/course4/week2)
* [week3](https://github.com/zyunsg/deep-learning/tree/master/course4/week3)
* [week4](https://github.com/zyunsg/deep-learning/tree/master/course4/week4)

## Summary

#### 1. Convolutional Neural Networks: Step by Step
* Convolution functions: transforms the input volume into an **different size** output volume
    - zero Padding: avoid shrinking height/width of the volumes. "same": height/width is exactly preserved after one layer
    - convolve window: apply filter by element-wise multiplying -> sum values up -> add bias
    - convolution forward
    - convolution backward
* Pooling functions: help reduce height and width of the input, and make feature detectors more invariant to its position in the input
    - two types: Max-pooling, Average-pooling
    - no parameters to train, but have hyperparameters, such as window size f
    - pooling forward
    - pooling backward
   
#### 2. Convolutional Neural Networks: Application: build ConvNet in TensorFlow for classification problem
* model()
   * create placeholder() 
     - [tf.placeholder()](https://www.tensorflow.org/api_docs/python/tf/placeholder)
   * initialize parameters()
     - [tf.get_variable(, initializer=tf.contrib.layers.xavier_initializer(seed=0))](https://www.tensorflow.org/api_docs/python/tf/get_variable)
   * forward propagation(): Conv2D -> Relu -> Max pool -> Conv2D -> Relu -> Max pool -> Flatten -> Fullyconnected (FC) layer
     - [tf.nn.conv2d()](https://www.tensorflow.org/api_docs/python/tf/nn/conv2d)
     - [tf.nn.max_pool()](https://www.tensorflow.org/api_docs/python/tf/nn/max_pool)
     - [tf.nn.relu()](https://www.tensorflow.org/api_docs/python/tf/nn/relu)
     - [tf.contrib.layers.flatten()](https://www.tensorflow.org/api_docs/python/tf/contrib/layers/flatten)
     - [tf.contrib.layers.fully_connected()](https://www.tensorflow.org/api_docs/python/tf/contrib/layers/fully_connected)
   * compute cost()
     - [tf.nn.softmax_cross_entropy_with_logits()](https://www.tensorflow.org/api_docs/python/tf/nn/softmax_cross_entropy_with_logits)
     - [tf.reduce_mean()](https://www.tensorflow.org/api_docs/python/tf/reduce_mean)
   * optimizer()
     - [tf.train.AdamOptimizer().minimize(cost)](https://www.tensorflow.org/api_docs/python/tf/train/AdamOptimizer)
   * initialize all variables globally
     - [tf.global_variables_initializer()](https://www.tensorflow.org/api_docs/python/tf/global_variables_initializer)
   * start session: (loop for num_epochs, get and optimize each mini-batch)
     
#### 3. Keras tutorial - the happy house
* four steps in Keras
    1. create the model 
       - define input placeholder: Input()
       - zero-padding: ZeroPadding2D()
       - CONV -> BN -> RELU block: CONV2D() -> BatchNormalization() -> Activation('relu')
       - Maxpool: MaxPooling2D()
       - flattn: Flatten()
       - fullyconnected: Dense()
       - create model: Model(inputs= , outputs= , name= )
    2. compile: model.compile(optimizer = "...", loss = "...", metrics = ["accuracy"])
    3. fit/train: model.fit(x = ..., y = ..., epochs = ..., batch_size = ...)
    4. evaluate/test: model.evaluate(x = ..., y = ...)
* model.summary(): prints layers details
* plot_model(): plot graph

#### 4. Residual Networks
* very deep "plain" networks don't work in practice because they are hard to train due to vanishing gradients
* a shortcut or skip-connections help address the Vanishing Gradient problem
* two types of blocks
    - identity block: the dimensions of input and output are the same
    - convolutional block: the dimensions of input and output do not match up
    - the **main difference** between them is that there is a conv2d layer in the shortcut path
* implementation
    - [conv2D](https://keras.io/layers/convolutional/#conv2d)
    - [BatchNorm](https://keras.io/layers/normalization/#batchnormalization)
    - activation: Activation('relu)
    - [Addition for shortcut path](https://keras.io/layers/merge/#add)

#### 5. Autonomous driving - Car detection
* bounding boxes: (p_c, b_x, b_y, b_h, b_w, c)
  - p_c: confidence of an object being present in the bounding box
  - b_x, b_y: midpoint coordinate of the bounding box
  - b_h, b_w: height/width of the bouding box
  - c: dimensional vector to represent object
* YOLO("you only look once"): object detection model, use pretrained model parameters in this exercise
   - input(m,608,608,3) -> CNN -> output(m,19,19,5,85)
   - flatten output: (m,19,19,425)
     - Each cell in a 19x19 grid over the input image gives 425 numbers. 
     - 425 = 5 x 85 because each cell contains predictions for 5 boxes, corresponding to 5 anchor boxes, as seen in lecture. 
     - 85 = 5 + 80 where 5 is because (p_c, b_x, b_y, b_h, b_w) has 5 numbers, and and 80 is the number of classes we'd like to detect
   - select only few boxes based on:
     - Score-thresholding: throw away boxes that have detected a class with a score less than the threshold
     - Non-max suppression: Compute the Intersection over Union and avoid selecting overlapping boxes
   - gives ouput
   
#### 6. Face Recognition for the Happy House
* two categories
  - face verification: 1:1 matching problem 
  - face recognition: 1:K matching problem
* triplet loss function
  - Anchor(A), Positive(P), Negative(N)
* the same encoding can be used for verification and recognition

#### 7. Deep Learning & Art: Neural Style Transfer
* Neural Style Transfer(NST)
  - content image C
  - style image S
  - generated image G
* NST uses representaions (hidden layer activations) based on **a pretrained ConvNet**
  - earlier layers: detect low-level features, such as edges, simple textures
  - deeper layers: detect high-level features, more complex textures as well as object classess
* total cost
  - alpha & beta: controls the relative weighting between content and style
  - content cost function: generally use one hidden layer's activations
  - style cost function: use multiple layers, compute one layer by Gram matrix
* steps to implement a NST
    1. create an Interactive Session
    2. load the content image 
    3. load the style image
    4. randomly initialize the image to be generated 
    5. load the VGG16 model
    7. build the TensorFlow graph:
        - run the content image through the VGG16 model and compute the content cost
        - run the style image through the VGG16 model and compute the style cost
        - compute the total cost
        - define the optimizer and the learning rate
    8. initialize the TensorFlow graph and run it for a large number of iterations, updating the generated image at every step.

 ## References
 1. **Residual Networks**
    - [Deep Residual Learning for Image Recognition (2015)](https://arxiv.org/abs/1512.03385)
    - [Francois Chollet's github repository](https://github.com/fchollet/deep-learning-models/blob/master/resnet50.py)
 2. **YOLO**
    - [You Only Look Once: Unified, Real-Time Object Detection](https://arxiv.org/abs/1506.02640)
    - [YOLO9000: Better, Faster, Stronger](https://arxiv.org/abs/1612.08242)
    - [YAD2K: Yet Another Darknet 2 Keras](https://github.com/allanzelener/YAD2K)
    - [YOLO official website](https://pjreddie.com/darknet/yolo/)
 3. **Face Recognition**
    - [FaceNet: A Unified Embedding for Face Recognition and Clustering](https://arxiv.org/pdf/1503.03832.pdf)
    - [DeepFace: Closing the gap to human-level performance in face verification](https://research.fb.com/wp-content/uploads/2016/11/deepface-closing-the-gap-to-human-level-performance-in-face-verification.pdf) 
    - [Keras-OpenFace source code](https://github.com/iwantooxxoox/Keras-OpenFace)
    - [Facenet github](https://github.com/davidsandberg/facenet)
 4. **Deep Learning & Art: Neural Style Transfer**
    - [A Neural Algorithm of Artistic Style](https://arxiv.org/abs/1508.06576) 
    - [Convolutional neural networks for artistic style transfer](https://harishnarayanan.org/writing/artistic-style-transfer/)
    - [Log0, TensorFlow Implementation of "A Neural Algorithm of Artistic Style](http://www.chioka.in/tensorflow-implementation-neural-algorithm-of-artistic-style)
    - [Very deep convolutional networks for large-scale image recognition](https://arxiv.org/pdf/1409.1556.pdf)
    - [MatConvNet](http://www.vlfeat.org/matconvnet/pretrained/)
 



