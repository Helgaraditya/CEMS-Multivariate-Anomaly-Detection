# Multivariate CEMS Anomaly Detection in the Cement Industry

## Project Overview

This project focuses on detecting multivariate anomalies in Continuous Emission Monitoring System (CEMS) data from the Raw Mill unit of PT Semen Indonesia. The project applies two unsupervised anomaly detection methods, Isolation Forest (IF) and Local Outlier Factor (LOF), to identify unusual patterns in emission and operational variables.

The CEMS dataset contains hourly observations collected over one year, consisting of six variables related to emission and operating conditions. Since the dataset is unlabeled, anomaly detection was performed using an unsupervised learning approach without predefined anomaly labels.

The project covers the complete data science workflow, including data preprocessing, exploratory data analysis, feature engineering, sliding-window transformation, model development, hyperparameter selection, anomaly detection, model comparison, and anomaly severity analysis.

---

## Objectives

The main objectives of this project are:

- Detect anomalous patterns in multivariate CEMS data.
- Apply and compare Isolation Forest and Local Outlier Factor.
- Investigate the sensitivity of model parameters, particularly the contamination level.
- Select stable model configurations using stability analysis.
- Analyze the overlap and differences between IF and LOF anomaly detections.
- Identify variables that contribute strongly to detected anomalous patterns.
- Analyze the daily severity of detected anomalies to provide a more operational interpretation.

---

## Dataset

The dataset was collected from the Continuous Emission Monitoring System (CEMS) of the Raw Mill unit.

### Dataset Characteristics

| Attribute | Description |
|---|---|
| Data Source | CEMS – Raw Mill |
| Observation Period | January–December 2025 |
| Frequency | Hourly |
| Initial Observations | 8,760 |
| Variables | 6 |
| Data Type | Multivariate Time Series |
| Learning Approach | Unsupervised Learning |
| Ground-Truth Labels | Not Available |

### Variables

The six variables used for anomaly detection are:

- Particulate (mg/Nm³)
- SO₂ (mg/Nm³)
- NOₓ (mg/Nm³)
- CO (mg/Nm³)
- O₂ (%)
- Flowrate (m/s)

These variables represent a combination of emission and operational characteristics of the cement production process.

---

## Project Workflow

```text
Raw CEMS Data
      │
      ▼
Data Integration & Cleaning
      │
      ▼
Exploratory Data Analysis
      │
      ▼
Data Standardization
      │
      ▼
24-Hour Sliding Window
      │
      ▼
Feature Transformation
      │
      ├───────────────┐
      ▼               ▼
Isolation Forest   Local Outlier Factor
      │               │
      └───────┬───────┘
              ▼
   Hyperparameter Selection
              │
              ▼
      Stability Analysis
              │
              ▼
      Final IF & LOF Models
              │
              ▼
       Anomaly Detection
              │
              ├───────────────┐
              ▼               ▼
      Overlap Analysis   Severity Analysis
              │               │
              └───────┬───────┘
                      ▼
             Operational Insights


# 1. Data Preprocessing

The raw CEMS data consisted of multiple monthly files containing hourly emission and operational measurements. These files were integrated into a single chronological dataset to establish a consistent time-series structure.

The preprocessing stage included:

- Integrating monthly CEMS data files.
- Standardizing date and time formats.
- Creating a unified `DATETIME` index.
- Removing non-operational and shutdown periods.
- Identifying and handling invalid zero values.
- Handling missing observations.
- Applying time-based interpolation where appropriate.
- Preparing the cleaned multivariate dataset for modeling.

The resulting dataset was structured as an hourly multivariate time series and used as the foundation for the subsequent exploratory analysis, feature engineering, and anomaly detection stages.
