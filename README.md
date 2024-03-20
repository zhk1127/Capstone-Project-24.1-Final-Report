# Capstone-Project-24.1-Final-Report
This is the final report of my Capstone Project

Using Different Regression Models to Predict ASO toxicity

Goal: The goal of this project is to identify more effective algorithms to predict antisense nucleotides (ASO) toxicity based on their sequence features. We will be training several linear regression models without regularization or with regularization (L1 and L2) to predict ASO toxicity based on the linear combination of their sequence features. We will used the new models to identify the features which most effectively enhance the accuracy of predicting whether a ASO is toxic or not.

Data Problem: The data task is to train and tune multiple linear regression models with or without regularization to predict the toxicity score of ASOs based on their sequence features.

Expected Results: The expected results would be several models using linear combination of some selected sequence features from an antisense oligonucleotide (ASO) to predict its toxicity. The prediction results are continuous and not binary, but we can choose different thresholds to define a toxic ASO versus a non-toxic ASO and convert the result to binary labels. Then we can use confusion matrix or receiver operation curve (ROC) to compare the performance of different models. In the original paper, a linear regression model is published for this purpose and my goal is to reproduce the authors’ key results by building a similar or even better models.

Data: The data is a from published literature by Roche in 2022.

Link: https://www.ncbi.nlm.nih.gov/pmc/articles/PMC9221153

This paper has a supplementary table which contains 1,800 antisense oligonucleotides sequences and their performance in a calcium assay. Measured calcium score can be used as a indicator for ASO toxicity. The ASOs with smaller calcium score are more toxic than these with greater calcium scores.

Importance: My research question is important because big pharmaceutical companies like Roche, Biogen, Eli Lilly can spend >100 millions of dollars in developing genetic medicine (e.g. ASO) to treatment human disease. Currently, they rely on animal experiments and empirical evidence to determine the toxicity of an ASO. It is expensive and also time consuming. The capability to design a ASO without potential toxicity can streamline the whole drug development process and can create real values for these pharmaceutical companies. It is super important to figure out the sequence features within an ASO which can predict its toxcity.

Conclusions:
1. Linear Regression model gave rise to identical results as the published Roche model for all the coefficients, traing_MSE, test_MSE, which can validate the procedure of my modeling process.
2. Using Ridge or Lasso Regression did not significantly change the coefficients, traing_MSE, test_MSE, compared to the model without regularization.
3. It seems like the test_MSE is signifcantly larger than training_MSE for all the models, that could be due to the fact that the training set data was not collected use the identical manner as the testing set and there might be some systematic shift between tranining set values and test set values. Therefore, I also used some tools I learned for classification (e.g. confusion matrix, ROC curve) to further evaluate these models.
4. All the models suggest that the ASOs with more guanine (G) in its sequence tend be more toxic, because the feature Number_G has most negative coefficient, which is consistent with Roche published results.
5.  All the 3 models (Linear Regressio, Lasso Regression and Ridge Regression)  gave rise to very similar results in Confusion Matrix and ROC curve. The AUC for all the 3 ROC curves is around 0.82, which suggests that they perform relatively well for the classification task to predict toxic vs. non-toxic ASOs.
7.  After including new features, all the 3 models (Linear Regressio, Lasso Regression and Ridge Regression) start to outperform Roche model in terms of their smaller training_MSE and smaller test_MSE. However, even after including new features, all the 3 models (Linear Regressio, Lasso Regression and Ridge Regression) still perform very similarly in terms of the coefficients of all features and MSE value.
9.  A long string of adenosine (MaxLength_A) can make the ASO less toxic; ASOs with more guanine (Number_G) in its sequence tend be more toxic.
10.  After including new features, all the 3 models (Linear Regressio, Lasso Regression and Ridge Regression) outperform Roche model in accuracy curve, because they have greater maximum accuracy and the drop of their accuracy is less steep when we raise the threshold, but all the 3 models (Linear Regressio, Lasso Regression and Ridge Regression) don't outperform Roche model when they are evaluated using ROC curves.

Future directions
1.Explore additional regression models including Random Forest Regressor and Gradient Boosting Regressor may further improve the model performance, since there could be some non-linear relationship between the selected features and the ASO toxicity score
2.Explore addtional datasets from published literatures or patents to increase the sample size of training set my further improve the accuracy of the model
3.Spend additional efforts in feature engineering (e.g. adding the frequency information of all the 16 types of dinucleotides) may further improve the model accuracy
