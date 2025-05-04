# Mortality Analysis with PySpark and Machine Learning

This project performs exploratory data analysis (EDA) and builds predictive models on U.S. mortality data from the years 2013–2015 using Apache Spark. It explores mortality patterns and leverages machine learning techniques to predict age at death based on various features.

## Project Structure

- `data/`: Contains all the raw and structured datasets.
  - `2015_data.parquet`: Mortality data for the year 2015.
  - `2014_data.parquet`: Mortality data for the year 2014.
  - `2013_data.parquet`: Mortality data for the year 2013.
  - `2015_codes.json`: JSON file with code mappings for the year 2015.
  
- `notebooks/`: Jupyter notebooks containing the data exploration and analysis workflows.
  - `mortality_analysis_spark.ipynb`: Jupyter notebook that contains Spark-based analysis of mortality data, including data loading, transformation, and machine learning model building.

- `references/`: Documentation and other references for the project.
  - `2023-Mortality-Public-Use-File-Documentation.pdf`: PDF file containing detailed information and definitions related to the mortality dataset.

## Dataset Description

The project uses three years of U.S. mortality public-use data files (`2013_data.parquet`, `2014_data.parquet`, `2015_data.parquet`). Cause-of-death codes are mapped using `2015_codes.json`. Data includes features such as:

- Age at death (`detail_age`)
- Sex
- Cause of death (coded and decoded), and more

For details, see the included [2023-Mortality-Public-Use-File-Documentation.pdf](./references/2023-Mortality-Public-Use-File-Documentation.pdf).

## Features

### 1. Data Loading & Cleaning
- Spark is used to load and union multiple years of data.
- JSON file is used to decode cause-of-death codes (`358_cause_recode`).
- Missing data is identified and either dropped or filled appropriately.

### 2. Exploratory Data Analysis (EDA)
- Most common ages of death
- Age distribution by sex
- Top 20 causes of death overall and by sex
- Visualizations using `matplotlib`

### 3. Data Preprocessing
- One-hot encoding for categorical features like `sex`
- Removal of string and irrelevant columns
- Feature scaling using `StandardScaler`

### 4. Machine Learning Models
Two regression models are trained to predict `detail_age` (age at death):
- **Linear Regression**
- **Random Forest Regressor**

Evaluation metrics:
- Root Mean Squared Error (RMSE)
- Mean Absolute Error (MAE)
- R² Score

Performance is compared both **with** and **without** the inclusion of recoded age fields.

### 5. Model Evaluation
- Numerical metrics to assess performance
- Scatter plots: Actual vs. Predicted for both models
