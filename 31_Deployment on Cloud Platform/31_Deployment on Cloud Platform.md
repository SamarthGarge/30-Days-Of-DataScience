[<< Day 30](../30_Building%20a%20Data%20Science%20Pipeline/30_Building%20a%20Data%20Science%20Pipeline.md)  |

# 🎉 Bonus Day 31: Deployment on Cloud Platform

Welcome to **Bonus Day 31** of the 30 Days of Data Science series! 🎉 Today, we’ll explore how to deploy your machine learning models or applications to **Cloud Platforms** using **Flask/FastAPI**. By the end, you'll understand the steps to deploy to **AWS**, **Azure**, and **GCP**.



## 📜 Table of Contents

- [🎉 Bonus Day 31: Deployment on Cloud Platform](#-bonus-day-31-deployment-on-cloud-platform)
  - [📜 Table of Contents](#-table-of-contents)
  - [🌐 Introduction](#-introduction)
  - [🚀 Preparing the Application for Deployment](#-preparing-the-application-for-deployment)
  - [⚙️ Deploying with Flask/FastAPI](#%EF%B8%8F-deploying-with-flaskfastapi)
    - [Flask Example](#flask-example)
    - [FastAPI Example](#fastapi-example)
  - [☁️ Deployment on AWS](#%EF%B8%8F-deployment-on-aws)
    - [Steps to Deploy](#steps-to-deploy)
  - [☁️ Deployment on Azure](#%EF%B8%8F-deployment-on-azure)
    - [Steps to Deploy](#steps-to-deploy-1)
  - [☁️ Deployment on GCP](#%EF%B8%8F-deployment-on-gcp)
    - [Steps to Deploy](#steps-to-deploy-2)
  - [📝 Practice Exercise](#-practice-exercise)
  - [📚 Summary](#-summary)



## 🌐 Introduction

Deployment is a crucial step in bringing your data science project to life. It allows others to interact with your model or application in real-time. We'll focus on deploying applications using **Flask** or **FastAPI** to popular cloud platforms like:

- **AWS (Amazon Web Services)**
- **Azure**
- **GCP (Google Cloud Platform)**



## 🚀 Preparing the Application for Deployment

### Basic Folder Structure
Ensure your project folder is structured properly:

```plaintext
project/
|-- app.py  # Main application script
|-- model.pkl  # Serialized ML model (if applicable)
|-- templates/
|    |-- index.html  # Frontend files (if needed)
|-- requirements.txt  # Python dependencies
|-- Dockerfile  # (Optional) Docker configuration
```

### Creating `requirements.txt`
List all dependencies in a `requirements.txt` file:

```plaintext
Flask==2.1.2
pandas==1.5.3
numpy==1.23.5
scikit-learn==1.1.3
```
Generate automatically:

```bash
pip freeze > requirements.txt
```



## ⚙️ Deploying with Flask/FastAPI

### Flask Example

Here’s a minimal **Flask** application:

```python
from flask import Flask, request, jsonify

app = Flask(__name__)

@app.route("/", methods=["GET"])
def home():
    return "Welcome to the Flask Deployment!"

@app.route("/predict", methods=["POST"])
def predict():
    data = request.json
    prediction = sum(data["values"])  # Example prediction logic
    return jsonify({"prediction": prediction})

if __name__ == "__main__":
    app.run(debug=True)
```

Run locally:

```bash
python app.py
```

### FastAPI Example

Here’s a minimal **FastAPI** application:

```python
from fastapi import FastAPI
from pydantic import BaseModel

app = FastAPI()

class InputData(BaseModel):
    values: list[int]

@app.get("/")
def home():
    return {"message": "Welcome to FastAPI Deployment!"}

@app.post("/predict")
def predict(data: InputData):
    prediction = sum(data.values)  # Example prediction logic
    return {"prediction": prediction}

if __name__ == "__main__":
    import uvicorn
    uvicorn.run(app, host="0.0.0.0", port=8000)
```

Run locally:

```bash
uvicorn app:app --reload
```



## ☁️ Deployment on AWS

### Steps to Deploy

1. **Set Up an EC2 Instance:**
   - Go to the [AWS Management Console](https://aws.amazon.com/).
   - Launch an EC2 instance with an Ubuntu AMI.

2. **Install Dependencies on EC2:**
   SSH into the instance and set up the environment:

   ```bash
   sudo apt update && sudo apt upgrade
   sudo apt install python3-pip
   pip3 install -r requirements.txt
   ```

3. **Run the Application:**
   
   ```bash
   python3 app.py
   ```

4. **Expose the Application:**
   - Open port 5000 (or your application port) in the AWS security group.
   - Access the app using the public IP of the EC2 instance.



## ☁️ Deployment on Azure

### Steps to Deploy

1. **Set Up an App Service:**
   - Go to the [Azure Portal](https://portal.azure.com/).
   - Create an App Service and select a Python runtime.

2. **Deploy Code:**
   - Zip your project folder and upload it through the Azure portal.

3. **Configure Startup Command:**
   Add the following startup command in the portal:

   ```bash
   gunicorn -w 4 -k uvicorn.workers.UvicornWorker app:app
   ```

4. **Access the Application:**
   - Use the App Service URL provided by Azure.



## ☁️ Deployment on GCP

### Steps to Deploy

1. **Set Up a Google Cloud Project:**
   - Go to the [GCP Console](https://console.cloud.google.com/).
   - Enable the App Engine API.

2. **Create an `app.yaml` File:**

   ```yaml
   runtime: python39
   entrypoint: gunicorn -w 4 -k uvicorn.workers.UvicornWorker app:app
   ```

3. **Deploy the Application:**

   ```bash
   gcloud app deploy
   ```

4. **Access the Application:**
   - Use the provided GCP URL.



## 📝 Practice Exercise

1. Create a Flask/FastAPI application that:
   - Accepts an input text.
   - Returns the sentiment (positive/negative) using a pre-trained model.

2. Deploy this application to any cloud platform of your choice.



## 📚 Summary

In this bonus session, we learned how to:

- Prepare a Flask/FastAPI application for deployment.
- Deploy to **AWS EC2**, **Azure App Service**, and **Google Cloud Platform**.
- Configure cloud platforms and expose services to the internet.

🎉 Congratulations on completing the **30 Days of Data Science** series with this bonus day! You’re now equipped to deploy your projects to the world. 🌎

---


