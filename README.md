# Comparative Analysis of Traditional Machine Learning and Deep Learning for Predicting Depression History Using CDC BRFSS Data

## Project Overview

This project compares traditional machine learning and deep learning approaches for predicting self-reported depression history using the 2024 Centers for Disease Control and Prevention (CDC) Behavioral Risk Factor Surveillance System (BRFSS) dataset.

The study investigates whether deep learning provides a predictive performance advantage over traditional machine learning when applied to structured public health survey data.

**Important:** The prediction target represents whether respondents reported ever being told by a healthcare professional that they had a depressive disorder. It does not represent a clinical diagnosis or necessarily indicate current depression.

## Dataset

- **Source:** CDC Behavioral Risk Factor Surveillance System (BRFSS), 2024
- **Original observations:** 457,670
- **Observations after target cleaning:** 455,006
- **Predictor variables:** 12
- **Target variable:** `ADDEPEV3`
- **Positive class:** Reported depression history
- **Negative class:** No reported depression history

The dataset was divided into training (70%), validation (15%), and testing (15%) subsets using stratified sampling.

### Selected Features

Age group, sex, education, employment status, income, general health, physical health, mental health, exercise participation, marital status, body mass index, and smoking history.

## Methodology

The workflow included:

1. Dataset acquisition and exploration
2. Data cleaning and missing-value handling
3. Feature selection and preprocessing
4. Stratified train-validation-test splitting
5. Traditional machine learning experiments
6. TensorFlow/Keras neural network experiments
7. Class imbalance handling and threshold optimization
8. Model comparison using validation data
9. Final evaluation on the held-out test dataset

Categorical features were imputed and one-hot encoded, while numerical features were imputed and standardized. Preprocessing was fitted exclusively on training data.

## Models Evaluated

**Traditional machine learning:**
- Logistic Regression
- Random Forest
- Histogram-Based Gradient Boosting

**Deep learning:**
- Baseline Artificial Neural Network
- Class-Weighted Artificial Neural Network
- Class-Weighted Artificial Neural Network with Dropout

Deep learning experiments used TensorFlow/Keras and `tf.data` pipelines.

## Final Test-Set Results

| Model | Accuracy | Precision | Recall | F1-score | ROC-AUC |
|---|---:|---:|---:|---:|---:|
| Gradient Boosting | 0.7914 | 0.5050 | 0.6375 | 0.5636 | 0.8158 |
| Dropout ANN | 0.7846 | 0.4926 | 0.6570 | 0.5630 | 0.8154 |

Both models used classification thresholds of 0.60, selected using validation data.

Gradient Boosting achieved marginally higher accuracy, precision, F1-score, and ROC-AUC. The Dropout ANN achieved higher recall.

The results suggest that the selected deep learning architecture did not provide a substantial performance advantage over the selected traditional machine learning model on this dataset.

## Technologies Used

- Python
- Google Colab
- Pandas and NumPy
- Scikit-learn
- TensorFlow/Keras
- Matplotlib and Seaborn
- Joblib
- Google Drive

## Reproducibility

The project notebook contains the preprocessing workflow, model training, experiments, validation results, and final test-set evaluation.

The original dataset is available from the [CDC BRFSS website](https://www.cdc.gov/brfss/annual_data/annual_2024.html).

To reproduce the experiments:

1. Open the notebook in Google Colab.
2. Obtain the 2024 BRFSS SAS XPORT dataset ZIP.
3. Save the ZIP as `LLCP2024XPT.zip` in the Google Drive project folder expected by the notebook, or update the dataset path.
4. Run the notebook cells in order.
5. Ensure the required Python packages are installed.

Training all models may require substantial computation.

## Limitations

- The target is based on self-reported depression history, not clinical assessment.
- Survey responses may be affected by recall and reporting bias.
- The dataset is imbalanced.
- Survey weights and the complex sampling design were not incorporated into this analysis.
- Predictive associations should not be interpreted as causal relationships.
- The models are research experiments
