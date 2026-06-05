---
layout: default
title: Seasonal Forecasting of Ferry Passenger Demand
---

# Seasonal Forecasting of Ferry Passenger Demand for Operational Planning

## Overview

This research applies the **Seasonal Autoregressive Integrated Moving Average (SARIMA)** model to forecast monthly ferry passenger volumes at **Bakauheni Port, Lampung, Indonesia** — one of the busiest ferry ports connecting the islands of Sumatra and Java.

The goal is to support data-driven operational planning, including vessel scheduling, resource allocation, and service optimization based on recurring seasonal demand patterns.

---

## Publication

**Journal:** International Journal of Electronics and Communications System (IJECS)

**Volume:** 5, Issue 2, pp. 221–233

**DOI:** [10.24042/ijecs.v5i2.26694](https://ejournal.radenintan.ac.id/index.php/IJECS/article/view/26694)

**ISSN:** 2798-2610

**Authors:** Khoirul Mizan Abdullah, Luluk Muthoharoh, Eggi Satria, Rahma Neliyana, Presilia, Gymnastiar Al Khoarizmy, Anwar Muslim, Ira Safitri

[Read Full Article](https://ejournal.radenintan.ac.id/index.php/IJECS/article/view/26694)

---

## Problem

Bakauheni Port serves as a critical gateway between Sumatra and Java. Based on data from BPS Lampung (2023), ferry transport accounts for **52.32% of total passenger movements** in Lampung Province.

Passenger demand fluctuates heavily throughout the year — surging during Eid al-Fitr, school holidays, and national celebrations — causing congestion and operational strain. Without reliable forecasting, port authorities struggle to plan vessel schedules and allocate resources effectively.

The core challenge: **predict future passenger volumes accurately enough to support proactive operational decisions.**

---

## Objective

Develop and evaluate a SARIMA-based forecasting model that:
- Captures both trend and seasonal patterns in monthly ferry passenger data
- Achieves sufficient accuracy to support short- to medium-term planning
- Provides a practical, interpretable tool for port operational management

---

## Dataset

<img src="images/time series plot.png" alt="Monthly Ferry Passenger Departures at Bakauheni Port 2014-2019"/>

*Monthly ferry passenger departures at Bakauheni Port (2014–2019), showing clear seasonal peaks during Eid al-Fitr and holiday periods*

- **Source:** BPS (Statistics Indonesia) — Lampung Province
- **Coverage:** Monthly ferry passenger departure records, January 2014 – December 2019
- **Format:** Originally published as infographics, manually extracted into tabular format
- **Split:** 80% training / 20% testing
- **Unit:** Thousands of passengers

Sample data range: from ~6,497 passengers (February 2015) to ~200,000+ during peak months.

---

## Methodology

The research followed a structured time series modeling workflow:

1. **Data Collection** — BPS Lampung official data
2. **Data Extraction** — Converting infographic format to tabular structure
3. **Train-Test Split** — 80:20 ratio
4. **Stationarity Testing** — Augmented Dickey-Fuller (ADF) test
5. **Variance Stabilization** — Box-Cox transformation (λ optimization)
6. **Differencing** — Seasonal (lag-12) + first-order differencing to achieve stationarity
7. **Model Identification** — ACF and PACF plot analysis
8. **Model Selection** — AIC, MAPE, and RMSE comparison across candidate models
9. **Model Diagnostics** — Q-Q plot, Ljung-Box, Shapiro-Wilk, Jarque-Bera tests
10. **Forecasting** — 8-period ahead forecast on test set

---

## Model Selection

Six SARIMA candidate models were evaluated. Key comparison results:

| Model | MAPE | RMSE | AIC |
|---|---|---|---|
| **(2,1,1)(0,1,0)₁₂** | **0.0477** | **0.001664** | **−511.67** |
| (0,1,1)(0,1,0)₁₂ | 0.0505 | 0.001802 | −502.39 |
| (1,1,0)(0,1,0)₁₂ | 0.0515 | 0.221839 | −501.29 |
| (1,1,1)(0,1,0)₁₂ | 0.0476 | 0.001670 | −512.99 |
| (1,1,2)(0,1,1)₁₂ | 0.0477 | 0.001665 | −511.54 |

The **SARIMA (2,1,1)(0,1,0)₁₂** model was selected based on its combination of lowest AIC, low RMSE, and all statistically significant parameters (AR1, AR2, MA1 all p < 0.05).

---

## Model Diagnostics

The selected model passed all key residual assumption checks:

| Test | Result | Interpretation |
|---|---|---|
| Ljung-Box | p = 0.2556 | No significant autocorrelation in residuals ✅ |
| Shapiro-Wilk | p = 7.145e-06 | Residuals approximately normal ✅ |
| Jarque-Bera | p = 2.2e-16 | Supports normal distribution of residuals ✅ |
| Q-Q Plot | Closely aligned with diagonal | Residuals follow normal distribution ✅ |

---

## Results

<img src="images/forecasting plot.png" alt="SARIMA Forecasting Plot - Train, Test, and Predicted Passenger Volumes"/>

*Forecasting plot: blue = training data, red = actual test data, green = model predictions*

The SARIMA (2,1,1)(0,1,0)₁₂ model produced:

- **MAPE: 11.47%** → Classified as "good" accuracy (within 10%–20% range)
- **Forecasting Accuracy: 88.53%**
- Strong seasonal pattern capture — peaks aligned with Eid al-Fitr and holiday periods
- Suitable for short- to medium-term operational planning horizons

The forecasting plot confirmed the model tracks actual passenger movement closely, with predicted values (green line) following the test observations (red line) within acceptable deviation bounds.

---

## Operational Impact

The forecasting model can directly support:
- **Vessel scheduling** — anticipate high-demand periods and pre-assign capacity
- **Resource allocation** — staff, ticketing, and docking preparation ahead of peak periods
- **Congestion reduction** — proactive management of passenger surges during Eid al-Fitr and year-end travel
- **Service quality improvement** — reduced waiting times and better passenger experience
- **Environmental sustainability** — optimized scheduling reduces unnecessary fuel consumption, aligned with SDG goals on clean energy and resilient infrastructure

---

## Limitations

- The model uses only historical passenger data — external factors such as weather, economic conditions, or special policy changes are not incorporated
- Performance may decline over longer forecasting horizons due to accumulated uncertainty
- Future improvements may include SARIMAX (with external variables) or hybrid deep learning approaches (e.g., SARIMA + LSTM)

---

## My Contribution

As one of the authors (G.A.K.), I contributed to:
- Literature review and analysis of related research
- Preparation of the theoretical basis and research methodology

---

## Tech Stack

- **R** — Time series modeling and statistical analysis
- **SARIMA** — Seasonal ARIMA modeling
- **ADF Test** — Stationarity assessment
- **Box-Cox Transformation** — Variance stabilization
- **ACF / PACF Analysis** — Model order identification
- **Ljung-Box, Shapiro-Wilk, Jarque-Bera** — Residual diagnostics
- **MAPE, RMSE, AIC** — Model evaluation metrics

---

## Article Link

[View Published Article — DOI: 10.24042/ijecs.v5i2.26694](https://ejournal.radenintan.ac.id/index.php/IJECS/article/view/26694)
