# Predicting Retail Sales Forecasting with Data Analytics

This project forecasts weekly retail sales using Python and machine learning techniques.
It was completed as part of The Build Fellowship (Sept–Oct 2025) under the mentorship of Nicholas Yuwono.

# Data Source
The data used in this project comes from the Kaggle dataset:

**Retail Dataset — manjeetsingh/retaildataset**

It includes:

**sales data-set.csv** – Weekly sales per store

**stores data-set.csv** – Store details

**Features data set.csv** – Economic and seasonal features

The dataset was downloaded programmatically using ```kaggle```.

# 1. Exploratory Data Analysis

**A. Sales Data Visualization**

**Bar Chart: Holiday vs Non-Holiday Sales**

Average weekly sales are higher during holidays, likely due to seasonal promotions and increased customer activity.

**B. Store Data Visualizations**

**Scatterplot: Weekly Sales over Time**

Shows sales spikes during holiday periods

# 2. Relationship in the Data
**Linear Regression: Weekly Sales vs Unemployment**
* Correlation is very weak
* R² is extremely low
* Regression line is almost flat
**Conclusion:** Unemployment alone does not meaningfully predict weekly sales

# 3. Building Prediction Models
**3A. Single-Feature Model**
* Predictor: Unemployment
* Target: Weekly Sales

**Results:**
* Low R²
* Model predicts nearly constant values
* Actual vs Predicted scatterplot does not follow identity line
**Conclusion:** A single feature is insufficient.

**3B. Multi-Feature Model**
Features used:
* Unemployment
* CPI
* Fuel Price
* Temperature
* IsHoliday

**Result:**
* Only a small improvement
* Still poor predictive performance
**Conclusion:** Weekly sales depend on other factors not captured in these variables.

# 4. Adding a 3-Week Lag Feature
To capture short-term demand cycles:
```python
data['Lag_3_Week'] = data['Weekly_Sales'].shift(3)
```
After including this lag feature:
* R² improved to ~0.83
* Predictions aligned closely with actual values
* Residuals centered clearly around zero
* Actual vs Predicted plot showed tight clustering

**Conclusion:**
* Short-term historical sales are the strongest predictor of weekly retail sales.
* Lag features dramatically improve model accuracy.

# Tools & Libraries Used
* Python
* pandas
* numpy
* matplotlib
* seaborn
* scikit-learn
* statsmodels
* kagglehub

**Key Outcomes**
* Built multiple regression models to evaluate predictors
* Added a 3-week lag that boosted accuracy from near-zero to ~83%
* Conducted full exploratory analysis with visualizations
* Demonstrated importance of time-series feature engineering in retail forecasting

