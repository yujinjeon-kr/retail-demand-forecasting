#  Retail Demand Forecasting  
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

#  Executive Summary

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

#  Model Performance

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

#  Problem Definition

Retail demand forecasting plays a critical role in **inventory management**.

Poor forecasts cause:

- Overstock → increased holding costs  
- Stockouts → lost revenue  

### Goal

Develop a forecasting model that improves prediction accuracy and analyze where forecast errors occur.

---

#  Dataset

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

#  Methodology

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

#  Modeling

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

#  Error Analysis

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

#  Business Insights

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

#  Tech Stack

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

#  Key Takeaways

- Machine learning improves demand forecasting accuracy compared to seasonal baselines  
- Forecast difficulty varies across demand regimes  
- Demand spikes remain the main source of forecast error  

This project demonstrates how **data-driven forecasting can support more reliable inventory planning.**







# 📈 소매 수요 예측 프로젝트  
## 머신러닝 기반 재고 리스크 감소

```
소매 거래 데이터
        ↓
피처 엔지니어링
        ↓
머신러닝 수요 예측 모델
        ↓
예측 오차 분석
        ↓
재고 운영 인사이트 도출
```

소매 산업에서 수요 예측은 재고 운영의 핵심 요소이다.  
본 프로젝트는 대규모 거래 데이터를 활용하여 **머신러닝 기반 수요 예측 모델**을 구축하고, 예측 정확도를 개선하며 예측 오차가 발생하는 패턴을 분석하는 것을 목표로 한다.

---

# 📊 프로젝트 요약 (Executive Summary)

### 목표

계절성 기반 베이스라인 모델 대비 **더 높은 예측 정확도를 갖는 수요 예측 모델을 개발**하는 것이 목표이다.

### 데이터

- 소매 거래 데이터셋  
- **1,000만 건 이상 거래 데이터**  
- 다양한 상품 카테고리 포함  

### 주요 결과

| 지표 | Baseline | Feature Model |
|------|------|------|
| RMSE | 26,460 | **23,440** |
| 오차 감소 | — | **3,020 units 감소** |
| 일 평균 개선 | — | **약 34 units 감소** |

➡ 피처 기반 모델이 계절성 기반 모델 대비 예측 정확도를 개선하고 재고 운영의 불확실성을 줄이는 결과를 보였다.

---

# 📈 모델 성능

## 실제 수요 vs 예측 수요

![Predicted vs Actual](visuals/predicted_vs_actual.png)

대부분의 예측값이 대각선 기준선 근처에 위치한다.  
이는 모델이 전체 수요 수준을 비교적 잘 학습했음을 의미한다.

다만 **수요가 급증하는 구간에서는 예측 난도가 높아지는 경향**이 나타난다.

---

## 수요 구간별 예측 오차

![Volume Segmentation](visuals/segmentation_volume_comparison.png)

수요 구간에 따라 예측 오차가 다르게 나타난다.

- **중간 수요 구간(Mid-demand)** → 가장 안정적인 예측
- **높은 수요 구간(High-demand)** → 가장 큰 RMSE 발생

이는 수요 급증 구간에서 예측 불확실성이 커지는 경향을 보여준다.

---

## 수요 수준 vs 예측 오차

![Error vs Demand](visuals/error_vs_demand_scatter.png)

수요 수준과 예측 오차 사이에 **뚜렷한 선형 관계는 관찰되지 않는다.**

하지만 수요 구간별 분석 결과를 보면 예측 난도는 **수요 규모 자체보다 수요 레짐(demand regime)** 에 영향을 받는 경향이 있다.

---

## 카테고리별 수요 변동성

![Category Volatility](visuals/category_volatility_vs_mean.png)

평균 판매량이 높은 카테고리는 일반적으로 **수요 변동성 또한 높은 경향**을 보인다.

이는 고수요 카테고리가 상대적으로 예측 난도가 높을 수 있음을 시사한다.

---

# 🎯 문제 정의

소매 산업에서 수요 예측은 **재고 관리와 운영 효율성에 직접적인 영향을 미친다.**

부정확한 수요 예측은 다음과 같은 문제를 발생시킨다.

- 과잉 재고 → 보관 비용 증가  
- 품절 발생 → 매출 손실  

### 프로젝트 목표

베이스라인 대비 더 정확한 수요 예측 모델을 개발하고  
예측 오차가 발생하는 주요 패턴을 분석하는 것이다.

---

# 📦 데이터

사용된 데이터는 다음과 같은 구조를 가진 소매 거래 데이터이다.

| 컬럼 | 설명 |
|------|------|
| date | 거래 시간 |
| cate | 상품 카테고리 |
| name | 상품 이름 |
| mart | 매장 식별자 |
| tot | 판매 수량 |

파생 변수

```
date_day
weekday
hour
lag features
rolling statistics
```

데이터 규모

```
1,000만 건 이상 데이터
10개의 CSV 파일
```

---

# ⚙️ 분석 방법

### 데이터 처리

- 대용량 데이터를 위한 chunk 단위 처리
- 결측값 처리
- 문자열 정규화

### 피처 엔지니어링

시계열 기반 피처 생성

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

이 피처들은 다음 패턴을 반영한다.

- 수요 지속성  
- 주간 계절성  
- 단기 수요 변동  

---

# 🤖 모델링

두 가지 접근 방식을 비교하였다.

### Baseline 모델

계절성 기반 naive 모델

```
Prediction(t) = demand(t-7)
```

---

### Feature 기반 모델

머신러닝 모델

```
HistGradientBoostingRegressor
```

평가 지표

```
RMSE
WMAPE
sMAPE
```

---

# 🔎 오차 분석

모델의 예측 오차를 여러 관점에서 분석하였다.

### 요일별 오차

요일에 따라 예측 오차가 다르게 나타난다.  
이는 주간 수요 패턴의 영향으로 해석할 수 있다.

### 수요 구간 분석

수요를 세 구간으로 나누어 분석하였다.

```
Low
Mid
High
```

분석 결과

- **Mid-demand 구간 → 가장 안정적인 예측**
- **High-demand 구간 → 가장 큰 예측 오차**

### 수요 급증 구간

수요 급증 구간은 과거 데이터만으로 예측하기 어려운 경향이 있다.

---

# 💡 비즈니스 인사이트

분석 결과 다음과 같은 운영 인사이트를 도출하였다.

### 주요 결과

- 높은 수요 구간에서 예측 오차 증가
- 수요 레짐에 따라 예측 난도 변화
- 머신러닝 기반 모델이 베이스라인보다 높은 예측 정확도

### 향후 개선 방향

예측 정확도를 더 개선하기 위해 다음 외생 변수를 활용할 수 있다.

- 프로모션 일정  
- 마케팅 이벤트  
- 재고 가용성  

이 변수들은 수요 급증 현상을 설명하는 데 도움이 될 수 있다.

---


# 🛠 기술 스택

```
Python
Pandas
NumPy
Scikit-learn
Matplotlib
```

사용 모델

```
HistGradientBoostingRegressor
```

---

# 📌 핵심 요약

- 머신러닝 기반 수요 예측 모델이 베이스라인 대비 예측 정확도를 개선
- 예측 난도는 수요 규모보다 **수요 레짐**의 영향을 더 크게 받는 경향
- 수요 급증 구간이 주요 예측 실패 원인

본 프로젝트는 **데이터 기반 수요 예측이 재고 운영 안정성 향상에 기여할 수 있음을 보여준다.**
