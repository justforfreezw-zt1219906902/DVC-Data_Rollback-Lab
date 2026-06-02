# ⏪ DVC Data Rollback Lab: Version Control for Data & Models

## 📌 Scenario
You are a Machine Learning Engineer at a major tech firm. Your team maintains a production model that predicts employee salaries based on Experience and Education. 

Currently, the model is highly accurate (R² > 0.80). However, the data engineering team is about to push a new automated data ingestion pipeline. What happens if their new pipeline contains a bug and corrupts our dataset? 

If we only use `Git`, we are in trouble. Git is designed for text (code), not gigabytes of data or heavy `.pkl` model artifacts. If the data is corrupted and the model degrades, we need a way to "Time Travel" back to yesterday's healthy data and model.

## 🎯 Objective
In this lab, you will learn how to use **DVC (Data Version Control)** alongside **Git** and **AWS S3**. 
1. **V1 (Healthy State):** You will generate clean data, train a healthy model, and use DVC to push those heavy files to your AWS S3 Data Lake, while Git tracks the tiny `.dvc` pointer files.
2. **V2 (The Disaster):** You will simulate a pipeline failure, generate corrupted data, and accidentally save the degraded model.
3. **V3 (The Rollback):** You will use Git and DVC to execute an emergency rollback, pulling the healthy data and model back from AWS S3 to restore the production system.

## 🛠️ Files in this Repository
* `data_generator.py`: Generates the dataset. It has a hidden `--corrupt` flag to simulate a pipeline disaster.
* `train.py`: Trains a Linear Regression model and evaluates its health.
* `.gitignore`: Strictly prevents you from accidentally pushing `dataset.csv` or `model.pkl` to GitHub (forcing you to use DVC).
