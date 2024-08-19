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

- [**Git**](https://git-scm.com/download/linux): Version control system.
- [**Docker**](https://docs.docker.com/engine/install/): Containerization platform.
- [**Terraform**](https://developer.hashicorp.com/terraform/tutorials/aws-get-started/install-cli): Infrastructure as Code tool.
- [**Minikube**](https://minikube.sigs.k8s.io/docs/start/?arch=%2Flinux%2Fx86-64%2Fstable%2Fbinary+download): Local Kubernetes cluster or you can use your Kubernetes cluster.
- [**kubectl**](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/): Kubernetes command-line tool.
- [**GitHub account**](https://docs.github.com/en/get-started/start-your-journey/creating-an-account-on-github): Required for creating repositories and running CI/CD pipelines. You can use your existing account.

---

## **3. Infrastructure as Code (IaC) Setup**

### **Terraform Setup**

1. **Clone the Infrastructure Repository**:
   ```bash
   git clone <infra-repo-url>
   cd infra

2. **Terraform Configuration**:

- **main.tf**: Automates the creation of a GitHub repository, sets up branch protection, and configures secrets and environment variables.
- **variables.tf**: Contains variables that you can change. Do not specify the database password and GitHub token to prevent leakage.

3. **Creating GitHub working repository in your account**:
  ```bash
  terraform init
  terraform apply
