# Week3: Classification of Text

## Objective
1. Text classification approaches comparision.
2. Naive Bayes vs SVM
3. Learn how to identify and extract features from text and transform them into feature vectors for models.

## Summary 
1. Multi-class classification vs Multi-label classfication
2. Textual features: 
    + words: remove stop words, normalization, stemming/lemmatization 
    + characteristics of words: capitalization
    + parts of speech of words in a sentence
    + grammatical structure, sentence parsing
    + grouping words of similar meaning, semantics
    + n-grams
3. naive bayes: 
   + a probabilistic model
   + assumes features are independent of each other, given the class label
   + for text classification problem, naive bayes models typically provide strong baselines
   + multinomial nv, bernoulli nv. 
4. Support Vector Machines(SVM): SVMs are liear classifier that find a hyperplane to separate **two classes** of data: positive and negative.
   + Multi-class classification: One vs Rest -> n-class SVM has n classifiers; one vs one -> n-class SVM has C(n,2) classifiers. 
   + Regularization parameter c: larger c = less regularization
   + Linear kernels work best for text data:
   + SVM tend to be the most accurate classifier, especially in high-dimensional data
   + Handles only numeric features: Convert categorical features to numerical features; Normalization 
   + Hyperplane hard to interpret 
5. Toolkits: Scikit-learn, NLTK 
   
