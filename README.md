# Sales Inventory Admin (DevOps Project)

This repository hosts the code and configurations for a **web app store admin** designed to manage the sales and inventory of electronics products. The project adopts a comprehensive DevOps approach, leveraging modern tools and practices to ensure scalability, reliability, and maintainability.

---

## **Project Overview**

- **Frontend**: Built with Next.js and deployed as static files to AWS S3.
- **Backend**: Developed with Django, containerized using Docker, and deployed on an AWS EKS cluster.
- **Infrastructure**: Provisioned using Terraform, AWS services, and optionally CloudFormation.

---

## **Technology Stack**

### **Frontend**
- Framework: [Next.js](https://nextjs.org/)
- Deployment: AWS S3 (Static Website Hosting)

### **Backend**
- Framework: [Django](https://www.djangoproject.com/)
- Containerization: Docker
- Orchestration: AWS EKS (Elastic Kubernetes Service)
- Database: AWS RDS (PostgreSQL)

### **Infrastructure**
- IaC: [Terraform](https://www.terraform.io/) and AWS CloudFormation
- Secrets Management: AWS Secrets Manager and HashiCorp Vault
- Bastion Host: Managed with EC2
- Monitoring: Prometheus and Grafana

### **CI/CD**
- Pipeline: GitHub Actions

---

## **Repository Structure**

```
sales-inventory-admin/
├── frontend/
│   ├── nextjs-app/          # Next.js project for the admin frontend
│   ├── build/               # Build output to upload to S3
├── backend/
│   ├── django-app/          # Django project for the backend
│   ├── Dockerfile           # Dockerfile for containerizing the backend
│   ├── requirements.txt     # Dependencies for Django
├── infrastructure/
│   ├── terraform/           # Terraform configurations
│   ├── cloudformation/      # Optional CloudFormation templates
├── secrets-manager/         # Scripts/Docs for managing Secrets
├── bastion-host/            # Bastion host configurations
├── monitoring/              # Grafana/Prometheus configurations
├── .github/
│   ├── workflows/           # GitHub Actions CI/CD workflows
├── README.md
```

---

## **Setup Instructions**

### **1. Frontend**
- Navigate to `frontend/nextjs-app/` and install dependencies:
  ```bash
  npm install
  ```
- Build the static files:
  ```bash
  npm run build
  ```
- Deploy the build output to S3 using Terraform or AWS CLI.

### **2. Backend**
- Navigate to `backend/django-app/` and set up the Python environment:
  ```bash
  pip install -r requirements.txt
  ```
- Build the Docker image:
  ```bash
  docker build -t django-backend .
  ```
- Push the Docker image to AWS ECR:
  ```bash
  aws ecr create-repository --repository-name django-backend
  docker tag django-backend:latest <ECR_REPO_URI>
  docker push <ECR_REPO_URI>
  ```

### **3. Infrastructure**
- Navigate to `infrastructure/terraform/` and initialize Terraform:
  ```bash
  terraform init
  ```
- Provision resources:
  ```bash
  terraform apply
  ```

### **4. CI/CD**
- Configure GitHub Actions workflows in `.github/workflows/` to automate builds and deployments.

---

## **Best Practices**

- **Security**:
  - Use AWS Secrets Manager for managing sensitive information.
  - Apply least-privilege IAM roles for services and users.
- **Monitoring**:
  - Enable Prometheus and Grafana for observability.
  - Use CloudWatch for logging and AWS X-Ray for tracing.
- **Backup and Recovery**:
  - Automate RDS backups and S3 versioning with lifecycle policies.

---

## **Future Enhancements**

- Add support for multi-region deployment.
- Integrate automated testing in CI/CD pipelines.
- Implement caching with AWS ElastiCache (Redis).

---

## **License**
This project is licensed under the [MIT License](LICENSE).

---

## **Contributions**
Contributions are welcome! Please create an issue or submit a pull request.

