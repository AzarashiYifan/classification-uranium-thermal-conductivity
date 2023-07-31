# Uranium Material Classification and Prediction Project

## Overview

This project aims to classify and predict potential uranium compounds with high thermal conductivity. It includes a series of Jupyter notebooks and trained machine learning models for data preparation, model training, and prediction. The steps to operate the project are as follows:

## Getting Started

1. **Build the Environment with Docker**

   Begin by building the environment using the Dockerfile provided in the project. This step ensures that all dependencies are correctly installed.

## Data Preparation

2. **Data Filtering (`data_prep.ipynb`)**

   Run the `data_prep.ipynb` notebook to filter and prepare the data. This notebook processes the raw data and prepares it for subsequent model training. The output of this notebook is a cleaned and processed dataset ready for the next stage.

## Model Training

3. **Train Models (`imba_model.ipynb`, `smote_model.ipynb`, `smote_rus_model.ipynb`)**

   The project includes three different models, each trained with a different strategy for handling the class imbalance in the dataset:

   - `imba_model.ipynb`: Trained on the original, imbalanced dataset.
   - `smote_model.ipynb`: Trained on a dataset balanced using the Synthetic Minority Over-sampling Technique (SMOTE).
   - `smote_rus_model.ipynb`: Trained on a dataset balanced using a combination of SMOTE and Random Under Sampling (RUS).

   You can run these notebooks to retrain the models. Each notebook saves the trained model as a pickle file for future use.

## Prediction

4. **Predict the Candidates (`prediction.ipynb`)**

   The `prediction.ipynb` notebook uses the trained model (by default, the SMOTE model) to predict potential uranium compounds with high thermal conductivity.

5. **Filter and Rank the Predictions (`mp_uranium_compounds.ipynb`, `melting_points.ipynb`)**

   These two notebooks are used to filter and rank the final predictions. Run the `mp_uranium_compounds.ipynb` and `melting_points.ipynb` notebooks in order to sort the predicted uranium compounds.

By following the steps above, you can prepare the data, train the models, and generate predictions for potential uranium compounds with high thermal conductivity.
