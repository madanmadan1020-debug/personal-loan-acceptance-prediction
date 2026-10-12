# Personal Loan Acceptance Prediction

A Machine Learning project that predicts whether a bank customer is likely to accept a personal loan offer based on customer demographics, income, and banking information.

## Project Overview

Banks often spend significant time and money promoting personal loans to customers who may not be interested. This project uses machine learning to identify customers who are more likely to accept a personal loan offer, helping banks make their marketing campaigns more targeted.

The project compares multiple machine learning algorithms, improves model performance through preprocessing and hyperparameter tuning, and provides an interactive web application using Streamlit.

**Best-performing model:** XGBoost, based on the reported cross-validation F1-score comparison.

## Key Features

- Customer data preprocessing and exploratory data analysis (EDA)
- Comparison of multiple machine learning algorithms
- Handling class imbalance using class weighting and SMOTE
- Feature scaling and hyperparameter tuning
- Model evaluation using classification metrics
- Feature importance analysis
- Interactive predictions through a Streamlit web application
- Input validation for customer age and professional experience

## Technologies Used

- **Programming Language:** Python
- **Data Processing:** Pandas, NumPy
- **Machine Learning:** Scikit-learn, XGBoost, Imbalanced-learn
- **Data Visualization:** Matplotlib, Seaborn
- **Web Application:** Streamlit
- **Model Persistence:** Joblib
- **Development Environment:** Jupyter Notebook, VS Code

## Dataset

The project uses the Bank Personal Loan Modeling dataset.

- Total records: 5,000 customers
- Original columns: 14
- Target variable: `Personal Loan`
- Target value `1`: Customer accepted the loan offer
- Target value `0`: Customer did not accept the loan offer

### Download the Dataset

Download the dataset from Kaggle:

https://www.kaggle.com/datasets/teertha/personal-loan-modeling

Place the CSV file in the following location:

`data/Bank_Personal_Loan_Modelling.csv`

The dataset is not included in this repository. Ensure that the filename and location match the project's expected path.

## Machine Learning Workflow

1. **Data Loading:** Load the customer dataset using Pandas.
2. **Data Preprocessing:** Remove unnecessary columns and correct negative professional experience values.
3. **Feature and Target Separation:** Separate customer attributes (`X`) from the target variable (`y`).
4. **Train-Test Split:** Split the dataset into 80% training data and 20% testing data using stratification.
5. **Feature Scaling:** Apply StandardScaler in the improved model pipelines.
6. **Class Imbalance Handling:** Use class weighting and SMOTE for selected models.
7. **Model Training:** Train and compare multiple machine learning algorithms.
8. **Hyperparameter Tuning:** Optimize selected models using stratified cross-validation.
9. **Model Evaluation:** Compare precision, recall, F1-score, accuracy, and ROC-AUC.
10. **Model Saving:** Save the selected model for reuse.
11. **Prediction:** Use the trained model through the Streamlit web interface.

## Machine Learning Algorithms

### Baseline Experiment

- Perceptron
- Logistic Regression
- K-Nearest Neighbors (KNN)
- Linear Support Vector Machine (SVM)
- K-Means
- Multi-Layer Perceptron (MLP)

### Improved Experiment

- Perceptron
- Logistic Regression
- KNN with SMOTE
- Support Vector Machine (SVM)
- MLP with SMOTE
- Random Forest
- XGBoost

The experiments compare different approaches to classification. K-Means is an unsupervised clustering algorithm and is included in the baseline experiment for comparison.

## Model Performance

The following are the reported test-set results for selected models.

| Model | Accuracy | Precision | Recall | F1-Score |
|---|---:|---:|---:|---:|
| SVM | 96.9% | 78.8% | 92.7% | 85.2% |
| MLP + SMOTE | 97.5% | 83.8% | 91.7% | 87.6% |
| Random Forest | 98.7% | 90.3% | 96.9% | 93.5% |
| XGBoost | 98.9% | 91.3% | 97.9% | 94.5% |

*Note: These values are the previously reported results from the project. They are not guarantees of performance on new data.*

### Why XGBoost?

XGBoost uses gradient-boosted decision trees to learn complex relationships between customer attributes. In the reported experiments, it achieved the highest cross-validation F1-score among the compared models and was selected as the best model.

## Important Features

The project identifies the following features as important predictive factors:

- Income
- Family size
- Education
- Average credit-card spending
- CD account status

These are predictive relationships in the dataset and do not necessarily imply causation.

## Project Structure

```text
personal-loan-acceptance-prediction/
│
├── app/
│   └── app.py
│
├── data/
│   └── .gitkeep
│
├── models/
│   └── best_model.pkl
│
├── notebooks/
│   └── loan_prediction.ipynb
│
├── results/
│
├── src/
│   ├── preprocess.py
│   ├── train.py
│   └── evaluate.py
│
├── requirements.txt
├── README.md
└── .gitignore
```

The model and results files are generated during execution and may not be present in a fresh clone.

## Installation and Setup

### 1. Clone the repository

```bash
git clone https://github.com/madanmadan1020-debug/personal-loan-acceptance-prediction.git
cd personal-loan-acceptance-prediction
```

### 2. Create a virtual environment

**Windows:**

```powershell
python -m venv .venv
.\.venv\Scripts\Activate.ps1
```

### 3. Install dependencies

```bash
python -m pip install --upgrade pip
pip install -r requirements.txt
```

### 4. Download and place the dataset

Download the dataset from Kaggle and place `Bank_Personal_Loan_Modelling.csv` inside the `data/` directory.

### 5. Train the machine learning models

```bash
python src/train.py
```

The training script preprocesses the data, trains and evaluates models, compares their performance, and saves the selected model to:

`models/best_model.pkl`

### 6. Launch the web application

After training completes successfully, run:

```bash
streamlit run app/app.py
```

Open the local URL displayed in your terminal, usually:

http://localhost:8501

Enter customer information and use the application to obtain a predicted loan acceptance class and estimated probability.

## Evaluation Metrics

- **Accuracy:** Proportion of correct predictions.
- **Precision:** Proportion of predicted acceptances that were actual acceptances.
- **Recall:** Proportion of actual acceptances correctly identified.
- **F1-score:** Harmonic mean of precision and recall.
- **ROC-AUC:** Measures the model's ability to distinguish between the two classes across classification thresholds.

Because the dataset is imbalanced, accuracy alone is not sufficient to assess the model.

## Limitations

- Predictions depend on the quality and representativeness of the historical dataset.
- Estimated probabilities are not guarantees of customer behaviour.
- Model performance may change when applied to customers from different populations or time periods.
- The model predicts acceptance of a loan offer; it does not determine loan eligibility or credit approval.
- The project is intended for learning and demonstration, not as a standalone system for making real financial decisions.

## Future Enhancements

- Add additional model comparison visualizations.
- Improve probability calibration and decision-threshold selection.
- Add model monitoring and data-drift detection.
- Improve the user interface and prediction reports.
- Evaluate fairness and performance across customer groups.

## Contributors

- **Madan P** — [GitHub](https://github.com/madanmadan1020-debug)
- **Mathin M** — Project collaborator

## Disclaimer

This project is developed for educational and demonstration purposes. Predictions should not be used as the sole basis for lending, credit approval, or other consequential financial decisions.

## License

Add an appropriate open-source license if you intend to distribute or reuse this project publicly.
