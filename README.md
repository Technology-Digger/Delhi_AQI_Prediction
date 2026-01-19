# 🌫️ Delhi AQI Prediction using Machine Learning

This project is an end-to-end Machine Learning system that predicts the **Air Quality Index (AQI) of Delhi** using both **air pollutant concentrations** and **meteorological (weather) features**.

The goal of this project is to build a **realistic and general AQI prediction model** by combining:
- Pollution data (PM2.5, PM10, CO, NO2)
- Weather data (Temperature, Humidity, Pressure, Wind Speed)

---

## 📌 Problem Statement

Air pollution is a major issue in Delhi. Accurately estimating AQI helps in:
- Public health awareness
- Policy planning
- Environmental monitoring systems

This project aims to:
> Predict the AQI index using historical pollution and weather data with Machine Learning.

---

## 📊 Dataset

**Source:** Delhi Weather & AQI 2025 Dataset  
**Rows:** ~52,000+ hourly records

### Features Used:
- `pm2_5` : PM2.5 concentration  
- `pm10` : PM10 concentration  
- `co` : Carbon Monoxide  
- `no2` : Nitrogen Dioxide  
- `temp_c` : Temperature  
- `humidity` : Humidity  
- `pressure_mb` : Air Pressure  
- `windspeed_kph` : Wind Speed  

### Target:
- `aqi_index` : Air Quality Index

---

## 🧹 Data Preprocessing

- Checked for missing values (none found)
- Performed **outlier capping using percentile method** (1% – 99%)
- This removed extreme sensor/noise values while keeping real-world high pollution days
- Performed Exploratory Data Analysis (EDA) using:
  - Histograms
  - Scatter plots
  - Correlation analysis

---

## 🔍 Exploratory Data Analysis (EDA)

Key findings:
- PM10 and PM2.5 are the **dominant factors** affecting AQI
- Weather features have **weaker but contextual influence**
- Wind speed shows a negative relationship with AQI (higher wind → lower AQI)

---

## 🤖 Models Trained & Compared

We trained and compared the following models:

1. K-Nearest Neighbors (KNN)
2. Decision Tree Regressor
3. Support Vector Regressor (SVR)
4. Random Forest Regressor ✅ (Best)

---

## 🏆 Model Performance (Final Setup: Weather + Pollution)

| Model | R² Score | MAE | RMSE |
|------|----------|------|--------|
| KNN | ~0.875 | ~45 | ~108 |
| Decision Tree | ~0.833 | ~47 | ~125 |
| SVR | ~0.754 | ~66 | ~151 |
| **Random Forest** | **~0.918** | **~38** | **~87** ✅ |

➡️ **Random Forest performed the best** due to its ability to handle non-linear relationships and noisy real-world data.

---

## 📈 Feature Importance (Random Forest)

Top contributing features:
1. **PM10 (~68%)**
2. PM2.5
3. NO2
4. Humidity
5. Temperature
6. CO
7. Wind Speed
8. Pressure

This confirms that **particulate matter (PM10 & PM2.5)** is the main driver of AQI in Delhi.

---

## ⚠️ Important Note on Data Leakage

AQI is calculated from pollutant values in real life.  
This project focuses on:
> Building a **general ML model using both weather and pollution data** to approximate AQI patterns, not a future forecasting system.

---

## 💾 Model Saving

The final trained model is saved using `joblib`:

## 🧪 Sample Prediction

Predicted AQI values are very close to actual values, usually within a few AQI points for normal conditions.

## 🛠️ Tech Stack

1. Python

2. Pandas, NumPy

3. Matplotlib, Seaborn

4. Scikit-learn

5. Jupyter Notebook

## 👨‍💻 Author

Anish Chatterjee
B.Tech CSE | AIML Enthusiast
```python
joblib.dump(rf, "delhi_aqi_rf_final_model.pkl")
