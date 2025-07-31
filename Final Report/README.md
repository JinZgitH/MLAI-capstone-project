# Airbnb Price Optimizer

## Initial Report and Exploratory Data Analysis

**Previous Report**: [Initial Report README.md](../README.md)

### Summary of Initial Analysis

The initial exploratory data analysis focused on understanding the Airbnb pricing dataset and establishing a baseline for the project:

**Dataset Overview**:
- **Source**: Kaggle Airbnb Price Dataset with ~74,000 listings
- **Scope**: Focused on NYC and LA markets for targeted analysis
- **Target Variable**: Log-transformed price for improved model performance

**Key Findings**:
- **City Distribution**: NYC (32,349 listings) and LA (22,453 listings) dominated the dataset
- **Feature Engineering**: Analyzed 119 distinct amenities, selected top 20 most predictive features
- **Data Quality**: Performed comprehensive cleaning (removed duplicates, null values, unnecessary columns)

**Baseline Model Performance**:
- **Algorithm**: Random Forest Regression
- **Metrics**: MAE: 0.29, RMSE: 0.40, R²: 0.67
- **Interpretation**: ~34% average relative error in raw price predictions

This initial analysis established the foundation for the final model development and optimization phase. 

