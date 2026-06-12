# Customer Churn Prediction

## Overview

This project predicts customer churn for a telecommunications company using machine learning. The solution includes a complete end-to-end pipeline covering data validation, preprocessing, feature engineering, model training, experiment tracking, inference, API serving, and containerized deployment.

The model is trained using XGBoost and served through FastAPI with an interactive Gradio interface.

## Features

* Data validation using Great Expectations
* Data preprocessing and feature engineering
* XGBoost classification model
* MLflow experiment tracking and model management
* FastAPI REST API
* Gradio web interface
* Dockerized deployment
* Reproducible training and inference pipeline

## Project Structure

```text
customer-churn/
│
├── data/
│   ├── raw/
│   └── processed/
│
├── src/
│   ├── app/
│   │   ├── app.py
│   │   └── main.py
│   │
│   ├── data/
│   ├── features/
│   ├── models/
│   ├── serving/
│   └── utils/
│
├── scripts/
├── model/
├── requirements.txt
├── Dockerfile
└── README.md
```

## Tech Stack

### Machine Learning

* XGBoost
* Scikit-learn
* Pandas
* NumPy

### MLOps

* MLflow
* Great Expectations

### Deployment

* FastAPI
* Gradio
* Docker

## Dataset

The project uses the Telco Customer Churn dataset.
[https://www.kaggle.com/datasets/blastchar/telco-customer-churn
](url)
Target Variable:

```text
Churn
```

Features include:

* Customer demographics
* Internet services
* Phone services
* Account information
* Billing information
* Contract details

## Model Performance

| Metric    | Score |
| --------- | ----- |
| Precision | 0.490 |
| Recall    | 0.821 |
| F1 Score  | 0.614 |
| ROC AUC   | 0.837 |

## Running the Training Pipeline

```bash
python scripts/run_pipeline.py \
--input data/raw/WA_Fn-UseC_-Telco-Customer-Churn.csv
```

The pipeline performs:

1. Data loading
2. Data validation
3. Preprocessing
4. Feature engineering
5. Train-test split
6. Model training
7. Evaluation
8. MLflow logging

## Running the Application Locally

### Install Dependencies

```bash
pip install -r requirements.txt
```

### Start FastAPI Server

```bash
uvicorn src.app.main:app --reload
```

### Access the Application

API:

```text
http://localhost:8000
```

Interactive UI:

```text
http://localhost:8000/ui
```

## Docker Deployment

### Build Image

```bash
docker build -t customer-churn .
```

### Run Container

```bash
docker run -p 8000:8000 customer-churn
```

### Access Application

```text
http://localhost:8000/ui
```

## API Endpoint

### Health Check

```http
GET /
```

Response:

```json
{
  "status": "ok"
}
```

### Predict Churn

```http
POST /predict
```

Example Request:

```json
{
  "gender": "Female",
  "Partner": "No",
  "Dependents": "No",
  "PhoneService": "Yes",
  "MultipleLines": "No",
  "InternetService": "Fiber optic",
  "OnlineSecurity": "No",
  "OnlineBackup": "No",
  "DeviceProtection": "No",
  "TechSupport": "No",
  "StreamingTV": "Yes",
  "StreamingMovies": "Yes",
  "Contract": "Month-to-month",
  "PaperlessBilling": "Yes",
  "PaymentMethod": "Electronic check",
  "tenure": 1,
  "MonthlyCharges": 85.0,
  "TotalCharges": 85.0
}
```

Example Response:

```json
{
  "prediction": "Likely to churn"
}
```

## Future Improvements

* CI/CD pipeline
* Cloud deployment on AWS


