## Airbnb Price Optimizer

**Jin Zheng**

**2025 UC Berkeley MLAI Program Capstone Project**

**(Module 20) Initial Report: Exploratory Data Analysis**: [jin_airbnb_pricing.ipynb](jin_airbnb_pricing.ipynb)

### Data Source

I found data from Kaggle at https://www.kaggle.com/datasets/rupindersinghrana/airbnb-price-dataset/data

* Name: Airbnb Price Dataset
* Source: Scraped or aggregated from Airbnb listings across major U.S. cities
* Total Rows: ~50,000+ entries
* Purpose: Enable modeling and analysis of nightly Airbnb prices using property features

### Exploratory Data Analysis (EDA) 

1. Data obeservation by grouping the data by city. I narrow down the data to only NYC and LA
2. verify the correlation between some of the main features to the log-price and make sure the dataset is useable for our project model training
3. basic cleaning to remove duplicated and nan values
4. remove unneeded columns for fast processing
5. closer observation by looking at price_vs_accommodates, price_by_room_type, property_type_count, top_20_zipcodes_by_city
6. break down amenities and compare their correlation with the log_price
7. there were 119 distinct amenities and I would like to keep the top features for modeling to avoid overfitting, reduce dimensionality, and improve interpretability.
    * remove standard amenities
    * remove rare amenities
    * Rank Amenities by Correlation with Price
    * keep the top 20 features 

### Train a baseline model to use as a comparison

use a simple yet effective regression algorithm to predict log_price based on available features. 

* Baseline Model: Random Forest
* MAE:  0.2900
* RMSE: 0.3994
* R²:   0.6666

#### First iteration: 
MAE 0.29: On average, the predicted log-prices are off by 0.29 units. Since Im using log_price, this translates to a ~34% average relative error in raw price (exp(0.29) ≈ 1.34).
RMSE 0.3994: Slightly higher than MAE, indicating some larger errors/outliers in prediction. RMSE penalizes those more heavily.
The model explains ~66.7% of the variance in log_price. This is a solid baseline, suggesting that the input features (property details, location, top amenities) have meaningful predictive power.
The error range is acceptable, especially given that the prediction target is log-transformed, making interpretation robust to outliers.

#### Room for imprvements
Adding more predictive features (e.g., reviews, seasonal effects, event calendars)
Trying other models 