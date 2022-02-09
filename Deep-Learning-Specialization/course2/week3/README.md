# Week3 Quiz: Hyperparameter tuning, Batch Normalization, Programming Frameworks

1. If searching among a large number of hyperparameters, you should try values in a grid rather than random values, so that you can carry out the search more systematically and not rely on chance. True or False?
   - [ ] True
   - [x] False

2. Every hyperparameter, if set poorly, can have a huge negative impact on training, and so all hyperparameters are about equally important to tune well. True or False?
   - [ ] True
   - [x] False

3. During hyperparameter search, whether you try to babysit one model (“Panda” strategy) or train a lot of models in parallel (“Caviar”) is largely determined by:
   - [ ] Whether you use batch or mini-batch optimization
   - [ ] The presence of local minima (and saddle points) in your neural network
   - [x] The amount of computational power you can access
   - [ ] The number of hyperparameters you have to tune

4. If you think β (hyperparameter for momentum) is between on 0.9 and 0.99, which of the following is the recommended way to sample a value for beta?
   - [ ] ```
          r = np.random.rand() 
          beta = r*0.09 + 0.9 
         ```
   - [x] ```
          r = np.random.rand() 
          beta = 1-10**(- r - 1)
         ```
   - [ ] ```
          r = np.random.rand() 
          beta = 1-10**(- r + 1)
         ```
   - [ ] ```
          r = np.random.rand()
          beta = r*0.9 + 0.09 
         ```
5. Finding good hyperparameter values is very time-consuming. So typically you should do it once at the start of the project, and try to find very good hyperparameters so that you don’t ever have to revisit tuning them again. True or false?
   - [ ] True
   - [x] False
   
6. In batch normalization as presented in the videos, if you apply it on the lth layer of your neural network, what are you normalizing?
   - [ ] a[l]
   - [ ] W[l]
   - [x] z[l]
   - [ ] b[l]
   
7. In the normalization formula z(i)_norm = (z(i)−μ) / √(σ2+ε), why do we use epsilon?
    - [ ] To have a more accurate normalization
    - [x] To avoid division by zero
    - [ ] To speed up convergence
    - [ ] In case μ is too small
   
8. Which of the following statements about γ and β in Batch Norm are true?
    - [ ] The optimal values are γ=√(σ2+ε), and β=μ.
    - [ ] There is one global value of γ∈R and one global value of β∈R for each layer, and applies to all the hidden units in that layer.
    - [ ] β and γ are hyperparameters of the algorithm, which we tune via random sampling.
    - [x] They can be learned using Adam, Gradient descent with momentum, or RMSprop, not just with gradient descent.
    - [x] They set the mean and variance of the linear variable z[l] of a given layer.

9. After training a neural network with Batch Norm, at test time, to evaluate the neural network on a new example you should:
    - [ ] Skip the step where you normalize using μ and σ2 since a single test example cannot be normalized.
    - [ ] Use the most recent mini-batch’s value of μ and σ2 to perform the needed normalizations.
    - [ ] If you implemented Batch Norm on mini-batches of (say) 256 examples, then to evaluate on one test example, duplicate that example 256 times so that you’re working with a mini-batch the same size as during training.
    - [x] Perform the needed normalizations, use μ and σ^2 estimated using an exponentially weighted average across mini-batches seen during training.
    
10. Which of these statements about deep learning programming frameworks are true? (Check all that apply)
       - [x] Even if a project is currently open source, good governance of the project helps ensure that the it remains open even in the long term, rather than become closed or modified to benefit only one company.
       - [ ] Deep learning programming frameworks require cloud-based machines to run.
       - [x] A programming framework allows you to code up deep learning algorithms with typically fewer lines of code than a lower-level language such as Python.
 
    
   
   
   
   
   
   
   
   
   
   
