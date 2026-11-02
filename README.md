# Skin Disease Classification

A machine learning project that classifies six types of erythemato-squamous skin diseases using clinical and histopathological features.

## Overview

Skin diseases can be difficult to tell apart because many of them share similar visible and microscopic features. This project explores a dermatology dataset of 366 patients and compares three classification models to see how well they predict the disease.

The project covers:

1. **Exploratory data analysis (EDA):** understanding the data, checking quality, and examining feature patterns.
2. **Model comparison:** Logistic Regression, Random Forest, and Support Vector Machine (SVM), evaluated with 10-fold stratified cross-validation and a held-out test set.
3. **Feature importance:** identifying which features each model relies on most, using permutation importance.
4. **Suggestions for clinicians:** practical points to support early identification of these diseases.

## Diseases Classified

| Class | Disease |
|---|---|
| 1 | Psoriasis |
| 2 | Seborrheic dermatitis |
| 3 | Lichen planus |
| 4 | Pityriasis rosea |
| 5 | Chronic dermatitis |
| 6 | Pityriasis rubra pilaris |

## Dataset

- **Source:** Dermatology dataset, UCI Machine Learning Repository
- **Patients:** 366
- **Features:** 34 input features (11 clinical, 22 histopathological, and Age)
- **Target:** disease class (1 to 6)
- **Missing values:** 8 missing ages, filled with the median of the training data only

## Methods

- **Train/test split:** 80% training, 20% testing, stratified by disease class
- **Preprocessing:** median imputation for Age, and standard scaling for Logistic Regression and SVM, both placed inside pipelines to prevent data leakage
- **Validation:** 10-fold stratified cross-validation on the training data
- **Final evaluation:** a single held-out test set of 74 patients
- **Feature importance:** permutation importance on the training data

## Results

| Model | Cross-validation accuracy | Test accuracy |
|---|---|---|
| Logistic Regression | 97.93% | 95.95% |
| Random Forest | 97.94% | 95.95% |
| SVM | 97.93% | 97.30% |

All three models performed very similarly. The differences are smaller than the variation between folds, so no model is clearly superior. Most misclassifications involved Seborrheic dermatitis and Pityriasis rosea, which share similar features.

The features that appeared consistently important across models include koebner phenomenon, fibrosis of the papillary dermis, spongiosis, and PNL infiltrate.

## Limitations

- The dataset is small (366 patients), and some disease classes have only 20 to 30 examples.
- The test set has only 74 patients, so one prediction changes accuracy by about 1.4%.
- Hyperparameters were not systematically tuned.
- Feature importance shows model behaviour, not medical causation.
- The models are for educational purposes and must not be used for clinical diagnosis.

## Files

- `skin_disease_classification.ipynb`: the complete notebook with code, outputs, and explanations

## How to Run

1. Open the notebook in [Jupyter](https://jupyter.org) or [Google Colab](https://colab.research.google.com).
2. Install the required libraries if they are not already available: pandas, numpy, matplotlib, seaborn, and scikit-learn.
3. Place the dataset file `dataset_35_dermatology (1).csv` in the same folder as the notebook. The dataset is available from the UCI Machine Learning Repository.
4. Run all cells from the top (Restart & Run All).


