# Life Insurance Claim Fraud Detection

## Project Structure

```Plaintext

life-insurance-claim-fraud-detection/
│
├── assets/                    # Images and diagrams for the README
│   └── architecture_diagram.png   
│
├── data/                      # 🥇 Medallion Architecture (Data Lakehouse Concept)
│   ├── bronze/                    # Raw Data: Unprocessed data ingested from AWS S3
│   ├── silver/                    # Cleaned Data: Cleansed, filtered, and feature-engineered data
│   └── gold/                      # Business-level Data: Final predictions ready for BI Dashboards
│
├── notebooks/                 # Databricks execution workflows
│   ├── data_ingestion.ipynb         # Ingests data from S3 to the Bronze layer
│   ├── eda_and_silver_prep.ipynb    # Data cleaning and feature engineering (saves to Silver)
│   ├── model_training_mlflow.ipynb  # Trains the model, tracks experiments via MLflow, and registers the model
│   └── batch_inference.ipynb        # 🚀 (Deployment) Loads the production model to score new daily claims
│
├── src/                       # Source Code (Modular Programming for scalability)
│   ├── __init__.py
│   ├── config.py                  # Environment variables and configurations (e.g., S3 paths, MLflow experiment names)
│   ├── data_processing.py         # PySpark functions for handling missing values and data cleaning
│   ├── feature_engineering.py     # Functions for feature transformations (StringIndexer, VectorAssembler)
│   ├── train.py                   # The core Random Forest training pipeline
│   └── inference.py               # Functions to load the MLflow model and generate predictions
│
├── tests/                     # Automated Testing (Evaluation Frameworks & Software Reliability)
│   ├── __init__.py
│   ├── test_data_processing.py    # Pytest script to ensure no null values exist before training
│   └── test_model.py              # Pytest script to verify model outputs (e.g., ensuring binary 0 or 1 output)
│
├── deployment/                # Automation and Job Scheduling
│   └── databricks_job_config.json # Configuration file for Databricks Workflows (Automated daily batch jobs)
│
├── .gitignore                 # Prevents pushing sensitive data and environment files to GitHub
├── requirements.txt           # List of dependencies (e.g., pyspark, mlflow, pytest)
└── README.md                  # Comprehensive project documentation

```