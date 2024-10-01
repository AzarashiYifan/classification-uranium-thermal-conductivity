# Uranium Material Classification and Prediction (archived)

## Overview

This project aims to classify and predict potential uranium compounds with high thermal conductivity. It includes a series of Jupyter notebooks and trained machine learning models for data preparation, model training, and prediction. The steps to operate the project are as follows:

## Getting Started

1. **Build the Environment with Docker**

   Begin by building the environment using the Dockerfile provided in the project. This step ensures that all dependencies are correctly installed.

2. **Obtain MP-API Key**
   
   Log in to Materials Project to obtain the API Key at https://next-gen.materialsproject.org/api

## Data Preparation

3. **Data Filtering (`data/data_prep.ipynb`)**

   The `20230112_interpolated_data.csv` file can be downloaded at https://figshare.com/articles/dataset/20230112_starrydata2/21929736

   Run the `data_prep.ipynb` notebook to filter and prepare the data. This notebook processes the raw data and prepares it for subsequent model training. The output of this notebook is a cleaned and processed dataset ready for the next stage.

## Model Training

4. **Train Models (`imba_model.ipynb`, `smote_model.ipynb`, `smote_rus_model.ipynb`)**

   The project includes three different models, each trained with a different strategy for handling the class imbalance in the dataset:

   - `imba_model.ipynb`: Trained on the original, imbalanced dataset.
   - `smote_model.ipynb`: Trained on a dataset balanced using the Synthetic Minority Over-sampling Technique (SMOTE).
   - `smote_rus_model.ipynb`: Trained on a dataset balanced using a combination of SMOTE and Random Under Sampling (RUS).

   You can run these notebooks to retrain the models. Each notebook saves the trained model as a pickle file for future use.

   The confusion matrix and feature importance are generated and plotted accordingly.

## Prediction

5. **Filter and Rank the Predictions (`data/prediction_data/mp_uranium_compounds.ipynb`, `data/prediction_data/melting_points.ipynb`)**

   These two notebooks are used to gather information for making and filtering the predictions.
   - `mp_uranium_compounds.ipynb`: Fetches a list of stable uranium compounds from Materials Project
   - `melting_points.ipynb`: Fetches the melting points of elements from Pymatgen
  
6. **Predict the Candidates (`prediction.ipynb`)**

   The `prediction.ipynb` notebook uses the trained model (by default, the SMOTE model) to predict potential uranium compounds with high thermal conductivity.
   The candidatse are ranked based on their uranium density

By following the steps above, you can prepare the data, train the models, and generate predictions for potential uranium compounds with high thermal conductivity.
