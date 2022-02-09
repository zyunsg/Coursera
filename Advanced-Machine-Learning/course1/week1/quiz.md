# Linear models

1. Consider a vector (1,−2,0.5). Apply a softmax transform to it and enter the first component (accurate to 2 decimal places).
   - 0.60
   
2. Suppose you are solving a 5-class classification problem with 10 features. How many parameters a linear model would have? Don't forget bias terms!
   - 55
   
3. There is an analytical solution for linear regression parameters and MSE loss, but we usually prefer gradient descent optimization over it. What are the reasons?
   - [x] Gradient descent doesn't require to invert a matrix
   - [x] Gradient descent is more scalable and can be applied for problems with high number of features
 
 
# Overfitting and regularization

1. Select correct statements about overfitting:
   - [x] Overfitting is a situation where a model gives comparable quality on new data and on a training sample
   - [x] Large model weights can indicate that model is overfitted

2. What disadvantages do model validation on holdout sample have?
   - [x] It can give biased quality estimates for small samples
   - [x] It is sensitive to the particular split of the sample into training and test parts
   
3. Suppose you are using k-fold cross-validation to assess model quality. How many times should you train the model during this procedure?
   - [x] k
   
4. Select correct statements about regularization:
   - [x] Weight penalty drives model parameters closer to zero and prevents the model from being too sensitive to small changes in features
   - [x] Regularization restricts model complexity (namely the scale of the coefficients) to reduce overfitting
