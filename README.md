# 📝 Django Notes App

A simple Notes application built using **Django** and **React**, containerized with **Docker** and deployed using **Kubernetes**.

---

## 📌 Overview

This project demonstrates how to deploy a Django-based application using:
- Docker
- Kubernetes Namespace
- Kubernetes Deployment
- Kubernetes Service

The application can be run either using **Docker** or **Kubernetes**.

---

## ✅ Prerequisites

Make sure the following are installed:

- Docker
- Kubernetes (Kind)
- kubectl
- Git

---

## 🚀 Run Using Docker

### Clone the repository

```
git clone https://github.com/jsmaxso/django-notes-app.git
```

### Build Docker image
```
docker build -t notes-app:latest .
```
### Run the container
```
docker run -d -p 8000:8000 notes-app:latest
```
### Access the application
```
http://localhost:8000
```
---

## ☸️ Run Using Kubernetes ( KIND Cluster)

### Create a Kind cluster
```
kind create cluster --name notes-cluster

```
### Load Docker image into Kind cluster
```
kind load docker-image notes-app:latest --name notes-cluster

```
### Apply Kubernetes Namespace
```
kubectl apply -f k8s/namespace.yml
```
### Deploy the Application
```
kubectl apply -f k8s/deployment.yml

```
### Apply Service
```
kubectl apply -f k8s/service.yml

```
### Access the Application
Since Kind uses NodePort, use port-forwarding:
```
kubectl port-forward svc/notes-app-service 8000:8000 -n notes-app

```
Open in browser:
```
http://localhost:8000

```



