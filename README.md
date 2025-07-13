# 📦 Spam Email Classification - MLOps Pipeline with DVC and S3

This project implements a fully automated **MLOps pipeline** for a **Spam Email Classification** task using:

- ✅ **DVC (Data Version Control)** for data, pipeline, experiment, and metrics tracking  
- ☁️ **Amazon S3** as the remote backend for versioned data and models  
- ⚙️ **params.yaml** to centralize configuration and hyperparameters  
- 📊 **metrics.json** to log and visualize model performance  
- 📈 Reproducible pipelines with `dvc repro` and experiment tracking with `dvc exp`

---

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
1. dvc remote add -d myremote s3://your-bucket-name/mlops-spam
2. dvc remote modify myremote endpointurl https://s3.YOUR-REGION.amazonaws.com
3. dvc remote modify myremote access_key_id <your-access-key>
4. dvc remote modify myremote secret_access_key <your-secret-key>
