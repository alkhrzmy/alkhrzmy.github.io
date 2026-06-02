---
layout: default
title: Seasonal Forecasting of Ferry Passenger Demand
---

# Seasonal Forecasting of Ferry Passenger Demand for Operational Planning

## Overview

This research project focuses on forecasting monthly ferry passenger demand at **Bakauheni Port, Lampung, Indonesia** using a seasonal time series approach.

The study applies the **Seasonal Autoregressive Integrated Moving Average (SARIMA)** model to capture recurring passenger movement patterns and support data-driven operational planning in ferry transportation.

---

## Publication

This project was published in the **International Journal of Electronics and Communications System (IJECS)**.

**Title:** Seasonal Forecasting of Ferry Passenger Demand for Operational Planning: Evidence from Bakauheni Port, Indonesia

**DOI:** 10.24042/ijecs.v5i2.26694

[Read Article](https://ejournal.radenintan.ac.id/index.php/IJECS/article/view/26694)

---

## Problem

Bakauheni Port is one of the major ferry transportation hubs connecting Sumatra and Java. Passenger demand at this port changes over time and often increases during specific seasonal periods, such as public holidays, school holidays, and Eid al-Fitr.

Without accurate forecasting, port authorities may face challenges in planning vessel schedules, resource allocation, passenger services, and operational capacity.

---

## Objective

The objective of this research is to develop a forecasting model that can predict monthly ferry passenger demand at Bakauheni Port and support operational planning through data-driven decision-making.

---

## Dataset

The dataset was collected from the official website of **Statistics Indonesia (BPS) for Lampung Province**.

The data consists of monthly ferry passenger departure records at Bakauheni Port from **2014 to 2019**. The original data was available in infographic format and was transformed into tabular format for analysis.

---

## Methodology

The research workflow includes:

1. **Data Collection**
   Monthly ferry passenger departure data was collected from official BPS Lampung sources.

2. **Data Extraction**
   Passenger data from infographic format was converted into structured tabular format.

3. **Train-Test Split**
   The dataset was divided into training and testing subsets using an 80:20 split.

4. **Stationarity Checking**
   The Augmented Dickey-Fuller (ADF) test was used to assess stationarity.

5. **Data Transformation**
   Box-Cox transformation and differencing were applied to stabilize variance and remove trend or seasonal components.

6. **Model Identification**
   ACF and PACF plots were used to identify candidate SARIMA model parameters.

7. **Model Selection**
   Candidate models were compared using AIC, RMSE, and MAPE.

8. **Model Diagnostics**
   Residual diagnostics were performed to evaluate model adequacy.

9. **Forecasting**
   The selected SARIMA model was used to forecast future passenger demand.

---

## Model

The selected model was:

**SARIMA (2,1,1)(0,1,0)12**

This model was selected because it showed strong performance in capturing seasonal passenger patterns while maintaining good forecasting accuracy.

---

## Results

The SARIMA model produced reliable forecasting performance for ferry passenger demand at Bakauheni Port.

Key results:

* **MAPE:** 11.47%
* **Forecasting Accuracy:** 88.53%
* The model successfully captured seasonal passenger movement patterns.
* The model can support short- to medium-term operational planning.

These results indicate that SARIMA is suitable for forecasting ferry passenger demand with strong seasonal characteristics.

---

## Operational Impact

The forecasting results can help port authorities and ferry operators in:

* Planning vessel schedules
* Allocating operational resources
* Anticipating seasonal passenger surges
* Reducing service delays and congestion
* Improving passenger service quality
* Supporting data-driven transportation planning

---

## Limitation

This study only used historical passenger data and did not include external factors such as weather, economic conditions, special events, or policy changes. Future work may improve the model by incorporating external variables or comparing SARIMA with machine learning and deep learning forecasting models.

---

## My Contribution

As one of the authors, I contributed to the literature review, related research analysis, theoretical foundation, and research methodology preparation.

---

## Tech Stack

* Time Series Forecasting
* SARIMA
* ADF Test
* Box-Cox Transformation
* ACF and PACF Analysis
* Model Diagnostics
* MAPE, RMSE, and AIC Evaluation
* R / Statistical Time Series Analysis

---

## Article Link

[View Published Article](https://ejournal.radenintan.ac.id/index.php/IJECS/article/view/26694)