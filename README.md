# Capstone MLOps Project

## Project Overview

This project implements a complete MLOps pipeline for a machine learning classification application based on the **Breast Cancer dataset**.

The workflow covers the complete lifecycle of the ML application, including dataset versioning, data processing, model training, experiment management, model selection, API development, containerization, and automated CI/CD.

### Key Components

* **DVC** – Dataset and pipeline version control
* **Scikit-learn** – Machine learning model development
* **MLflow** – Experiment tracking and model management
* **FastAPI** – REST API for model predictions
* **Docker** – Application containerization
* **GitHub Actions** – Continuous Integration and Continuous Deployment

---

## End-to-End Pipeline

The project follows the workflow below:

```text
Breast Cancer Dataset
        ↓
Dataset Versioning with DVC
        ↓
Data Processing
        ↓
Training Multiple Classifiers
        ↓
MLflow Experiment Tracking
        ↓
Performance Evaluation
        ↓
Selection of Best Model
        ↓
Model Registration
        ↓
FastAPI REST Service
        ↓
Docker Container
        ↓
GitHub Actions CI/CD
```

---

## Model Development and Comparison

Three different classification algorithms were trained and evaluated:

1. **Random Forest**
2. **Decision Tree**
3. **Logistic Regression**

### Evaluation Results

| Classification Model |  Accuracy |
| -------------------- | --------: |
| Random Forest        |     0.956 |
| Decision Tree        |     0.912 |
| Logistic Regression  | **0.982** |

Based on the evaluation results, **Logistic Regression** produced the best accuracy of **0.982**. Therefore, it was selected as the final model for the application.

---

## Experiment Tracking with MLflow

The experiments and model results are managed using **MLflow**.

MLflow is responsible for:

* Recording experiment parameters
* Tracking evaluation metrics
* Saving trained model artifacts
* Comparing different model runs
* Registering the selected model

### Final Registered Model

| Parameter       | Value               |
| --------------- | ------------------- |
| Registered Name | `BreastCancerModel` |
| Model Version   | `2`                 |
| Algorithm       | Logistic Regression |
| Accuracy        | `0.982`             |

---

## Dataset and DVC

**DVC (Data Version Control)** is incorporated to manage the dataset and maintain reproducibility of the ML pipeline.

The repository contains the following DVC-related components:

```text
.dvc/
.dvcignore
data/
```

The pipeline was verified using DVC, with the following status:

```text
Data and pipelines are up to date.
```

This helps ensure that the required data and pipeline stages remain synchronized.

---

## Prediction Service

The trained model is exposed through a **FastAPI** application.

The API provides a REST endpoint that accepts the required breast cancer feature values and returns the corresponding prediction.

### API Endpoint

```text
POST /predict
```

### Start the FastAPI Server

From the project directory, run:

```bash
uvicorn src.app:app --reload
```

The application will be available at:

```text
http://127.0.0.1:8000
```

### Interactive API Documentation

FastAPI automatically provides Swagger documentation.

Open:

```text
http://127.0.0.1:8000/docs
```

### Sample Prediction Output

```json
{
  "prediction": 1
}
```

---

## Containerization with Docker

Docker is used to package the application together with its required dependencies.

### Create the Docker Image

Run the following command from the project directory:

```bash
docker build -t capstone-mlops .
```

The `Dockerfile` defines the environment and instructions required to build the application image.

---

## Automated CI/CD

**GitHub Actions** is used to automate the development and deployment workflow.

The workflow is configured to execute when changes are pushed to the `main` branch.

### Workflow Stages

The automation performs tasks such as:

1. Checking out the project files
2. Configuring the Python environment
3. Installing required packages
4. Executing tests
5. Preparing the dataset
6. Training the ML model
7. Evaluating model performance
8. Creating the Docker image
9. Deploying the application

This automation helps maintain a consistent and reproducible ML development process.

---

## Running the Project

### Step 1 — Navigate to the Project

Open Command Prompt or PowerShell and execute:

```bash
cd "C:\Users\Skkir\OneDrive\Documents\Projects\DevOps session\Capstone\_MLOps\_Project"
```

### Step 2 — Install Required Packages

```bash
pip install -r requirements.txt
```

### Step 3 — Train the Model

```bash
python src/train.py
```

### Step 4 — Launch the Prediction API

```bash
uvicorn src.app:app --reload
```

### Step 5 — Access the API Documentation

Open the following address in your browser:

```text
http://127.0.0.1:8000/docs
```

---

## Repository Layout

```text
_MLOps_Project/
│
├── .dvc/
├── .github/
│   └── workflows/
│
├── data/
├── models/
├── mlartifacts/
│
├── src/
│   ├── app.py
│   ├── train.py
│   ├── predict.py
│   └── utils.py
│
├── tests/
│
├── Dockerfile
├── requirements.txt
├── mlflow.db
├── .dvcignore
└── README.md
```

---

## Technology Stack

| Technology     | Purpose                                    |
| -------------- | ------------------------------------------ |
| Python         | Application and ML development             |
| Scikit-learn   | Classification models                      |
| DVC            | Dataset and pipeline versioning            |
| MLflow         | Experiment tracking and model registration |
| FastAPI        | Prediction API                             |
| Docker         | Containerization                           |
| Git            | Version control                            |
| GitHub         | Source code hosting                        |
| GitHub Actions | CI/CD automation                           |

---

## Project Outcome

The project demonstrates how a machine learning model can be taken beyond model training and integrated into a reproducible MLOps workflow.

The final system combines **data versioning, model experimentation, model registration, API serving, containerization, and CI/CD automation** into a single workflow.
