# 🚀 Three-Tier Web Application on AWS EKS
**Created by Vineet Chaudhari**

## 📋 Project Overview

This project demonstrates a **complete three-tier web application** deployed on **Amazon Elastic Kubernetes Service (EKS)** using **Infrastructure as Code (IaC)**. It showcases modern cloud-native development practices and DevOps principles that I've implemented to create a scalable, production-ready application.

### 🏗️ What is a Three-Tier Architecture?

A three-tier architecture separates an application into three logical layers:

1. **🖥️ Presentation Tier (Frontend)** - User Interface built with React.js
2. **⚙️ Application Tier (Backend)** - Business logic API built with Node.js/Express
3. **🗄️ Data Tier (Database)** - Data storage using MongoDB

### 🌟 Key Features

- **Container Orchestration**: Kubernetes deployment on AWS EKS
- **Infrastructure as Code**: Terraform for AWS resource provisioning  
- **Auto Scaling**: Horizontal Pod Autoscaler and Cluster Autoscaler
- **Load Balancing**: AWS Application Load Balancer integration
- **Monitoring**: Grafana dashboards for observability
- **High Availability**: Multi-AZ deployment with fault tolerance

## 🛠️ Technology Stack

| Layer | Technology | Purpose |
|-------|------------|---------|
| **Frontend** | React.js, Material-UI | User interface and user experience |
| **Backend** | Node.js, Express.js | REST API and business logic |
| **Database** | MongoDB | Data persistence and storage |
| **Container** | Docker | Application containerization |
| **Orchestration** | Kubernetes (EKS) | Container management and scaling |
| **Infrastructure** | Terraform | Infrastructure provisioning |
| **Cloud Provider** | AWS | Hosting and managed services |
| **Monitoring** | Grafana, Prometheus | Application and infrastructure monitoring |

## 📁 Project Structure

```
three-tier-eks-iac/
├── app/
│   ├── frontend/          # React.js application
│   │   ├── src/
│   │   ├── public/
│   │   ├── Dockerfile
│   │   └── package.json
│   └── backend/           # Node.js API server
│       ├── models/
│       ├── routes/
│       ├── Dockerfile
│       └── package.json
├── terraform/             # Infrastructure as Code
│   ├── eks.tf            # EKS cluster configuration
│   ├── vpc.tf             # Network configuration
│   ├── autoscaler-*.tf    # Auto-scaling setup
│   └── variables.tf
├── k8s_manifests/         # Kubernetes deployment files
│   ├── frontend-*.yaml
│   ├── backend-*.yaml
│   ├── mongo/
│   └── full_stack_lb.yaml
└── README.md
```

## 🔧 Prerequisites & Setup

### Required Tools Installation

Before starting, ensure you have the following tools installed:

#### 1. **AWS CLI v2**
```bash
# Download and install from: https://aws.amazon.com/cli/
# Verify installation
aws --version
```

#### 2. **kubectl (Kubernetes CLI)**
```bash
# Installation guide: https://kubernetes.io/docs/tasks/tools/
# Verify installation
kubectl version --client
```

#### 3. **Helm Package Manager**
```bash
# Installation guide: https://helm.sh/docs/intro/install/
# After installation, update repos
helm repo update
```

#### 4. **Terraform**
```bash
# Download from: https://www.terraform.io/downloads.html
# Verify installation
terraform version
```

#### 5. **Docker**
```bash
# Download from: https://www.docker.com/products/docker-desktop
# Verify installation
docker --version
```

### AWS Configuration

1. **Configure AWS credentials:**
```bash
aws configure
# Enter your AWS Access Key ID, Secret Access Key, Region, and Output format
```

2. **Verify AWS access:**
```bash
aws sts get-caller-identity
```

## 🚀 Deployment Guide

### Step 1: Infrastructure Provisioning with Terraform

```bash
# Navigate to terraform directory
cd terraform/

# Initialize Terraform
terraform init

# Review the infrastructure plan
terraform plan

# Apply the infrastructure
terraform apply
# Type 'yes' when prompted
```

**What this creates:**
- VPC with public/private subnets
- EKS cluster with managed node groups
- IAM roles and policies
- Security groups
- Auto-scaling configurations

### Step 2: Configure kubectl

```bash
# Update kubeconfig to connect to your EKS cluster
aws eks update-kubeconfig --name my-eks-cluster --region us-west-2

# Verify cluster access
kubectl auth can-i "*" "*"
kubectl get nodes
```

### Step 3: Build and Push Docker Images

#### For your ECR repository (replace with your own ECR URL):

**Frontend Image:**
```bash
# Navigate to frontend directory
cd app/frontend/

# Build for different platforms
# For Mac (Apple Silicon):
docker buildx build --platform linux/amd64 -t vineet-task-frontend:v1 .

# For Linux/Windows:
docker build -t vineet-task-frontend:v1 .

# Tag and push to your container registry
docker tag vineet-task-frontend:v1 YOUR_ECR_URI/vineet-task-frontend:v1
docker push YOUR_ECR_URI/vineet-task-frontend:v1
```

**Backend Image:**
```bash
# Navigate to backend directory
cd app/backend/

# Build the image
docker build -t vineet-task-backend:v1 .

# Tag and push to your container registry
docker tag vineet-task-backend:v1 YOUR_ECR_URI/vineet-task-backend:v1
docker push YOUR_ECR_URI/vineet-task-backend:v1
```

### Step 4: Deploy Application to Kubernetes

#### Create Namespace
```bash
# Create a dedicated namespace for our application
kubectl create namespace vineet-task-app

# Set the namespace as default for current context
kubectl config set-context --current --namespace vineet-task-app
```

#### Deploy Database (MongoDB)
```bash
cd k8s_manifests/mongo/

# Apply MongoDB configurations in order
kubectl apply -f secrets.yaml      # Database credentials
kubectl apply -f deploy.yaml       # MongoDB deployment
kubectl apply -f service.yaml      # MongoDB service
```

#### Deploy Backend API
```bash
cd ../

# Deploy Node.js backend
kubectl apply -f backend-deployment.yaml
kubectl apply -f backend-service.yaml
```

#### Deploy Frontend
```bash
# Deploy React frontend
kubectl apply -f frontend-deployment.yaml
kubectl apply -f frontend-service.yaml
```

#### Deploy Load Balancer
```bash
# Create Application Load Balancer for external access
kubectl apply -f full_stack_lb.yaml
```

### Step 5: Verify Deployment

```bash
# Check all pods are running
kubectl get pods

# Check services
kubectl get services

# Check deployments
kubectl get deployments

# Get load balancer URL
kubectl get ingress
# or
kubectl get service -o wide
```

## 📊 Monitoring & Troubleshooting

### Check Application Logs
```bash
# Backend logs
kubectl logs -f deployment/backend-deployment

# Frontend logs
kubectl logs -f deployment/frontend-deployment

# MongoDB logs
kubectl logs -f deployment/mongo-deployment
```

### Verify Auto Scaling
```bash
# Check cluster autoscaler
kubectl get pods -n kube-system | grep cluster-autoscaler

# Check autoscaler logs
kubectl logs -f -n kube-system -l app=cluster-autoscaler
```

### Check Load Balancer Controller
```bash
# Verify AWS Load Balancer Controller
kubectl logs -f -n kube-system -l app.kubernetes.io/name=aws-load-balancer-controller
```

## 📈 Grafana Monitoring Setup

### Access Grafana Dashboard
```bash
# Forward Grafana port (if deployed)
kubectl port-forward service/grafana 3000:80
```

**Default Credentials:**
- Username: `admin`
- Password: `prom-operator`

**Recommended Dashboard ID:** `1860` (Node Exporter Full)

**Explore more dashboards:** https://grafana.com/grafana/dashboards/

## 🧹 Cleanup Resources

### Remove Kubernetes Resources
```bash
# Delete application resources
kubectl delete namespace vineet-task-app

# Delete other namespaces if created
kubectl delete namespace monitoring
```

### Destroy Infrastructure
```bash
cd terraform/

# Destroy all AWS resources
terraform destroy
# Type 'yes' when prompted
```

## 🔒 Security Best Practices

- ✅ Use IAM roles instead of hardcoded credentials
- ✅ Enable VPC endpoints for secure communication
- ✅ Implement network policies for pod-to-pod communication
- ✅ Use Kubernetes secrets for sensitive data
- ✅ Enable cluster logging and monitoring
- ✅ Regularly update container images and Kubernetes versions

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add some amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- AWS EKS Documentation
- Terraform AWS Provider
- Kubernetes Community
- React.js and Node.js Communities

---#   T h r e e - T i e r - A W S - E K S - I A C - p r o j e c t -  
 