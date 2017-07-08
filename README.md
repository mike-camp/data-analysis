# Data Analysis and Machine learning:
There are several high quality datasets that are freely available.  In this repository, I will post jupyter notebooks showing my analysis of interesting datasets.    

## UCI Heart Disease:

Three clinics created datasets on patients suspected of having heart disease, which are publically available via the [UCI machine learning repository](archive.ics.uci.edu/ml/machine-learning-databases/heart-disease).   The actual dataset contains a list of 75 features including:

* age
* sex
* location of pain
* resting ecg results
* The diagnosis of heart disease presense and severity

With 75 features and 773 samples, the model is at risk of overfitting the data.  However, most of these features are not actually relevent and the classification accuracy levels off after selecting ~5 features using either mutual information or the anova f ratio.   
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



