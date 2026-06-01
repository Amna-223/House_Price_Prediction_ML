# Islamabad House Price Prediction System

A machine learning-based web scraping project that predicts real estate prices in Islamabad using property data from Zameen.com.

## Project Overview

This project builds an end-to-end ML pipeline to estimate house prices in Islamabad. Property listings are scraped from Zameen.com, preprocessed, and used to train multiple regression models. The best model (Decision Tree) achieves 90.7% accuracy in predicting property prices.

## Key Features

- Web Scraping: Automated data collection from Zameen.com using Selenium
- Data Preprocessing: Missing value handling, outlier removal, feature engineering
- Multiple Models: Linear Regression, Decision Tree, Random Forest, Gradient Boosting, XGBoost, CatBoost
- Interactive CLI: User-friendly prediction system for price estimation

## Technologies Used

- Python
- Selenium WebDriver & BeautifulSoup (web scraping)
- Pandas & NumPy (data processing)
- Scikit-learn (modeling & evaluation)
- XGBoost & CatBoost (boosting algorithms)

## Dataset

- Source: Zameen.com (Islamabad properties)
- Total Listings: 325 properties
- Features: Price, area (Marla/Kanal), bedrooms, bathrooms, location, built year, parking, servant quarters, store rooms, kitchens, drawing rooms

## Data Processing Steps

1. Missing Value Treatment: Filled with zeros or median values
2. Feature Engineering:
   - Price conversion (Crore/Lakh/Arab → Crore)
   - Area conversion (Marla/Kanal → square yards)
   - Property age calculation
   - Location premium scores
   - Luxury score creation
3. Outlier Removal: Removed price/area outliers beyond 3 standard deviations
4. Encoding: Label encoding and one-hot encoding (52 total features)
5. Scaling: StandardScaler applied

## Model Performance Comparison

01) Best Model: Decision Tree
R² Score: 0.9072 (explains 90.7% of price variance)
MAE: 1.62 Crore
RMSE: 2.63 Crore
MAPE: 17.22%

Why it won: Captures non-linear relationships naturally, handles feature interactions well, robust to outliers

02) Runner Up: CatBoost
R² Score: 0.8756
MAE: 1.98 Crore
RMSE: 3.04 Crore
MAPE: 20.24%

03) Gradient Boosting
R² Score: 0.8658
MAE: 2.04 Crore
RMSE: 3.17 Crore
MAPE: 22.50%

04) Random Forest
R² Score: 0.8338
MAE: 1.99 Crore
RMSE: 3.52 Crore
MAPE: 19.48%

05) Linear Regression (Baseline)
R² Score: 0.7971
MAE: 2.62 Crore
RMSE: 3.89 Crore
MAPE: 35.47%

06) XGBoost
R² Score: 0.7514
MAE: 2.33 Crore
RMSE: 4.30 Crore
MAPE: 20.58%

Why it performed worst: Small dataset (325 records) – boosting algorithms typically need larger datasets for optimal performance

##  How to Run the Project

The system runs in an interactive loop
Input: area (e.g., "10 Marla", "1 Kanal"), bedrooms, bathrooms, location
Output: Estimated price in Crore or Lakh

### Prerequisites
```bash
pip install pandas numpy scikit-learn selenium beautifulsoup4 xgboost catboost