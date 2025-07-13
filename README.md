# 📦 Spam Email Classification - MLOps Pipeline with DVC and S3

This project implements a fully automated **MLOps pipeline** for a **Spam Email Classification** task using:

- ✅ **DVC (Data Version Control)** for data, pipeline, experiment, and metrics tracking  
- ☁️ **Amazon S3** as the remote backend for versioned data and models  
- ⚙️ **params.yaml** to centralize configuration and hyperparameters  
- 📊 **metrics.json** to log and visualize model performance  
- 📈 Reproducible pipelines with `dvc repro` and experiment tracking with `dvc exp`

---

## 📂 Project Structure

├── data/ # Data (tracked by DVC)
├── dvc.yaml # DVC pipeline stages
├── params.yaml # Central config for all stages
├── metrics.json # Model evaluation metrics
├── plots/ # DVC plots for metrics (optional)
├── src/ # Source scripts
│ ├── data_ingestion.py
│ ├── preprocessing.py
│ ├── feature_engineering.py
│ ├── model_training.py
│ ├── model_evaluation.py
├── .dvc/ # DVC internals
├── .gitignore
└── README.md # You're here!


## 🔄 MLOps Pipeline Flow (Automated with DVC)

The pipeline is modular and built using DVC stages:

1. **Data Ingestion** → Downloads or loads email dataset.
2. **Preprocessing** → Cleans and tokenizes text data.
3. **Feature Engineering** → Applies TF-IDF.
4. **Model Training** → Trains the spam classification model.
5. **Model Evaluation** → Evaluates performance and logs to `metrics.json`.

Each stage has:

- **Inputs** and **Outputs** declared in `dvc.yaml`
- **Parameters** pulled from `params.yaml`
- **Metrics** saved in `metrics.json`


Setting up your AWS S3 bucket
dvc remote add -d myremote s3://your-bucket-name/mlops-spam
dvc remote modify myremote endpointurl https://s3.YOUR-REGION.amazonaws.com
dvc remote modify myremote access_key_id <your-access-key>
dvc remote modify myremote secret_access_key <your-secret-key>
