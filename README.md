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

