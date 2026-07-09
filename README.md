# 🌍 Global Air Quality Prediction System

A complete end-to-end Data Engineering and Machine Learning project developed as the **DEPI Graduation Project**. The project follows the **Medallion Architecture (Bronze → Silver → Gold)** to process global air quality data and build a machine learning model capable of predicting the **Air Quality Index (AQI)**.

---

## 📌 Project Overview

This project transforms raw air quality data into clean, analytics-ready datasets before training an optimized machine learning model to predict AQI.

The workflow includes:

- Data Ingestion
- Data Cleaning
- Data Validation
- Feature Engineering
- Exploratory Data Analysis (EDA)
- Medallion Architecture
- Machine Learning Model Training
- AQI Prediction
- Dashboard Visualization

---

## 🏗️ Project Architecture

```
Raw Data
    │
    ▼
Bronze Layer
(Data Ingestion)
    │
    ▼
Silver Layer
(Data Cleaning & Validation)
    │
    ▼
Gold Layer
(Feature Engineering & Analytics)
    │
    ▼
Machine Learning
(LightGBM Regression)
    │
    ▼
AQI Prediction Dashboard
```

---

## 📂 Project Structure

```
DEPI Final Discussion/

├── Medilian&EDA/
│   ├── bronze_layer.py
│   ├── silver_layer.py
│   ├── gold_layer.py
│   ├── EDA.py
│   ├── bronze_pipeline-Colab.ipynb
│   ├── silver_pipeline-Colab.ipynb
│   ├── gold_pipeline_Colab.ipynb
│   ├── silver_layer.csv
│   └── bronze_output.csv
│
├── Ai model/
│   ├── model_training.py
│   ├── predict.py
│   ├── src/
│   │   └── dashboard.py
│   ├── data/
│   ├── models/
│   ├── outputs/
│   └── README.md
│
└── README.md
```

---

## 🚀 Features

- Medallion Data Architecture
- Data Cleaning & Validation
- Missing Value Handling
- Feature Engineering
- Exploratory Data Analysis
- Machine Learning Pipeline
- Model Comparison
- Hyperparameter Tuning
- AQI Prediction
- Interactive Dashboard
- Feature Importance Analysis
- SHAP Explainability

---

## 🤖 Machine Learning

Several regression algorithms were evaluated, including:

- Linear Regression
- Ridge Regression
- Lasso Regression
- Decision Tree
- Random Forest
- XGBoost
- CatBoost
- **LightGBM (Best Model)**

### Best Model

**LightGBM Regressor**

Performance:

- **R² Score:** 0.885
- **RMSE:** 0.418

---

## 📊 Dataset

The project uses the **WAQI COVID-19 Air Quality Dataset (Q4 2023)**.

The dataset contains environmental measurements such as:

- AQI
- PM2.5
- PM10
- O₃
- NO₂
- SO₂
- CO
- Temperature
- Humidity
- Wind Speed
- Pressure
- UV Index
- City
- Country
- Date

---

## 📈 Project Workflow

1. Load raw dataset
2. Build Bronze Layer
3. Clean data into Silver Layer
4. Generate Gold Layer
5. Perform EDA
6. Train ML models
7. Evaluate models
8. Save best model
9. Predict AQI
10. Display dashboard

---

## 🛠️ Technologies Used

### Programming

- Python

### Data Processing

- Pandas
- NumPy

### Visualization

- Matplotlib
- Seaborn

### Machine Learning

- Scikit-learn
- LightGBM
- XGBoost
- CatBoost

### Explainability

- SHAP

### Model Persistence

- Joblib

---

## ⚙️ Installation

Clone the repository

```bash
git clone https://github.com/your-username/your-repository.git
```

Move into the project

```bash
cd your-repository
```

Install dependencies

```bash
pip install -r requirements.txt
```

---

## ▶️ Running the Project

### 1. Build Data Pipeline

Run the Bronze, Silver, and Gold layer scripts.

### 2. Train the Model

```bash
python "Ai model/model_training.py"
```

### 3. Predict AQI

```bash
python "Ai model/predict.py"
```

---

## 📊 Outputs

The project generates:

- Trained LightGBM model
- Feature Importance
- Correlation Heatmap
- SHAP Summary
- Residual Plot
- Prediction Results
- Dashboard
- CSV Prediction File

---

## 📌 Future Improvements

- Real-time AQI prediction
- Weather API integration
- Cloud deployment
- Docker support
- CI/CD pipeline
- Streamlit web application
- Automated retraining

---

## 👨‍💻 Team

Developed as part of the **Digital Egypt Pioneers Initiative (DEPI)** Graduation Project.

---

## 📄 License

This project is intended for educational purposes.
