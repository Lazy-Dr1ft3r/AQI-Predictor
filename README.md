# Delhi Air Quality Index Prediction
## Introduction
This project develops a comprehensive machine learning pipeline for predicting Air Quality Index (AQI) in Delhi, India. The system makes use of historical environmental monitoring data from multiple government sources to forecast air quality conditions, supporting public health advisories and urban planning decisions.

### Motivation

### Objectives

## Dataset

### Sources
### Format

## Methodology

## ML Pipeline Flowdiagram

```mermaid
flowchart LR
    A[**Data Preprocessing**Cleaning, handling missing values, and standardizing formats] 
    B[**Feature Engineering**Lag features, rolling statistics, trend indicators, temporal patterns]
    C[**Model Training & Validation**Building and evaluating models with proper train-test splits]
    D[**Data Leakage Detection**Identifying information leakage causing unrealistic results]
    
    A --> B --> C --> D
```



