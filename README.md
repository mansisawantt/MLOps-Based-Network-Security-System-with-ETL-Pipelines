# MLOps-Based Network Security System with ETL Pipelines

[![GitHub license](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)  
[![AWS Deployment](https://img.shields.io/badge/AWS-Deployed-green)](#deployment-on-aws)  
[![Docker](https://img.shields.io/badge/Docker-Enabled-blue)](#docker-setup)  

## 🚀 Project Overview

The **MLOps-Based Network Security System** is an AI-driven cybersecurity solution that detects phishing attacks using a machine learning model. The project integrates ETL (Extract, Transform, Load) pipelines to process network data and deploys the model using **Docker** and **AWS Elastic Beanstalk**.

## 🔑 Key Features

- **Phishing Detection Model**: Uses **NLP-based techniques** to analyze network requests.
- **ETL Pipelines**: Extracts, transforms, and loads network security data efficiently.
- **MLOps Integration**: CI/CD pipeline using GitHub Actions & AWS ECR.
- **Docker & AWS Deployment**: Packaged with Docker and deployed on **AWS Elastic Beanstalk**.
- **FastAPI Backend**: Provides a REST API to interact with the model.

## 🏢 Project Architecture

```
📺 MLOps-Based-Network-Security-System
 ├ 📂 src
 ┃ ├ 📋 etl_pipeline.py
 ┃ ├ 📋 model_training.py
 ┃ ├ 📋 app.py  # FastAPI backend
 ├ 📂 docker
 ┃ ├ 📋 Dockerfile
 ├ 📂 .github/workflows
 ┃ ├ 📋 main.yml  # GitHub Actions CI/CD Pipeline
 ├ 📋 requirements.txt
 ├ 📋 README.md
 ├ 📋 LICENSE
```

## 🛠️ Setup & Installation

### 1️⃣ Clone the Repository

```bash
git clone https://github.com/mansisawantt/MLOps-Based-Network-Security-System-with-ETL-Pipelines.git
cd MLOps-Based-Network-Security-System-with-ETL-Pipelines
```

### 2️⃣ Install Dependencies

```bash
pip install -r requirements.txt
```

### 3️⃣ Run FastAPI Locally

```bash
uvicorn src.app:app --host 0.0.0.0 --port 8080
```

Then, open your browser and go to:

```
http://localhost:8080/docs
```

## 🐓 Docker Setup

### Build & Run the Docker Container

```bash
docker build -t networksecurity-mansi .
docker run -d -p 8080:8080 --name networksecurity networksecurity-mansi
```

## 🚀 Deployment on AWS

### 1️⃣ Push Docker Image to AWS ECR

```bash
aws ecr get-login-password --region us-east-1 | docker login --username AWS --password-stdin 182399695594.dkr.ecr.us-east-1.amazonaws.com
docker tag networksecurity-mansi:latest 182399695594.dkr.ecr.us-east-1.amazonaws.com/networksecurity-mansi:latest
docker push 182399695594.dkr.ecr.us-east-1.amazonaws.com/networksecurity-mansi:latest
```

### 2️⃣ Deploy on AWS Elastic Beanstalk

```bash
eb init -p docker networksecurity-mansi --region us-east-1
eb create networksecurity-env
```

## 📝 API Endpoints

| Method | Endpoint        | Description             |
|--------|----------------|-------------------------|
| GET    | `/`            | Check API health       |
| POST   | `/predict`     | Predict phishing links |

## 🔧 CI/CD Pipeline

- **GitHub Actions** automates Docker image building and pushes to **AWS ECR**.
- Deployment is triggered when new code is pushed to the `main` branch.

## 🐄 License

This project is licensed under the **MIT License**. See the [LICENSE](LICENSE) file for details.

## 💬 Contact

For any issues, please open a GitHub **issue** or contact me at:  
📧 Email: *mansisawant438@gmail.com*  
🔗 LinkedIn: [Mansi Sawant](https://www.linkedin.com/in/mansisawantt/)

