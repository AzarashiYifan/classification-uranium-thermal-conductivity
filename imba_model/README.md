# Machine Learning - Imbalanced Dataset

This project uses a RandomForest Classifier to classify materials based on their properties. The model is trained using stratified group k-fold cross-validation to handle imbalanced data. The project also includes methods to evaluate model performance and visualize important features.

## Overview

1. **Data Preparation**: The data is loaded from a CSV file, with the features and target variable identified. The feature matrix `X` is all columns excluding 'class' and 'main_elements'. The target variable `y` is the 'class' column. The groups for stratified group k-fold cross-validation are defined by the 'main_elements' column.

2. **Model Initialization**: A RandomForest Classifier model is initialized with a random state for reproducibility and n_jobs set to -1 for using all processors.

3. **Cross-validation**: StratifiedGroupKFold cross-validation is used to ensure that each fold retains the same proportion of samples from each class as the whole dataset. It also ensures that all samples in a group are included in the same test set. This method is especially useful when dealing with imbalanced datasets.

4. **Model Evaluation**: Precision, recall, F1-score, and support are calculated for each class and averaged over all folds. The confusion matrix for each fold is also calculated and stored for future use.

5. **Training a Final Model**: A final RandomForest model is trained on the entire dataset. The top 10 features based on their importances are identified.

6. **Model Saving**: The trained model is saved into a pickle file for future use.

7. **Visualizing Model Performance and Features**: The confusion matrix is visualized and saved as a PNG image. The feature importances are also visualized and saved as a PNG image.
