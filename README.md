# Career Objective

Aspiring DevOps Engineer with experience in Docker, Kubernetes, Jenkins, Helm, Linux, and Cloud technologies. Seeking opportunities to build scalable, secure, and automated deployment pipelines while continuously improving infrastructure reliability and operational efficiency.

# SMAITIC DevOps Assignment

## Project Overview

This project demonstrates production-ready containerization, CI/CD pipeline design, and Kubernetes deployment practices for a Node.js application.

The application exposes:

* Main endpoint: `/`
* Health endpoint: `/health`

## Technology Stack

* Node.js
* Docker
* Jenkins
* Helm
* Kubernetes (AWS EKS Target)
* Linux

---

## Project Structure

smaitic-devops-assignment/

├── app/

│   ├── Dockerfile

│   ├── package.json

│   └── server.js

│

├── helm-chart/

│   ├── Chart.yaml

│   ├── values.yaml

│   └── templates/

│       ├── deployment.yaml

│       ├── service.yaml

│       ├── ingress.yaml

│       ├── configmap.yaml

│       ├── secret.yaml

│       └── hpa.yaml

│

├── Jenkinsfile

└── README.md

---

## Docker Improvements

The original Dockerfile was improved using the following practices:

* Replaced `node:latest` with `node:24-alpine`
* Implemented multi-stage build
* Added `.dockerignore`
* Added non-root user
* Added Docker HEALTHCHECK
* Added image metadata using LABEL
* Used `npm ci --omit=dev`
* Added health endpoint monitoring

---

## Jenkins Pipeline

Pipeline Stages:

1. Checkout
2. Validate Dockerfile
3. Build Docker Image
4. Docker Image Scan
5. Helm Lint
6. Helm Package
7. Deploy to AWS EKS

---

## Helm Chart Components

* Deployment
* Service
* Ingress
* ConfigMap
* Secret
* Horizontal Pod Autoscaler

The service port name requirement (`api-web`) has been implemented.

---

## Security Enhancements

* Non-root container execution
* Fixed image versioning
* Reduced attack surface
* Health monitoring
* Resource limits and requests
* Kubernetes readiness and liveness probes

---

## Build Instructions

Build Docker image:

docker build -t smaitic-api:v4 app/

Run container:

docker run -d -p 3001:3000 --name smaitic-container smaitic-api:v4

Verify application:

http://localhost:3001

Health endpoint:

http://localhost:3001/health

---

## Assumptions

* AWS EKS deployment stage is represented as a pipeline placeholder.
* Container image registry configuration is environment specific.
* Monitoring and logging integrations are outside the scope of this implementation.

---

## Conclusion

This solution demonstrates production-oriented DevOps practices including containerization, CI/CD automation design, Kubernetes deployment templating, security hardening, and operational readiness.
