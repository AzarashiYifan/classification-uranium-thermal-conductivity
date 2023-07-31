# Machine Learning - SMOTE

This project uses a RandomForest Classifier to classify materials based on their properties. The model uses the Synthetic Minority Over-sampling Technique (SMOTE) to balance the classes in the training data. The model is trained using stratified group k-fold cross-validation. The project also includes methods to evaluate model performance.

## Overview

1. **Data Preparation**: The data is loaded from a CSV file. The feature matrix `X` is all columns excluding 'class' and 'main_elements'. The target variable `y` is the 'class' column. The groups for stratified group k-fold cross-validation are defined by the 'main_elements' column.

2. **Model Initialization**: A RandomForest Classifier model is initialized with a random state for reproducibility and n_jobs set to -1 for using all processors.

3. **Cross-validation with SMOTE**: StratifiedGroupKFold cross-validation is used. For each fold, a SMOTE object is created and used to oversample the minority classes in the training set. The model is then fitted on the resampled data.

4. **Model Evaluation**: Precision, recall, F1-score, and support are calculated for each class and averaged over all folds. The confusion matrix for each fold is also calculated and stored for future use.

5. **Training a Final Model with SMOTE**: A final RandomForest model is trained on the entire dataset resampled with SMOTE.

6. **Extracting Feature Importances**: Feature importances are extracted from the final model. The top 10 features based on their importances are identified.

7. **Model Saving**: The trained model is saved into a pickle file for future use.

8. **Confusion Matrix Calculation**: The sum and normalized confusion matrix of all folds are calculated.
