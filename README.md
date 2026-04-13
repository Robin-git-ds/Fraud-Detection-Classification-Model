# Fraud Detection Classification Model

This project implements a comprehensive fraud detection system for financial transactions using machine learning techniques. It addresses class imbalance issues and compares multiple classification algorithms to identify fraudulent transactions.

## Overview

The system processes financial transaction data to detect fraud using both traditional machine learning models and graph-based analysis. It handles severe class imbalance through SMOTE oversampling and evaluates models using comprehensive metrics.

## Features

- **Data Preprocessing**: Feature selection and train-test splitting
- **Class Imbalance Handling**: SMOTE (Synthetic Minority Oversampling Technique)
- **Multiple ML Models**:
  - Decision Tree Classifier
  - Random Forest Classifier
  - Support Vector Machine (SVM)
- **Comprehensive Evaluation**: Accuracy, Precision, Recall, F1-Score, Confusion Matrix
- **Graph-based Detection**: BFS algorithm for transaction network analysis
- **Visualization**: Confusion matrices for model performance

## Dataset

**Note**: The dataset file `fadml_dummy.csv` is not included in this repository due to size constraints. You need to obtain the financial transaction dataset and place it in the project directory.

The expected dataset format includes features such as:
- `step`: Time step of the transaction
- `amount`: Transaction amount
- `oldbalanceOrg`: Origin account balance before transaction
- `newbalanceOrig`: Origin account balance after transaction
- `oldbalanceDest`: Destination account balance before transaction
- `newbalanceDest`: Destination account balance after transaction
- `nameOrig`: Origin account ID
- `nameDest`: Destination account ID
- `isFraud`: Target variable (0: legitimate, 1: fraudulent)

## Algorithm Workflow

### 1. Data Preparation
- Load transaction dataset
- Select relevant features
- Split into training (80%) and testing (20%) sets

### 2. Handling Class Imbalance
- Apply SMOTE to oversample minority class (fraudulent transactions)
- Create synthetic samples to balance the dataset

### 3. Model Training and Evaluation
Train and evaluate three classification models on resampled data:
- **Decision Tree**: Simple, interpretable model
- **Random Forest**: Ensemble method for better accuracy
- **SVM**: Effective for high-dimensional data

### 4. Graph-based Fraud Detection
- Build transaction graph (accounts as nodes, transactions as edges)
- Use BFS to traverse transaction networks
- Identify suspicious patterns based on amount thresholds and balance ratios

## Requirements

- Python 3.7+
- pandas
- numpy
- scikit-learn
- imbalanced-learn
- matplotlib

## Installation

1. Install dependencies:
   ```bash
   pip install -r requirements.txt
   ```

2. Place the dataset file `fadml_dummy.csv` in the project directory.

## Usage

1. **Open the Jupyter Notebook**:
   ```bash
   jupyter notebook fadml_proj.ipynb
   ```

2. **Run cells sequentially** to execute the complete analysis pipeline.

3. **Key Outputs**:
   - Model performance metrics for each algorithm
   - Confusion matrices visualizing prediction results
   - Detected suspicious transactions from graph analysis

## Results

### Model Performance (on test set):
- **Decision Tree**: Accuracy ~92%, F1-Score ~0.57
- **Random Forest**: Improved Recall from 0.51 to 0.62
- **SVM**: Robust performance on imbalanced data

### Graph-based Detection:
- Identifies transaction patterns suspicious for fraud
- Uses network analysis to find connected fraudulent activities

## Project Structure

```
Fraud-Detection-Classification-Model/
├── README.md                    # Project documentation
├── requirements.txt             # Python dependencies
├── fadml_proj.ipynb             # Main analysis notebook
└── fadml_dummy.csv              # Transaction dataset (not included)
```

## Key Techniques

### SMOTE Oversampling
Addresses class imbalance by generating synthetic examples of the minority class, improving model performance on rare fraud cases.

### Confusion Matrix Analysis
Provides detailed breakdown of:
- True Positives (correct fraud detection)
- True Negatives (correct legitimate detection)
- False Positives (false alarms)
- False Negatives (missed fraud)

### Graph-based Detection
Complements ML models by analyzing transaction networks to identify suspicious patterns that traditional models might miss.

## Business Impact

- **Fraud Prevention**: Early detection of suspicious transactions
- **Risk Management**: Improved identification of fraudulent patterns
- **Operational Efficiency**: Automated fraud detection reduces manual review
- **Customer Protection**: Minimizes financial losses from fraud

## Customization

- **Feature Selection**: Modify the `features` list for different variables
- **SMOTE Parameters**: Adjust `random_state` or sampling strategy
- **Model Hyperparameters**: Tune individual model parameters
- **Graph Thresholds**: Adjust amount and balance ratio thresholds in BFS
- **Train/Test Split**: Change `test_size` for different evaluation ratios

## Troubleshooting

- **Memory Issues**: Reduce dataset size or use sampling
- **Long Training Time**: Use simpler models or reduce SMOTE samples
- **Import Errors**: Ensure all packages are installed correctly
- **Graph Performance**: Limit BFS depth or number of runs for large datasets

## Future Enhancements

- Add more advanced models (XGBoost, Neural Networks)
- Implement real-time fraud detection
- Include feature engineering (time-based patterns, account behavior)
- Deploy as web service for production use
