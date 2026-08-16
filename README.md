# Predictive Risk Modeling for Global Freight Delays

### Using Multi-Modal Operational Streams — Classification Approach

## Project Overview

This project develops a predictive risk-classification framework for identifying freight-delay risk across supply chains using multi-modal operational data.

The project uses freight and supply-chain indicators covering port activity, containership capacity, rail performance, trucking performance, freight rates, fuel prices, employment and other operational measures.

The main focus is **binary classification**:

- **High-risk (1):** next-week freight risk is above the 75th-percentile threshold
- **Low-risk (0):** next-week freight risk is at or below the threshold

The project compares classical machine-learning and advanced deep-learning approaches and provides model evaluation, anomaly detection, explainability and a freight-risk scoring framework.

## Aim

To build a predictive classification framework that identifies, measures and predicts short-term freight-delay risk using multi-modal operational data.

## Research Question

> Can multi-modal port and freight operational data be used to accurately classify short-term freight-delay risk as high-risk versus low-risk, and which classification approach performs best?

## Research Objectives

1. Evaluate freight and supply-chain indicators from 2019 onwards to identify delay signals and anomalies.
2. Build predictive classification models for high-risk and low-risk freight disruption.
3. Compare classical machine-learning and deep-learning classifiers across different operational periods, including pre-COVID, COVID and post-COVID regimes.
4. Produce an interpretable 0–100 freight-risk score for logistics decision-making.

## Dataset

**Dataset:** Supply Chain and Freight Indicators — U.S. Department of Transportation / MARAD.

The notebook loads:

`Supply_Chain_and_Freight_Indicators.csv`

The dataset contains 26,135 raw observations and 12 columns before cleaning. The main fields include:

- `ID`
- `DATE`
- `YEAR`
- `INDICATOR`
- `MEASURE1`
- `MEASURE2`
- `MEASURE1_DESCRIPTION`
- `MEASURE2_DESCRIPTION`
- `VALUE1`
- `UNITS`
- `NOTE`
- `SOURCE`

The dataset contains 44 different indicators covering areas such as:

- Containership capacity and port activity
- Containers at U.S. ports
- Port congestion and vessel waiting
- Rail performance
- Truck speeds and trucking rates
- Freight transportation activity
- Diesel and fuel prices
- Freight rates
- Transportation and warehousing employment
- Supply-chain and economic indicators

## Data Source

The dataset is from the U.S. Department of Transportation / Maritime Administration (MARAD).

Data source:

https://catalog.data.gov/dataset/supply-chain-and-freight-indicators

## Data Preprocessing

The project performs several preprocessing steps before modelling:

1. Creates a working copy of the raw dataset.
2. Converts `VALUE1` from text into numeric values.
3. Removes commas and non-numeric characters from numeric values.
4. Converts `DATE` into a datetime format.
5. Converts `YEAR` into a numeric value.
6. Handles columns that contain no useful values.
7. Removes records with missing `DATE` or `VALUE1`.
8. Sorts the cleaned data chronologically.

The notebook reports a cleaned dataset of 25,632 observations, covering dates from January 2017 to August 2026 in the executed analysis.

## Methodology

The project follows an end-to-end machine-learning workflow.

### 1. Exploratory Data Analysis

The notebook investigates freight and supply-chain patterns using multiple dashboards and visualisations.

The analysis examines:

- Freight trends over time
- Port congestion
- Container activity
- Rail performance
- Trucking activity
- Freight rates
- Fuel prices
- Economic indicators
- Operational disruptions
- COVID-period effects

### 2. Composite Freight Risk / Congestion Index

Multiple operational indicators are combined to create a composite freight-risk/congestion measure.

This provides a common framework for measuring overall disruption across different freight and supply-chain signals.

### 3. Feature Engineering

Features are created from the operational time-series data to provide predictive information for the classification models.

The target is based on the future freight-risk level, with the 75th percentile used to distinguish high-risk from low-risk conditions.

### 4. Anomaly Detection

Two approaches are used to identify unusual freight and supply-chain conditions:

- **Isolation Forest**
- **CUSUM**

These methods help identify periods where operational behaviour differs significantly from normal patterns.

### 5. Chronological Train/Test Split

Because the data is time-dependent, the modelling workflow uses chronological ordering rather than randomly mixing future and past observations.

This helps reduce the risk of using future information when predicting earlier periods.

## Machine Learning Models

### Baseline Models

The project includes:

- Logistic Regression
- Random Forest Classifier

These provide baseline classification performance and are useful for comparison with more advanced approaches.

### Advanced Models

The project also evaluates:

- LSTM
- Transformer
- XGBoost

The advanced models are designed to capture more complex relationships and temporal patterns in freight operational data.

## Explainable AI

**SHAP (SHapley Additive exPlanations)** is used with the modelling workflow to investigate feature importance and model explanations.

This helps identify which operational indicators contribute most to freight-delay risk predictions and makes the classification framework more interpretable.

## Model Evaluation

The classification models are evaluated using classification-focused metrics, including:

- ROC-AUC
- F1-score
- Confusion Matrix
- Classification Report
- ROC Curve

The models are compared to determine which classification approach provides the most effective prediction of high-risk freight conditions.

> Note: Model scores should be taken directly from the latest executed notebook results rather than hard-coded in this README.

## Freight Risk Score

The project produces an interpretable **0–100 freight-risk score** intended to communicate the level of disruption more clearly to logistics and supply-chain decision-makers.

The classification framework focuses on identifying whether the following week's freight risk is likely to be high or low.

