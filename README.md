# **Coffee API Service Documentation**

## **Table of Contents**

1. [Overview](#overview)
2. [Prerequisites](#prerequisites)
3. [Infrastructure as Code (IaC) Setup](#infrastructure-as-code-iac-setup)
    - [Terraform Setup](#terraform-setup)
    - [Kubernetes Manifests](#kubernetes-manifests)
4. [Deployment Instructions](#deployment-instructions)
    - [Dockerizing the API](#dockerizing-the-api)
    - [Setting Up GitHub Actions CI/CD Pipeline](#setting-up-github-actions-cicd-pipeline)
    - [Deploying to Minikube](#deploying-to-minikube)
5. [Usage Instructions](#usage-instructions)
6. [Architectural Decisions and Trade-offs](#architectural-decisions-and-trade-offs)
7. [Conclusion](#conclusion)

---

## **1. Overview**

The Coffee API Service is a RESTful API designed to simulate a simple coffee-selling platform. Users can "purchase" different types of coffee based on the payment amount provided:

- **Espresso**: For payments less than $2.00.
- **Latte**: For payments between $2.00 and $3.00.
- **Cappuccino**: For payments of $3.00 or more.

The API is built using FastAPI and integrates with a PostgreSQL database to record transactions. Each transaction logs details such as the transaction ID, timestamp, payment amount, and the type of coffee served.

The service is containerized using Docker and deployed on a Kubernetes cluster via Minikube for local development. Deployment and management are automated through GitHub Actions, ensuring that the service is easy to maintain and scale.

---

## **2. Prerequisites**

Before deploying the Coffee API Service, ensure that you have the following installed and configured:

- **Git**: Version control system. [Git install](https://git-scm.com/download/linux)
- **Docker**: Containerization platform.
- **Terraform**: Infrastructure as Code tool.
- **Minikube**: Local Kubernetes cluster.
- **kubectl**: Kubernetes command-line tool.
- **GitHub account**: Required for creating repositories and running CI/CD pipelines.

---

## **3. Infrastructure as Code (IaC) Setup**

### **Terraform Setup**

1. **Clone the Infrastructure Repository**:
   ```bash
   git clone <infra-repo-url>
   cd infra
