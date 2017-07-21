# Data Analysis and Machine learning:
There are several high quality datasets that are freely available.  In this repository, I will post jupyter notebooks showing my analysis of interesting datasets.    

## Table of Contents

* [UCI Heart Disease dataset](#1)
* [Spam Classification dataset](#2)

## UCI Heart Disease: <a id='1'></a>

Three clinics created datasets on patients suspected of having heart disease, which are publically available via the [UCI machine learning repository](archive.ics.uci.edu/ml/machine-learning-databases/heart-disease).   The actual dataset contains a list of 75 features including:

* age
* sex
* location of pain
* resting ecg results
* The diagnosis of heart disease presence and severity

With 75 features and 773 samples, the model is at risk of overfitting the data.  However, most of these features are not actually relevant and the classification accuracy levels off after selecting ~5 features using either mutual information or the anova f ratio.   
![accuracy vs no features](/images/accuracy_no_features.png) 

Based on this, we end up finding the best accuracy using only six features present in the original 75 feature dataset.   

Several types of classification were tried; however, the best score was due to the xgboost classifier, with logistic regression giving the second best results.  

|classifier|cross validation accuracy |
|:---------|---------|
|Random Forest | .568 |
|Logistic Regression | .572|
|Linear SVM | .542 |
|SVM with RBF Kernel | .541 |
| Xgboost Classifier | .575 |

When we tested the XGBoost Classifier on the test set, we achieved an accuracy of 56.7%, which means the algorithm wasn't overfitting.    In addition, we also used the XGBoost Classifier to find the relative importance of each feature it used in the dataset.   

|Feature | Relative Importance |
|:-------|------------|
|ST depression induced by exercise compared to rest | .497 |
|whether or not there was an exercise induced angina | .154 |
| whether or not pain was induced by exercise | .114 |
| whether or not the pain was relieved by rest | .108 |
| type of chest pain | .083 |


## Spam Classification <a id='2'></a>

Spam has been around since the beginning of the internet.  In fact, the use of spam over a network stretches al the way back to 1884 when wealthy americans were sent unsolicited investment offers over the telegraph\[[1](http://content.time.com/time/business/article/0,8599,1933796,00.html)\]  In more modern times, the first appearence of modern email spam occured on ARPANET, a military precurser to the internet, when "a man named Gary Turk sent an email solicitation to 400 people advertising his line of new computers'[1].  

The UCI machine learning repository has a collection of labeled spam and ham comments from five different youtube videos.  To classify these comments as spam or ham, I used three different simple machine learning algorithms, which were

* Logistic Regression
* Naive Bayes Classification
* Recurrent Neural Networks

Due to the small amount of training data, and the short nature of youtube comments.  The best classifiers turned out to be the simple ones, where Logistic Regression, and the Naive Bayes classifiers substantially outperformed the neural network.   

| Classifier | Training f1 score | Test f1 score |
|------------|------------------|----------------|
|Logistic Regression | .99 | .93 |
| Naive Bayes Classifier | .90 | .87 |
| Recurrent Neural Network | .93 | .74 |


