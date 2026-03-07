# 📈 Retail Demand Forecasting  
## Reducing Inventory Risk with Machine Learning

```
Retail Transaction Data
        ↓
Feature Engineering
        ↓
Machine Learning Forecast Model
        ↓
Forecast Error Analysis
        ↓
Inventory Planning Insights
```

Forecasting retail demand is critical for inventory planning.  
This project develops a **machine learning–based demand forecasting model** using large-scale transaction data to improve prediction accuracy and analyze where forecast errors occur.

---

# 📊 Executive Summary

### Objective
Develop a demand forecasting model that improves prediction accuracy compared to a seasonal baseline.

### Dataset
- Retail transaction dataset  
- **10M+ records**  
- Multiple product categories  

### Key Results

| Metric | Baseline | Feature Model |
|------|------|------|
| RMSE | 26,460 | **23,440** |
| Error Reduction | — | **3,020 units** |
| Avg Daily Improvement | — | **~34 units/day** |

➡ Feature-based forecasting improves prediction accuracy and reduces uncertainty in inventory planning.

---

# 📈 Model Performance

## Predicted vs Actual Demand

![Predicted vs Actual](visuals/predicted_vs_actual.png)

Most predictions lie close to the diagonal reference line, indicating that the model captures the overall demand level reasonably well.  
However, extreme demand levels remain more difficult to predict.

---

## Forecast Error by Demand Segment

![Volume Segmentation](visuals/segmentation_volume_comparison.png)

Forecast errors vary across demand regimes:

- **Mid-demand segment → most stable forecasts**
- **High-demand segment → largest RMSE**

This indicates that demand spikes introduce additional forecasting uncertainty.

---

## Error vs Demand Level

![Error vs Demand](visuals/error_vs_demand_scatter.png)

The scatter plot shows **no strong linear relationship** between demand magnitude and forecast error.  
However, segmentation analysis reveals that forecast difficulty varies across demand regimes.

---

## Category Demand Volatility

![Category Volatility](visuals/category_volatility_vs_mean.png)

High-demand categories exhibit greater demand volatility, making them inherently more difficult to forecast.

---

# 🎯 Problem Definition

Retail demand forecasting plays a critical role in **inventory management**.

Poor forecasts cause:

- Overstock → increased holding costs  
- Stockouts → lost revenue  

### Goal

Develop a forecasting model that improves prediction accuracy and analyze where forecast errors occur.

---

# 📦 Dataset

Retail transaction data structure:

| Column | Description |
|------|------|
| date | transaction timestamp |
| cate | product category |
| name | product name |
| mart | store identifier |
| tot | sales quantity |

Derived features include:

```
date_day
weekday
hour
lag features
rolling statistics
```

Dataset scale:

```
10M+ rows
10 CSV files
```

---

# ⚙️ Methodology

### Data Processing

- Chunk-based large dataset processing
- Missing value handling
- String normalization

### Feature Engineering

Time-series features:

```
lag_1
lag_7
lag_14
lag_28
rolling mean (7)
rolling std (7)
weekday
month
```

These features capture:

- demand persistence  
- weekly seasonality  
- short-term demand fluctuations  

---

# 🤖 Modeling

Two forecasting approaches were compared.

### Baseline Model

Seasonal naive model:

```
Prediction(t) = demand(t-7)
```

---

### Feature Model

Machine learning model:

```
HistGradientBoostingRegressor
```

Evaluation metrics:

```
RMSE
WMAPE
sMAPE
```

---

# 🔎 Error Analysis

Forecast errors were analyzed across multiple dimensions.

### Weekday Analysis

Forecast errors vary across weekdays due to weekly demand patterns.

### Demand Segmentation

Demand levels were divided into:

```
Low
Mid
High
```

Key findings:

- **Mid-demand → most predictable**
- **High-demand → largest forecast errors**

### Demand Spikes

Demand spikes remain difficult to predict using historical features alone.

---

# 💡 Business Insights

Key operational findings:

- Forecast errors increase during **high-demand spikes**
- Demand regimes significantly affect forecasting performance
- Feature-based models outperform seasonal baselines

### Potential Improvements

Future forecasting systems could incorporate:

- promotion schedules  
- marketing campaigns  
- inventory availability signals  

These variables may help explain sudden demand spikes.

---

# 🗂 Project Structure

```
inventory_forecasting_project
│
├── notebooks
│   └── Demand_Forecasting_HGBR_WMAPE_Analysis.ipynb
│
├── visuals
│   ├── predicted_vs_actual.png
│   ├── segmentation_volume_comparison.png
│   ├── error_vs_demand_scatter.png
│   └── category_volatility_vs_mean.png
│
├── output
│   ├── error_by_weekday_rmse.csv
│   └── business_impact_summary.csv
│
└── README.md
```

---

# 🛠 Tech Stack

```
Python
Pandas
NumPy
Scikit-learn
Matplotlib
```

Model

```
HistGradientBoostingRegressor
```

---

# 📌 Key Takeaways

- Machine learning improves demand forecasting accuracy compared to seasonal baselines  
- Forecast difficulty varies across demand regimes  
- Demand spikes remain the main source of forecast error  

This project demonstrates how **data-driven forecasting can support more reliable inventory planning.**

---

# 👤 Author

Data Analysis Portfolio Project
