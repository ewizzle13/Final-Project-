# Intrusion Detection System (IDS) - Machine Learning Final Project

## Overview

This project focuses on building a machine learning-based intrusion detection system using the **CIC-IDS2017 dataset (Wednesday traffic)**. The goal is to classify network traffic as either **benign** or **attack (DoS)**.

The dataset contains network flow features extracted from packet captures, which are used as input for machine learning models to detect malicious activity.

---

## Data Description

The dataset includes multiple files provided in different formats:

* CSV
* JSON
* Parquet

All formats contain the same data. For this project, a single format is selected to avoid redundancy and duplication.

The dataset includes the following classes:

* BENIGN
* DoS Hulk
* DoS GoldenEye
* DoS slowhttptest
* DoS slowloris
* Heartbleed

---

## Data Processing & Cleaning

### 1. Data Loading

* Combined multiple files into a single dataset using `pandas`

### 2. Data Cleaning

* Standardized column names (removed extra whitespace)
* Removed duplicate rows
* Removed irrelevant class:

  * **Heartbleed** (not a DoS attack)
* Handled missing values by replacing with **median values from the training data**

### 3. Feature Preparation

* Separated features (`X`) and target label (`y`)
* Target column: `Label`
* Converted labels into binary classification:

  * `BENIGN` → `benign`
  * All DoS attacks → `attack`

### 4. Outlier Handling

* Applied **IQR-based outlier detection** on numeric features
* Replaced extreme values with the **median (training data only)** to reduce noise and prevent data leakage

---

## Machine Learning Approach

### Objective

Build a classifier to distinguish:

* Normal traffic (benign)
* Malicious traffic (DoS attacks)

### Steps

* Train-test split of dataset (80/20 with stratification)
* Outlier handling applied **only to training data**
* Missing value imputation using **training median**
* Feature scaling using `StandardScaler`
* Model training using multiple algorithms:

  * Logistic Regression - Leilani Rivera
  * Perceptron (baseline linear model) - Niurika Gonzalez
  * Random Forest - Eniya Madden

---

## Evaluation Metrics

Models are evaluated using:

* Accuracy
* Precision
* Recall
* F1-score
* Confusion Matrix

---

## Results

| Model               | Accuracy | Precision | Recall | F1 Score |
| ------------------- | -------- | --------- | ------ | -------- |
| Random Forest       | **0.99** | 0.99      | 0.999  | 0.99     |
| Logistic Regression | 0.84     | 0.90      | 0.92   | 0.91     |
| Perceptron          | TBD      | TBD       | TBD    | TBD      |

### Key Observations

* **Random Forest achieved the highest performance (~99% accuracy)** due to its ability to capture complex, non-linear relationships in network traffic data.
* **Logistic Regression (~84% accuracy)** performed well but is limited by its assumption of linear separability.
* **Perceptron (accuracy)** 
* The difference in performance highlights the importance of model selection for cybersecurity datasets.
* Recall is especially important in this task, as missing an attack (false negative) can be critical.

---

## Project Structure

```plaintext
Final-Project-/
│
├── data/
│   └── final_project_data_sp2026_L/
│
├── notebooks/
│   ├── random_forest.ipynb
│   ├── logistic_regression.ipynb
│   └── perceptron.ipynb
│
├── results/
│   ├── plots/
│   └── metrics/
│
├── README.md
```

---

## Key Takeaways

* Consistent preprocessing across models is critical for fair comparison
* Applying transformations only to training data prevents data leakage
* Tree-based models perform best on complex intrusion detection data
* Linear models provide useful baselines but may struggle with non-linear patterns

---

## Notes

* The project focuses specifically on **Wednesday traffic (DoS attacks)**
* Only one data format is used to avoid duplication
* Emphasis was placed on maintaining a **clean and consistent ML pipeline**

---

## Team Members

* E'niya Madden
* Leilani Rivera
* Niurika Gonzalez
