  # Machine Learning - Imbalanced Dataset Handling with SMOTE and RUS

This project applies a combination of Synthetic Minority Over-sampling Technique (SMOTE) and Random Under-sampling (RUS) to tackle the issue of imbalanced data. A RandomForest Classifier is used to classify materials based on their properties. The model is trained using stratified group k-fold cross-validation to ensure a fair distribution of classes in each fold. Performance of the model is evaluated using precision, recall, and F1-score. 

## Overview

1. **Data Preparation**: The data is loaded from a CSV file. The feature matrix `X` is all columns excluding 'class' and 'main_elements'. The target variable `y` is the 'class' column. The groups for stratified group k-fold cross-validation are defined by the 'main_elements' column.

2. **Model Initialization**: A RandomForest Classifier model is initialized with a random state for reproducibility and n_jobs set to -1 for using all processors.

3. **Cross-validation**: StratifiedGroupKFold cross-validation is used to ensure that each fold retains the same proportion of samples from each class as the whole dataset. It also ensures that all samples in a group are included in the same test set. This method is especially useful when dealing with imbalanced datasets.

4. **Data Balancing**: SMOTE is used to oversample the minority classes in the training data. RUS is then applied to under-sample the majority class, resulting in a balanced training set.

5. **Model Evaluation**: Precision, recall, F1-score, and support are calculated for each class and averaged over all folds. The confusion matrix for each fold is also calculated and stored for future use.

6. **Training a Final Model**: A final RandomForest model is trained on the entire dataset, using the same SMOTE and RUS strategy. The top 10 features based on their importances are identified.

7. **Model Saving**: The trained model is saved into a pickle file for future use.
