# Airbnb Price Optimizer



## Executive summary

Develop a machine learning model that predicts the nightly price of Airbnb listings in selected cities, with the goal of helping hosts maximize revenue while balancing occupancy rates.

## Rationale
In the competitive short-term rental market, pricing decisions have a direct impact on host revenue, occupancy rates, and guest satisfaction. Unlike traditional hotels, Airbnb listings vary widely in amenities, property types, and booking flexibility — making manual or static pricing strategies suboptimal.

This project addresses that gap by building a data-driven dynamic pricing model to assist Airbnb hosts in setting optimal nightly prices based on property attributes, amenities, location, and market demand patterns.

## Research Question
How can we accurately predict the nightly price of an Airbnb property based on its characteristics, amenities, and location — in order to optimize host revenue while maintaining competitive occupancy rates?

## Data Sources
Primary Dataset
Source: Kaggle – [Airbnb Price Dataset](https://www.kaggle.com/datasets/rupindersinghrana/airbnb-price-dataset/data)

Description: A structured dataset containing over 70,000 Airbnb listings from major U.S. cities.

Fields Used:
* price, log_price – nightly listing prices (raw and log-transformed)
* property_type, room_type, city, zipcode
* accommodates, bathrooms, bedrooms, beds
* instant_bookable – binary flag
* amenities – Top 20 Amenities: Extracted using correlation analysis between amenities and log_price

## Methodology
1. Data Cleaning and Preprocessing
2. Exploratory Data Analysis (EDA)
3. Model Development
    * Multiple Regression Models
    * Cross-Validation
    * Hyperparameter Tuning (Grid Search)
4. Model Evaluation

## Results
Model Comparison Summary
| Model                | MAE        | RMSE       | R²         | Notes                                                         |
| -------------------- | ---------- | ---------- | ---------- | ------------------------------------------------------------- |
| **Random Forest**    | 0.2900     | 0.3994     | 0.6666     | a simple yet effective regression                             |
| **LinearRegression** | 0.2803     | 0.3842     | 0.6914     | Simple, interpretable baseline                                |
| **Ridge**            | 0.2799     | 0.3833     | 0.6929     | Slight improvement over linear with regularization            |
| **Lasso**            | 0.3094     | 0.4179     | 0.6350     | Underperformed — likely over-regularized                      |
| **XGBoost**          | 0.2765     | 0.3780     | 0.7014     | Strong, non-linear, well-tuned ensemble                       |
| **SVR**              | **0.2666** | **0.3709** | **0.7125** | ⭐ Best performer overall — captures non-linearity effectively |
|**XGBoost + Ridge**   | 0.2728     | 0.3736     | 0.7082     | ✅ Strong ensemble; robust and consistent                     |

### Key Takeaways
1️⃣ SVR outperformed all other models across MAE, RMSE, and R², suggesting it's best at capturing complex pricing relationships — likely due to the RBF kernel's flexibility. 🚫 However, SVR doesn't scale well with 50k+ rows — For my dataset, it took **600+ mins** to complete the training...

2️⃣ XGBoost + Ridge Stacking Regressor strikes an excellent balance between:
    * Accuracy: second-best RMSE and R² overall
    * Robustness: combines linear and non-linear patterns
    * Production readiness: more scalable than SVR for large-scale usage

3️⃣ XGBoost was a close second and may be preferred for larger datasets due to SVR’s scalability limits.

4️⃣ Lasso underperforms consistently, possibly due to excessive feature shrinkage.

5️⃣ Linear and Ridge models perform reasonably but lag behind ensemble and kernel-based methods.

### ✅ Recommendation

Use `SVR` for small-to-medium batch predictions or if interpretability isn't a top concern.
Use `XGBoost + Ridge` for production scaling, feature importance analysis, and retraining on larger sets.

## Outline of project

- [Initial Report README.md](../README.md)
- Initial Report: Exploratory Data Analysis: [jin_airbnb_pricing.ipynb](jin_airbnb_pricing.ipynb)
- Final Models developing [final.ipynb](final.ipynb)

#### Summary of Initial Analysis

**Dataset**: Kaggle Airbnb Price Dataset (~74,000 listings from NYC and LA)

**Key Work**: 
- Data cleaning and feature engineering (selected top 20 amenities from 119 total)
- City-focused analysis (NYC: 32K, LA: 22K listings)
- Baseline Random Forest model (R²: 0.67, MAE: 0.29)

**Outcome**: Established foundation for final model optimization. 

