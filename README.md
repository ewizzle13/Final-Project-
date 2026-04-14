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
* Removed irrelevant or incorrect class:

  * **Heartbleed** (not a DoS attack)
* Handled missing or inconsistent values 

### 3. Feature Preparation

* Separated features (`X`) and target label (`y`)
* Target column: `Label`
* Converted labels into binary classification:

  * `BENIGN` → `benign`
  * All DoS attacks → `attack`

---

##  Machine Learning Approach

### Objective

Build a classifier to distinguish:

* Normal traffic (benign)
* Malicious traffic (DoS attacks)

### Steps

* Train-test split of dataset
* Feature scaling (StanderScale)
* Model training using multiple algorithms:

  * Logistic Regression
  * Decision Tree
  * Random Forest - Eniya Madden

### Evaluation Metrics

Models are evaluated using:

* Accuracy
* Precision
* Recall
* F1-score
* Confusion Matrix

---

## Results

The performance of each model is compared to determine the most effective classifier for intrusion detection.

Special emphasis is placed on:

* **Recall** (detecting attacks)
* **Precision** (reducing false positives)

---

## Project Structure

```
.
├── finalproject.ipynb        # Main notebook (data processing + modeling)
├── README.md                # Project documentation
├── final_project_data_sp2026_L/
│   ├── ids_*.csv/Json/parquet  # Dataset files
```

---

## Key Takeaways

* Data preprocessing is critical for cybersecurity datasets
* Binary classification simplifies intrusion detection tasks
* Model selection impacts detection accuracy and reliability
* Avoiding data duplication ensures valid model performance

---

## Notes

* Only one data format Parquet is used to increase runtime complexity
* The project focuses specifically on **Wednesday traffic (DoS attacks)**

---

## Team Members

* E'niya Madden
* Leilani Rivera
* Niurika Gonzalez

---
