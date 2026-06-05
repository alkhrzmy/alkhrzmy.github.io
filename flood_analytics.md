---
layout: default
title: Predictive Flood Analytics with Hadoop Ecosystem in Lampung
---

# Predictive Flood Analytics with Hadoop Ecosystem in Lampung Province

## Overview

This project implements a comprehensive **Hadoop ecosystem** consisting of 12 integrated services for predictive flood analysis in **Lampung Province, Indonesia**.

The system is designed to handle multi-source big data from weather stations, IoT sensors, satellite imagery, and historical flood records — integrating them into a unified pipeline for real-time monitoring and flood risk prediction.

Published at **Seminar Nasional Sains Data 2024 (SENADA 2024)**, UPN "Veteran" Jawa Timur.

---

## Problem

Lampung Province faces increasing flood frequency and severity. A major flood hit Bandar Lampung on June 11, 2020 due to the overflow of Kalibalau River, highlighting the urgent need for an effective flood prediction and mitigation system.

The core challenge was **data fragmentation** across agencies — weather data from BMKG, topographic data from BIG, historical flood records from BNPB, and field sensor readings were all stored separately without adequate integration.

---

## Objective

Build a production-ready distributed big data infrastructure that can:
- Integrate multi-source, heterogeneous data in real-time
- Process batch and streaming data for flood prediction
- Provide real-time dashboards for monitoring and early warning
- Serve as a replicable foundation for disaster management systems across Indonesia

---

## System Architecture

The system follows a **microservices architecture** with 12 integrated services deployed via Docker containers, organized into the following layers:

| Layer | Components |
|---|---|
| Storage Layer | HDFS (NameNode, DataNode, HistoryServer) |
| Resource Management | YARN (ResourceManager, NodeManager) |
| Stream Processing | Apache Kafka (KRaft mode), Zookeeper |
| Batch & Stream Processing | Apache Spark (Master + Worker) |
| SQL Interface | Apache Hive |
| NoSQL Storage | Apache HBase |
| Visualization | Apache Superset |

All services are orchestrated with `docker-compose` and communicate over a single bridge network with inter-container latency under 1ms.

---

## Data Sources

Data was collected from 5 primary sources:

| Source | Format | Volume | Description |
|---|---|---|---|
| BMKG | CSV/JSON via REST API | ~500 MB/day | Rainfall, humidity, temperature, wind speed |
| BNPB | PostgreSQL | ~2 GB (10 years) | Historical flood records: location, date, severity |
| DEMNAS | GeoTIFF (30m resolution) | — | Elevation data for topographic analysis |
| IoT Sensors | JSON via MQTT | ~1 GB/day | Real-time field readings every 5 minutes |
| Satellite Imagery | Remote sensing | ~5 GB/day | Spatial and land cover analysis |

---

## Data Pipeline

The pipeline implements **Lambda Architecture** with dual processing paths:

**Batch Processing:**
> HDFS Raw Data → Spark ETL → Feature Store → Model Training → Hive Tables

**Stream Processing:**
> IoT Sensors → Kafka Topics → Spark Streaming → Feature Engineering → ML Prediction → HBase → Alerts

---

## Performance Results

### Data Ingestion
| Source | Throughput | Notes |
|---|---|---|
| BMKG API | 700 KB/s | 99.9% success rate |
| Kafka IoT Sensors | 2.5 MB/s | 50,000 messages/second |
| Satellite Batch Import | 1.9 MB/s | 5GB processed in 45 minutes |
| BNPB Database | 420 KB/s | Historical flood data import |

### Spark vs MapReduce Processing Speed
| Task | Data Size | MapReduce | Spark | Improvement |
|---|---|---|---|---|
| Daily Weather Aggregation | 1 GB | 4.5 min | 0.7 min | **6.4x** |
| Spatial Join (Flood Zones) | 5 GB | 22 min | 3.2 min | **6.9x** |
| Time Series Analysis | 3 GB | 15 min | 1.8 min | **8.3x** |
| Feature Engineering | 10 GB | 38 min | 5.5 min | **6.9x** |

### Spark Streaming (Real-Time Processing)
- Processing Latency: **< 5 seconds** ✅
- Throughput: **10 GB/hour** ✅
- Micro-batch Interval: 2 seconds

### System Uptime (3-Day Monitoring)
- System Availability: **99.3%** (target: 99%)
- Average Resource Utilization: 65%
- Storage Growth: 5 GB/day (with Snappy compression)

---

## Machine Learning

Machine learning exploration was done using **Spark MLlib**:

- **Random Forest Classifier** — Flood risk classification (Low / Medium / High) using 23 features from weather, topographic, and historical data. Trained on 80% data, validated on 20%.
- **Gradient Boosting** — Water level prediction. Feature importance analysis identified **rainfall intensity** and **elevation** as top predictors.

Key ML challenges: limited labeled data, imbalanced classes (few extreme flood events), and complexity of spatial-temporal feature engineering.

---

## Visualization

Apache Superset was integrated with Apache Hive for real-time business intelligence dashboards:

- Real-time weather monitoring (30-second refresh)
- Flood risk heatmap (geospatial visualization)
- Historical trend analysis (time-series charts)
- Alert dashboard with critical threshold monitoring

---

## Key Learnings

Through this project, I learned how to:
- Design and deploy a production-ready distributed big data infrastructure
- Orchestrate 12 microservices using Docker and docker-compose
- Build Lambda Architecture pipelines for both batch and stream data processing
- Integrate heterogeneous multi-source data (API, IoT, geospatial, satellite)
- Apply Spark MLlib for flood risk classification on spatial-temporal data
- Build real-time monitoring dashboards with Apache Superset

---

## Tech Stack

- **Apache Hadoop** (HDFS, YARN) — Distributed storage and resource management
- **Apache Spark** — Batch and stream processing, MLlib
- **Apache Kafka** — Real-time data ingestion
- **Apache Hive** — SQL interface over HDFS
- **Apache HBase** — NoSQL time-series storage
- **Apache Superset** — Real-time dashboards
- **Docker & docker-compose** — Containerization and orchestration
- **Python** — ETL scripts, data ingestion, Jupyter notebooks
- **MQTT** — IoT sensor data protocol

---

## Publication

**Title:** Implementasi Ekosistem Hadoop Untuk Analisis Prediktif Banjir di Provinsi Lampung Menggunakan Multi-Source Big Data

**Venue:** Seminar Nasional Sains Data 2024 (SENADA 2024), UPN "Veteran" Jawa Timur

**ISSN:** E-ISSN 2808-5841 | P-ISSN 2808-7283

**Authors:** Gymnastiar Al Khoarizmy, Hermawan Manurung, Esteria Rohanauli Sidauruk, Shula Talitha Ardhya Putri, Ardika Satria, Luluk Muthoharoh

---

## Repository

GitHub repository and additional documentation will be added here.
