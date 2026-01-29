🚀 End-to-End CI/CD Pipeline using GitHub Actions, Docker & Kubernetes
📌 Project Overview

This project demonstrates a complete CI/CD (Continuous Integration & Continuous Deployment) pipeline built from scratch.
The pipeline automates build, test, containerization, and deployment of a Python Flask application using modern DevOps tools.

This project is designed for beginners/freshers to understand real-world DevOps workflows.

🛠️ Tech Stack Used

Git & GitHub – Source code management

GitHub Actions – CI pipeline automation

Python (Flask) – Sample web application

PyTest – Automated testing

Docker – Containerization

Docker Hub – Docker image registry

Kubernetes (Minikube) – Application deployment & orchestration

🏗️ Project Architecture
Developer
   |
   |  (git push)
   v
GitHub Repository
   |
   |  GitHub Actions (CI)
   |  - Build
   |  - Test
   |  - Docker Image Build
   |  - Docker Image Push
   v
Docker Hub
   |
   |  (Manual CD)
   v
Kubernetes (Minikube)

📂 Project Structure
ci-cd-demo-project/
│
├── app.py
├── test_app.py
├── requirements.txt
├── Dockerfile
├── deployment.yaml
├── service.yaml
└── .github/
    └── workflows/
        └── cicd.yml

⚙️ CI/CD Workflow Explanation
🔹 Continuous Integration (CI)

Code is pushed to GitHub

GitHub Actions workflow is triggered

Dependencies are installed

Automated tests are executed using PyTest

Docker image is built

Docker image is pushed to Docker Hub

🔹 Continuous Deployment (CD)

Docker image is pulled from Docker Hub

Application is deployed on local Kubernetes cluster (Minikube)

Kubernetes Deployment manages Pods

Kubernetes Service exposes the application

⚠️ Deployment is done locally on Minikube because GitHub Actions runners cannot access local environments.

▶️ How to Run the Project (Local Setup)
1️⃣ Clone the Repository
git clone https://github.com/<your-username>/ci-cd-demo-project.git
cd ci-cd-demo-project

2️⃣ Run Application Locally
pip install -r requirements.txt
python app.py


Access:

http://localhost:5000

3️⃣ Build & Run Docker Container
docker build -t flask-ci-cd .
docker run -p 5000:5000 flask-ci-cd

4️⃣ Push Docker Image to Docker Hub
docker login
docker tag flask-ci-cd <docker-username>/flask-ci-cd:latest
docker push <docker-username>/flask-ci-cd:latest

5️⃣ Deploy on Kubernetes (Minikube)

Start Minikube:

minikube start


Apply Kubernetes manifests:

kubectl apply -f deployment.yaml
kubectl apply -f service.yaml


Check status:

kubectl get pods
kubectl get svc

6️⃣ Access the Application

Recommended method:

kubectl port-forward service/flask-service 5000:5000


Open browser:

http://localhost:5000

📘 Key Learnings

Writing CI pipelines using GitHub Actions

Secure secret management using GitHub Secrets

Docker image build and push automation

Kubernetes Deployments and Services

Debugging real-world Kubernetes networking issues

Understanding CI vs CD responsibilities

🚀 Future Improvements

Deploy to AWS EKS

Use Helm charts

Add SonarQube for code quality

Add Slack notifications

Implement rolling updates
