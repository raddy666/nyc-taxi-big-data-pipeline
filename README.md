# 🚕 Taxi Big Data Analysis & Prediction System

A **distributed big data analytics and prediction system** designed to analyze large-scale taxi transportation data and provide **demand hotspot analysis, congestion insights, and trip-duration prediction**.

This team project was developed during an internship at **Chengdu Suncape Data Co., Ltd.** (Big Data Analysis Team) and covers **end-to-end data engineering**, from raw data ingestion to distributed processing, analytics, visualization, and AI-assisted prediction.

---

## 📌 Project Overview

The system processes large volumes of taxi trip data using a **Hadoop-based distributed environment**, performs analytics with **Spark and Hive**, visualizes insights via **Apache Zeppelin**, and exposes trip-duration predictions through a **command-line chat assistant** (Random Forest model with a GPT-4 fallback).

Key goals:
- Scalable data processing on distributed infrastructure
- Reliable ETL pipeline for transportation datasets
- Actionable analytics for urban mobility
- Trip-duration prediction from historical patterns

---
### 📊 Dataset Scale

- **City:** New York City
- **Time Span:** 2010–2013
- **Data Size:** 3.15 GB (3,302,447 KB)
- **Records:** 20,142,893 taxi trips (exact count from HDFS)

The dataset captures multi-year urban transportation patterns at city scale, enabling large-scale demand analysis and congestion modeling.


## 🏗️ System Architecture

```text
Raw Taxi Data (Parquet)
        ↓
ETL Pipeline (pandas, Dask, PySpark)
        ↓
HDFS Distributed Storage
        ↓
Apache Hive (SQL Analytics)
        ↓
Apache Zeppelin (Visualization)
        ↓
Prediction Layer (Random Forest model + GPT-4 chat bot)
```
---

## 🔧 Core Features

### 📊 Distributed Data Processing
- 3-node Hadoop cluster with dedicated master node
- HDFS for fault-tolerant distributed storage
- Spark-based batch processing for large datasets

### 🔄 ETL Pipeline
- Parquet → CSV data transformation
- Data cleaning and normalization using pandas and PySpark
- Structured storage in MySQL for downstream access
- Automated data flow from ingestion to analytics

### 📈 Analytics & Visualization
- 30+ interactive visualizations in Apache Zeppelin (PySpark)
- Geospatial heatmaps for taxi demand hotspots
- Congestion pattern analysis using Hive SQL queries
- Time-based and region-based demand trends

### 🤖 Prediction & AI Integration
A command-line chat bot (`query.py`) answers natural-language questions about taxi trips:
- Feature extraction: regular expressions pull the day of the week, pickup hour (AM/PM) and taxi type (yellow, green, fhvhv) out of the question
- Prediction: a Random Forest regressor (scikit-learn, 100 trees, trained in `train_model.py` on pickup day, pickup hour and taxi type across the yellow, green, FHV and FHVHV datasets) returns the predicted trip duration in minutes
- Fallback: questions that are not trip-duration requests are forwarded to the OpenAI GPT-4 API
- Interface: command-line chat loop

**Example Query:**
> "How long will a yellow taxi trip take on Friday at 6 PM?"
> **Response:** "The predicted trip duration is *N* minutes."

---

## 🧩 Project Components

- Distributed storage and processing on a 3-node Hadoop cluster (Linux)
- ETL pipeline for yellow, green, FHV and FHVHV trip data
- Spark and Hive analytics with Apache Zeppelin dashboards
- Random Forest trip-duration model with a chat interface

---

## 🛠️ Technology Stack

- **Big Data:** Hadoop (HDFS, MapReduce)
- **Processing:** Apache Spark, PySpark
- **Query Engine:** Apache Hive
- **Visualization:** Apache Zeppelin
- **Database:** MySQL
- **Programming:** Python (pandas, PySpark, Dask)
- **Machine Learning:** scikit-learn (Random Forest)
- **Platform:** Linux
- **IDE:** PyCharm
- **AI Integration:** OpenAI API (GPT-4)

---

## ▶️ Setup & Execution (Local / Cluster)

>  This project targets a Hadoop/Spark cluster environment and is not intended for single-machine execution without distributed setup.


### Environment Setup
- Linux
- Hadoop cluster (standalone or multi-node)
- Apache Spark
- Apache Hive
- Apache Zeppelin
- MySQL
- Python 3.x

### Typical Workflow
1. Load raw taxi data into HDFS
2. Run the ETL scripts
3. Execute Hive queries for analytics
4. Visualize results in Zeppelin
5. Ask the chat bot for trip-duration predictions

---

## 📈 Example Use Cases

- Identifying taxi demand hotspots by time and location
- Detecting congestion-prone zones in urban areas
- Estimating trip durations by day, hour and taxi type
- Supporting data-driven transportation planning

---

## 🚧 Possible Extensions

- Real-time streaming using Kafka
- Deep learning-based demand forecasting
- REST API for prediction services
- City-scale deployment and performance benchmarking
- Dashboard deployment for municipal use

---

## 👥 Team

Team project developed at Chengdu Suncape Data Co., Ltd. (March 2025 – June 2025). See the repository's commit history for individual contributions.
