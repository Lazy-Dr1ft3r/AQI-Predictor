# 😷 Delhi Air Quality Index Prediction
## 📖 Introduction

This project develops a comprehensive machine learning pipeline for predicting Air Quality Index (AQI) in Delhi, India. The system makes use of historical environmental monitoring data from multiple government sources to forecast air quality conditions, supporting public health advisories and urban planning decisions.

### Motivation

The idea to do this project was birthed during a time when Delhi was g

###  Objectives

- Build an end-to-end ML pipeline from raw data to deployment-ready model.
- Process and integrate data from multiple heterogeneous monitoring sources.
- Chart out meaningful features capturing patterns and environmental trends.
- Develop a robust prediction model with realistic  performance.

## 🗂️ Dataset

The data was gathered from the Central Pollution Copntrol Board repository ([Link](https://airquality.cpcb.gov.in/ccr/#/caaqm-dashboard-all/caaqm-landing/aqi-repository)). 6 years worth of data was downloaded (2018-2024). The readings within this repo were measured and provided by multiple government institutes, they were:

| Source | Description | 
|-------|----------------------|
| DPCC |Delhi Pollution Control Committee monitoring data |
| CPCBB | Central Pollution Control Board national monitoring network | 
| IMD | India Meteorological Department weather data |
| IITM |Indian Institute of Tropical Meteorology research data|

The dataset consists of daily AQI measurements from 2018-2024 for 37 monitoring stations, all within Delhi. These stations are:

<img width="687" height="564" alt="image" src="https://github.com/user-attachments/assets/47b0aece-7fb4-4979-a387-56938f45d1a7" />

### Dataset issues

- <ins>**Missing/NULL Values:**</ins> The raw data had empty cells scattered throughout, requiring systematic handling to avoid dropping too many records or introducing bias.
- <ins>**Multi-Source Data Integration:**</ins> Data came from different sources (DPCC, CPCB, IMD, IITM) with varying formats, requiring standardization into a unified structure.
- <ins>**Wide-to-Long Format Transformation:**</ins> The raw data was in wide format (months as columns, days as rows) and needed transformation to long format (one row per date-station combination) for ML modeling.

## ⚙️ Methodology

### ML Pipeline Flowdiagram

```mermaid
flowchart LR
    A[**Data Preprocessing**] 
    B[**Feature Engineering**]
    C[**Model Training & Validation**]
    D[**Data Leakage Detection**]
    
    A --> B --> C --> D
```

### Data Preprocessing

Raw data underwent extensive cleaning and standardization including handling missing values through interpolation, normalizing column names across sources, removing duplicate records, and converting timestamps to consistent formats. The preprocessing pipeline was designed to adapt to format variations across different data sources and time periods.

### Feature Engineering

A comprehensive feature set was developed to capture the complexity of environmental data:

- <ins>**Lag Features:**</ins> Previous hour, day, and week AQI values to capture short and medium-term patterns

- <ins>**Rolling Statistics:**</ins> Moving averages, standard deviations, and min/max over 6, 12, 24, and 72-hour windows

- <ins>**Temporal Features:**</ins> Hour of day, day of week, month, season, and holiday indicators

### Training

Regression models like Linear Regression (baseline), Ridge and Lasso Regression, Decision Tree, and Random Forest were evaluated with strict temporal ordering to prevent data leakage. Out of which, the Random Forest Classifier emerged as the bbest perfomer.

### Testing

Time series cross-validation was conducted. The train-test split of the data maintained a chronological integrity, ensuring the model was only evaluated on future data it had not seen during training.


## 📊 Results

| Model | Overall Bias (Mean) | 
|-------|----------------------|
| R<sup>2</sup> Score | 0.80 |
| Improvement over baseline | 17% | 
| Variance Explained | 80% |
