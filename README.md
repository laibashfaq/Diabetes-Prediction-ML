# Diabetes Prediction Using Machine Learning 🩺

An end-to-end Machine Learning project focused on diabetes prediction through exploratory data analysis, data cleaning, feature engineering, data visualization, and classification model evaluation.

## 📌 Project Overview

This project explores the relationship between patient health measurements and diabetes outcomes. It demonstrates a complete machine learning workflow, with particular attention to data quality, duplicate records, missing values, and reliable model evaluation.

The target variable is `Outcome`:

- `0` — No diabetes
- `1` — Diabetes

A key focus of this project is understanding how duplicate records can cause data leakage and artificially inflate model performance when the same records appear in both training and testing datasets.

## 🎯 Objectives

- Explore and understand the diabetes dataset.
- Identify missing values and physiologically implausible zero values.
- Detect duplicate records and investigate their effect on model evaluation.
- Perform exploratory data analysis and visualize feature relationships.
- Engineer meaningful features from existing health measurements.
- Train and compare multiple classification algorithms.
- Evaluate model performance using cross-validation and test-set metrics.
- Examine feature importance, probability calibration, and classification thresholds.

## 📂 Project Structure

```text
diabetes-prediction-ml/
│
├── README.md
├── Diabetes_Analysis.ipynb
├── Diabetes.csv
└── requirements.txt
```

## 🛠️ Technologies Used

- **Python** — programming language
- **Pandas** — data manipulation and analysis
- **NumPy** — numerical computing
- **Matplotlib** — data visualization
- **Seaborn** — statistical visualization
- **Scikit-learn** — preprocessing, classification, cross-validation, hyperparameter tuning, and evaluation
- **Jupyter Notebook / Google Colab** — development environment

## 🔄 Project Workflow

### 1. Data Loading and Exploration

- Load the diabetes dataset.
- Inspect its structure, data types, and descriptive statistics.
- Examine the target distribution and check for missing values.
- Identify data-quality issues that may affect model performance.

### 2. Data Quality Analysis

The notebook investigates two important issues:

- **Zero values representing missing measurements:** Zero values in Glucose, BloodPressure, SkinThickness, Insulin, and BMI are treated as missing where appropriate.
- **Duplicate records:** Duplicate measurements are identified while ignoring the `Id` column.

A Random Forest experiment demonstrates how leaving duplicate records in the dataset can cause information leakage between training and testing sets.

### 3. Exploratory Data Analysis (EDA)

The project explores:

- Diabetes outcome distribution.
- Missing-value patterns and duplicate records.
- Feature distributions by outcome.
- Relationships between glucose, BMI, age, insulin, and pregnancies.
- Correlations between health measurements and the target variable.
- Diabetes rates across age, BMI, and glucose groups.

Visualizations include histograms, boxplots, violin plots, correlation heatmaps, scatterplots, and pairwise feature comparisons.

### 4. Data Preprocessing

The preprocessing workflow includes:

- Replacing selected impossible zero values with missing values.
- Removing duplicate records.
- Removing the identifier column.
- Splitting the data into training and testing sets using stratification.
- Imputing missing measurements using medians calculated from the training data.

This approach helps reduce information leakage during preprocessing.

### 5. Feature Engineering

Additional features are created to capture potentially useful relationships between health measurements:

- `Glucose_BMI` — interaction between glucose and BMI.
- `Insulin_log` — logarithmic transformation of insulin.
- `Glucose_Insulin` — ratio of glucose to insulin.
- `Age_Glucose` — interaction between age and glucose.
- `Pregnancy_Rate` — pregnancies relative to age.
- `Prediabetic_Glu` and `Diabetic_Glu` — glucose threshold indicators.
- `Obese` and `High_BP` — BMI and blood-pressure indicators.
- `Insulin_missing` and `Skin_missing` — missingness indicators.
- Age-group indicators.

These features are explored for their potential contribution to prediction performance.

### 6. Model Training

The following classification algorithms are evaluated:

- Logistic Regression
- K-Nearest Neighbors (KNN)
- Support Vector Machine (SVM)
- Random Forest
- Gradient Boosting

Repeated stratified cross-validation is used for baseline model comparison. Grid search is applied to tune Logistic Regression, Random Forest, and Gradient Boosting models.

### 7. Model Evaluation

Model performance is assessed using:

- Accuracy
- Precision
- Recall
- F1-score
- ROC-AUC
- Precision-Recall AUC
- Classification report
- Confusion matrix
- ROC and Precision-Recall curves

The notebook also investigates Random Forest feature importance, Logistic Regression coefficients, probability calibration, and the trade-off between classification thresholds and recall.

## 🔍 Key Findings

The notebook's conclusions highlight the following observations:

- **Data quality matters:** Approximately 72% of the original rows are identified as exact duplicates when the `Id` column is ignored.
- **Duplicates can inflate performance:** Keeping duplicate records can allow the same measurements to appear in both training and testing data.
- **Glucose is the dominant predictor** in the notebook's feature-importance analysis, followed by BMI, age, and engineered interaction features.
- **More realistic evaluation:** After cleaning, the notebook reports approximately 71–73% test accuracy and ROC-AUC values around 0.82–0.83 across the evaluated models.
- **Recall requires attention:** The notebook notes lower recall for the diabetic class and explores how changing the decision threshold can increase detection at the cost of additional false positives.

These findings describe the results reported by the notebook. Actual metrics may vary with the dataset, preprocessing decisions, and experimental setup.

## 🚀 Getting Started

### Prerequisites

Install Python and the required libraries.

### Installation

1. Clone the repository:

   ```bash
   git clone https://github.com/YOUR-USERNAME/Diabetes Prediction-ML.git
   ```

2. Navigate to the project directory:

   ```bash
   cd Diabetes Prediction-ML
   ```

3. Install the dependencies:

   ```bash
   pip install -r requirements.txt
   ```

4. Launch Jupyter Notebook:

   ```bash
   jupyter notebook Diabetes Analysis.ipynb
   ```

5. Run the notebook cells sequentially.

**Dataset requirement:** Place `Diabetes.csv` in the project directory. The CSV must contain the columns expected by the notebook, including `Id` and `Outcome`. Update the data path if your file is stored elsewhere.

## 💡 Future Improvements

- Compare alternative imputation strategies.
- Use a scikit-learn pipeline to integrate preprocessing and feature engineering into cross-validation.
- Investigate patient-level duplicate handling and more robust validation strategies.
- Tune classification thresholds according to a clearly defined evaluation objective.
- Add explainability techniques such as SHAP.
- Build a simple demonstration interface for model predictions.

## 📚 Learning Outcomes

This project demonstrates practical experience in:

- Exploratory Data Analysis
- Data Cleaning and Quality Assessment
- Duplicate Detection and Data Leakage Awareness
- Feature Engineering
- Supervised Machine Learning
- Cross-Validation and Hyperparameter Tuning
- Classification Metrics and Model Comparison
- Feature Importance and Model Calibration

## ⚠️ Disclaimer

This project is for educational and portfolio purposes only. Its predictions are not medical diagnoses and should not be used to make clinical decisions.

## 👩‍💻 Author

**Laiba Ashfaq**

Computer Science Graduate | Interested in Artificial Intelligence, Machine Learning, and Data Analysis.

## 📄 License

No license has been specified. Add an appropriate license if you intend to distribute the project as open source, and verify that the dataset's terms permit redistribution.

