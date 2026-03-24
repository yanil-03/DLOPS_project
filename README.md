# 🧠 DLOps Image Classification Project

This project demonstrates an **end-to-end Deep Learning Operations (DLOps) pipeline** for an Image Classification system. It covers the complete lifecycle from **data ingestion to model deployment**, along with **DVC pipelines, CI/CD automation, Docker, and AWS deployment**.

---

## 🚀 What I Built

* End-to-end **CNN-based Image Classification pipeline**
* Modular pipeline structure using:

  * Components
  * Configuration
  * Entity classes
* **DVC pipeline** for reproducibility
* **CI/CD pipeline using GitHub Actions**
* **Dockerized application**
* Deployment on **AWS EC2 with ECR**

---

## 🏗️ Project Workflow

```text
Data Ingestion → Prepare Base Model → Prepare Callbacks → Training → Evaluation → Prediction → Deployment
```

---

## 📂 Project Structure

```text
DLOPS_project/
│
├── src/cnnClassifier/
│   ├── components/        # Data ingestion, training, evaluation, etc.
│   ├── pipeline/          # Pipeline stages
│   ├── entity/            # Config entity classes
│   ├── config/            # Configuration manager
│   ├── constants/         # Constants
│
├── config/                # config.yaml
├── research/              # Jupyter notebooks (experiments)
├── templates/             # HTML files (UI)
├── artifacts/             # Outputs (models, data)
├── dvc.yaml               # DVC pipeline
├── params.yaml            # Parameters
├── app.py                 # Flask/Streamlit app
├── main.py                # Pipeline runner
├── Dockerfile             # Docker setup
└── .github/workflows/     # CI/CD pipelines
```

---

## 🔄 Pipeline Stages

### 1. Data Ingestion

* Download dataset from GitHub (zip format)
* Extract and store in artifacts


### 2. Prepare Base Model

* Define CNN architecture
* Load pretrained weights (if used)

### 3. Prepare Callbacks

* Logging
* Checkpoints
* TensorBoard (if configured)

### 4. Model Training

* Train CNN model
* Save trained model

### 5. Model Evaluation

* Evaluate model performance
* Generate `score.json` (accuracy & loss)

### 6. Prediction Pipeline

* Upload image
* Predict class via web app

---

## 📊 DVC (Data Version Control)

Used for pipeline automation and reproducibility.

### Commands used:

```bash
dvc init
dvc repro
dvc dag
```

* `dvc.yaml` defines pipeline stages
* `dvc.lock` tracks execution
* Enables reproducible ML workflows

---

## 🐳 Docker

Application is containerized using Docker.

```bash
docker build -t dlops-app .
docker run -p 8080:8080 dlops-app
```

---

## 🔁 CI/CD Pipeline (GitHub Actions)

Implemented CI/CD using:

```
.github/workflows/main.yaml
```

### Workflow:

* Push code to GitHub
* Trigger GitHub Actions
* Build Docker image
* Push to AWS ECR
* Deploy on EC2 (self-hosted runner)

---

## ☁️ AWS Deployment

### Services Used:

* **EC2** → Hosting application
* **ECR** → Docker image storage
* **IAM** → Access management

### Steps:

1. Create IAM user with:

   * AmazonEC2FullAccess
   * AmazonEC2ContainerRegistryFullAccess
2. Create ECR repository
3. Launch EC2 instance (Ubuntu)
4. Install Docker
5. Configure EC2 as self-hosted runner
6. Add GitHub secrets:

   * AWS_ACCESS_KEY_ID
   * AWS_SECRET_ACCESS_KEY
   * AWS_REGION
   * AWS_ECR_LOGIN_URI
   * ECR_REPOSITORY_NAME
7. Run CI/CD pipeline

---

## 🧪 Run Locally

```bash
git clone https://github.com/yanil-03/DLOPS_project.git
cd DLOPS_project

python -m venv venv
venv\Scripts\activate   # Windows

pip install -r requirements.txt

python main.py
python app.py
```

---

## 🌐 Web App

* Upload image
* Click **Predict**
* Get classification result

---

## 🔥 Key Learnings

* End-to-end ML pipeline design
* DVC for experiment tracking
* CI/CD automation with GitHub Actions
* Docker containerization
* AWS deployment with EC2 + ECR
* Self-hosted runners setup

---

## ⚠️ Notes

* Dataset is stored externally (GitHub zip)
* AWS resources should be deleted after use to avoid charges:

  * EC2 instance
  * ECR repository
  * IAM user

---

## 👨‍💻 Author

**Yanil Kumawat**
GitHub: https://github.com/yanil-03

---

## ⭐ If you like this project

* Star ⭐ the repo
* Fork 🍴 it
* Share 📢 it

---
