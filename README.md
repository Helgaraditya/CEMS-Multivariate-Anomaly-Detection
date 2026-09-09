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

![Project Workflow](images/Research_Flowchart.jpg)

The following sections describe each stage of the workflow, from data preprocessing to the final anomaly analysis and key findings.

---

## 1. Data Preprocessing

The preprocessing stage was performed to prepare the CEMS data for subsequent analysis and modeling.

The preprocessing workflow included:

- Integrating monthly CEMS datasets into a unified dataset.
- Cleaning and validating the collected observations.
- Removing invalid or non-operational observations.
- Handling missing values.
- Replacing invalid zero values with missing values where appropriate.
- Performing time-based interpolation for selected variables.
- Standardizing timestamp formats.
- Preparing the final dataset for exploratory analysis and modeling.

The preprocessing process was implemented using Python and related data-processing libraries.

---

## 2. Exploratory Data Analysis

Exploratory Data Analysis (EDA) was performed to understand the characteristics and relationships within the CEMS data before applying anomaly detection models.

The analysis included:

- Descriptive statistics.
- Distribution analysis.
- Histograms.
- Boxplots.
- Time-series visualization.
- Correlation analysis.
- Correlation heatmaps.
- Identification of potential relationships between emission and operational variables.

The EDA stage was used to understand the normal behavior, distribution, and variability of the monitored variables.

---

## 3. Feature Engineering

### Data Standardization

The six CEMS variables were standardized before applying the sliding-window transformation so that differences in measurement scales would not dominate the anomaly detection process.

### 24-Hour Sliding Window

A 24-hour sliding window was used to capture temporal patterns across one day.

For each modeling observation, 24 consecutive hourly observations were combined into a single window.

The initial dataset contained **8,760 hourly observations**. With a window size of 24, the transformation generated:

- **8,737 sliding windows**
- **144 features per window**

The feature structure can be summarized as:

```text
24 hours × 6 variables = 144 features
