# 🚀 Three-Tier Web Application on AWS EKS
**Created by Vineet Chaudhari**

[![AWS](https://img.shields.io/badge/AWS-Cloud-orange)](https://aws.amazon.com/)
[![Kubernetes](https://img.shields.io/badge/Kubernetes-EKS-blue)](https://kubernetes.io/)
[![Terraform](https://img.shields.io/badge/Terraform-IaC-purple)](https://terraform.io/)
[![Docker](https://img.shields.io/badge/Docker-Containerization-blue)](https://docker.com/)
[![React](https://img.shields.io/badge/React-Frontend-61DAFB)](https://reactjs.org/)
[![Node.js](https://img.shields.io/badge/Node.js-Backend-green)](https://nodejs.org/)

## 📋 Project Overview

This project demonstrates a **complete three-tier web application** deployed on **Amazon Elastic Kubernetes Service (EKS)** using **Infrastructure as Code (IaC)**. It showcases modern cloud-native development practices and DevOps principles that I've implemented to create a scalable, production-ready application.

## 🎯 Learning Objectives

By the end of this project, you will understand:
- ✅ **Three-tier architecture** design patterns
- ✅ **Containerization** with Docker
- ✅ **Kubernetes orchestration** on AWS EKS
- ✅ **Infrastructure as Code** with Terraform
- ✅ **Auto-scaling** and load balancing
- ✅ **CI/CD pipeline** concepts
- ✅ **Cloud-native** monitoring and observability

## 🏗️ Architecture Deep Dive

### What is a Three-Tier Architecture?

A three-tier architecture is a software design pattern that separates applications into three logical and physical computing tiers:

```
┌─────────────────────────────────────────────────────────────┐
│                    🌐 Internet Users                        │
└─────────────────┬───────────────────────────────────────────┘
                  │
                  ▼
┌─────────────────────────────────────────────────────────────┐
│           🖥️  PRESENTATION TIER (Frontend)                 │
│                                                             │
│  • React.js Application                                     │
│  • Material-UI Components                                   │
│  • User Interface & Experience                              │
│  • Runs in Web Browser                                      │
│                                                             │
└─────────────────┬───────────────────────────────────────────┘
                  │ HTTP/HTTPS Requests
                  ▼
┌─────────────────────────────────────────────────────────────┐
│            ⚙️  APPLICATION TIER (Backend)                  │
│                                                             │
│  • Node.js + Express.js API                                │
│  • Business Logic Processing                                │
│  • Authentication & Authorization                           │
│  • Data Validation & Processing                             │
│                                                             │
└─────────────────┬───────────────────────────────────────────┘
                  │ Database Queries
                  ▼
┌─────────────────────────────────────────────────────────────┐
│             🗄️  DATA TIER (Database)                      │
│                                                             │
│  • MongoDB Database                                         │
│  • Data Storage & Retrieval                                │
│  • Data Persistence                                         │
│  • CRUD Operations                                          │
│                                                             │
└─────────────────────────────────────────────────────────────┘
```

### 🌟 Key Features & Benefits

| Feature | Description | Benefit |
|---------|-------------|---------|
| **🔄 Auto Scaling** | Horizontal Pod Autoscaler (HPA) & Cluster Autoscaler (CA) | Handles traffic spikes automatically |
| **🌍 Load Balancing** | AWS Application Load Balancer (ALB) | Distributes traffic evenly |
| **📊 Monitoring** | Grafana + Prometheus integration | Real-time performance insights |
| **🔒 Security** | IAM roles, VPC, Security Groups | Enterprise-grade security |
| **💰 Cost Optimization** | Spot instances, auto-scaling | Reduces infrastructure costs |
| **🚀 High Availability** | Multi-AZ deployment | 99.9% uptime guarantee |
| **📦 Containerization** | Docker containers | Consistent deployment across environments |
| **🏗️ Infrastructure as Code** | Terraform automation | Reproducible, version-controlled infrastructure |

## 🛠️ Technology Stack Explained

### Frontend Layer
- **React.js**: A JavaScript library for building user interfaces
- **Material-UI**: React components implementing Google's Material Design
- **Axios**: HTTP client for making API requests

### Backend Layer  
- **Node.js**: JavaScript runtime for server-side development
- **Express.js**: Fast, minimalist web framework for Node.js
- **CORS**: Cross-Origin Resource Sharing for API access

### Database Layer
- **MongoDB**: NoSQL document database for flexible data storage

### Infrastructure & DevOps
- **AWS EKS**: Managed Kubernetes service
- **Terraform**: Infrastructure as Code tool
- **Docker**: Containerization platform
- **Kubernetes**: Container orchestration platform
- **AWS ALB**: Application Load Balancer for traffic distribution

## 📁 Project Structure Detailed

```
Three-Tier-AWS-EKS-IAC-Project/
│
├── 📱 app/                              # Application source code
│   ├── 🎨 frontend/                     # React.js application
│   │   ├── src/
│   │   │   ├── App.js                   # Main React component
│   │   │   ├── Tasks.js                 # Task management component
│   │   │   └── services/
│   │   │       └── taskServices.js     # API service calls
│   │   ├── public/                      # Static assets
│   │   ├── Dockerfile                   # Frontend container config
│   │   └── package.json                 # Frontend dependencies
│   │
│   └── ⚙️ backend/                      # Node.js API server
│       ├── models/
│       │   └── task.js                  # MongoDB data model
│       ├── routes/
│       │   └── tasks.js                 # API route handlers
│       ├── index.js                     # Server entry point
│       ├── db.js                        # Database connection
│       ├── Dockerfile                   # Backend container config
│       └── package.json                 # Backend dependencies
│
├── 🏗️ terraform/                        # Infrastructure as Code
│   ├── eks.tf                          # EKS cluster configuration
│   ├── vpc.tf                          # Network infrastructure
│   ├── iam.tf                          # Identity & Access Management
│   ├── autoscaler-*.tf                 # Auto-scaling configuration
│   ├── monitoring.tf                   # Grafana/Prometheus setup
│   └── variables.tf                    # Terraform variables
│
├── ☸️ k8s_manifests/                    # Kubernetes deployment files
│   ├── frontend-deployment.yaml        # Frontend pods configuration
│   ├── frontend-service.yaml           # Frontend service exposure
│   ├── backend-deployment.yaml         # Backend pods configuration
│   ├── backend-service.yaml            # Backend service exposure
│   ├── full_stack_lb.yaml              # Load balancer configuration
│   └── mongo/                          # MongoDB deployment
│       ├── deploy.yaml                 # MongoDB deployment
│       ├── service.yaml                # MongoDB service
│       └── secrets.yaml                # Database credentials
│
└── 📚 README.md                         # This comprehensive guide
```

## 🔧 Prerequisites & Setup Guide

### 🎯 What You Need to Know
- **Basic understanding of**: Command line interface (CLI)
- **Familiarity with**: Cloud computing concepts
- **Optional but helpful**: Docker, Kubernetes, AWS basics

### 💻 Required Tools Installation

#### 1. **AWS CLI v2** (Amazon Web Services Command Line Interface)
**What it does**: Allows you to interact with AWS services from your terminal

**Installation:**
```bash
# Windows (using MSI installer)
# Download from: https://awscli.amazonaws.com/AWSCLIV2.msi

# macOS
curl "https://awscli.amazonaws.com/AWSCLIV2.pkg" -o "AWSCLIV2.pkg"
sudo installer -pkg AWSCLIV2.pkg -target /

# Linux
curl "https://awscli.amazonaws.com/awscli-exe-linux-x86_64.zip" -o "awscliv2.zip"
unzip awscliv2.zip
sudo ./aws/install

# Verify installation
aws --version
```

#### 2. **kubectl** (Kubernetes Command Line Tool)
**What it does**: Controls Kubernetes clusters and manages containerized applications

**Installation:**
```bash
# Windows (using Chocolatey)
choco install kubernetes-cli

# macOS (using Homebrew)
brew install kubectl

# Linux
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
sudo install -o root -g root -m 0755 kubectl /usr/local/bin/kubectl

# Verify installation
kubectl version --client
```

#### 3. **Helm** (Kubernetes Package Manager)
**What it does**: Simplifies deployment and management of Kubernetes applications

**Installation:**
```bash
# Windows (using Chocolatey)
choco install kubernetes-helm

# macOS (using Homebrew)
brew install helm

# Linux
curl https://raw.githubusercontent.com/helm/helm/main/scripts/get-helm-3 | bash

# Update repositories after installation
helm repo update

# Verify installation
helm version
```

#### 4. **Terraform** (Infrastructure as Code Tool)
**What it does**: Builds, changes, and versions infrastructure safely and efficiently

**Installation:**
```bash
# Windows (using Chocolatey)
choco install terraform

# macOS (using Homebrew)
brew install terraform

# Linux (Ubuntu/Debian)
wget -O- https://apt.releases.hashicorp.com/gpg | sudo gpg --dearmor -o /usr/share/keyrings/hashicorp-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/hashicorp-archive-keyring.gpg] https://apt.releases.hashicorp.com $(lsb_release -cs) main" | sudo tee /etc/apt/sources.list.d/hashicorp.list
sudo apt update && sudo apt install terraform

# Verify installation
terraform --version
```

#### 5. **Docker** (Containerization Platform)
**What it does**: Packages applications and their dependencies into containers

**Installation:**
```bash
# Download Docker Desktop from: https://www.docker.com/products/docker-desktop

# After installation, verify
docker --version
docker run hello-world
```

### 🔑 AWS Account Setup

#### Step 1: Create AWS Account
1. Go to [AWS Console](https://aws.amazon.com/)
2. Click "Create an AWS Account"
3. Follow the registration process
4. **Note**: You'll need a credit card, but we'll use free tier resources

#### Step 2: Create IAM User
1. Go to **IAM Console** → **Users** → **Add User**
2. Username: `eks-admin`
3. Access type: **Programmatic access**
4. Attach policies:
   - `AmazonEKSClusterPolicy`
   - `AmazonEKSWorkerNodePolicy`
   - `AmazonEKS_CNI_Policy`
   - `AmazonEC2ContainerRegistryReadOnly`
   - `EC2InstanceProfileForImageBuilder`

#### Step 3: Configure AWS CLI
```bash
# Configure AWS credentials
aws configure

# You'll be prompted for:
# AWS Access Key ID: [Enter your access key]
# AWS Secret Access Key: [Enter your secret key]
# Default region name: us-west-2
# Default output format: json

# Verify configuration
aws sts get-caller-identity
```

## 🚀 Complete Deployment Guide

### Phase 1: Infrastructure Provisioning with Terraform

**What we're doing**: Creating the foundational AWS infrastructure including VPC, EKS cluster, and supporting services.

```bash
# Step 1: Navigate to terraform directory
cd terraform/

# Step 2: Initialize Terraform (downloads required providers)
terraform init

# Step 3: Validate configuration files
terraform validate

# Step 4: Preview what will be created
terraform plan

# Step 5: Create the infrastructure
terraform apply
# When prompted, type: yes
```

**⏱️ Expected time**: 15-20 minutes

**What gets created**:
- ✅ VPC with public/private subnets across multiple AZs
- ✅ Internet Gateway and NAT Gateways
- ✅ EKS cluster with managed node groups
- ✅ IAM roles and security groups
- ✅ Auto Scaling Groups
- ✅ Load Balancer Controller

### Phase 2: Kubernetes Cluster Configuration

**What we're doing**: Connecting to our EKS cluster and verifying it's working correctly.

```bash
# Step 1: Update kubeconfig to connect to EKS cluster
aws eks update-kubeconfig --name my-eks-cluster --region us-west-2

# Step 2: Verify cluster connection
kubectl cluster-info

# Step 3: Check cluster nodes
kubectl get nodes

# Step 4: Verify you have admin access
kubectl auth can-i "*" "*"
# Should return "yes"

# Step 5: Check system pods are running
kubectl get pods -n kube-system
```

### Phase 3: Container Registry Setup

**What we're doing**: Creating a place to store our Docker images that Kubernetes can access.

#### Option A: Using Amazon ECR (Recommended)

```bash
# Step 1: Create ECR repositories
aws ecr create-repository --repository-name vineet-task-frontend --region us-west-2
aws ecr create-repository --repository-name vineet-task-backend --region us-west-2

# Step 2: Get login token for ECR
aws ecr get-login-password --region us-west-2 | docker login --username AWS --password-stdin YOUR_ACCOUNT_ID.dkr.ecr.us-west-2.amazonaws.com

# Step 3: Note down your ECR URLs
echo "Frontend ECR: YOUR_ACCOUNT_ID.dkr.ecr.us-west-2.amazonaws.com/vineet-task-frontend"
echo "Backend ECR: YOUR_ACCOUNT_ID.dkr.ecr.us-west-2.amazonaws.com/vineet-task-backend"
```

#### Option B: Using Docker Hub (Alternative)

```bash
# Step 1: Login to Docker Hub
docker login

# Step 2: Use these image names:
# Frontend: your-dockerhub-username/vineet-task-frontend:v1
# Backend: your-dockerhub-username/vineet-task-backend:v1
```

### Phase 4: Building and Pushing Docker Images

**What we're doing**: Converting our applications into Docker containers and uploading them to our registry.

#### Frontend Application

```bash
# Step 1: Navigate to frontend directory
cd app/frontend/

# Step 2: Build Docker image
# For Mac (Apple Silicon M1/M2):
docker buildx build --platform linux/amd64 -t vineet-task-frontend:v1 .

# For Linux/Windows/Intel Mac:
docker build -t vineet-task-frontend:v1 .

# Step 3: Tag for your registry
# For ECR:
docker tag vineet-task-frontend:v1 YOUR_ACCOUNT_ID.dkr.ecr.us-west-2.amazonaws.com/vineet-task-frontend:v1

# For Docker Hub:
docker tag vineet-task-frontend:v1 your-dockerhub-username/vineet-task-frontend:v1

# Step 4: Push to registry
# For ECR:
docker push YOUR_ACCOUNT_ID.dkr.ecr.us-west-2.amazonaws.com/vineet-task-frontend:v1

# For Docker Hub:
docker push your-dockerhub-username/vineet-task-frontend:v1
```

#### Backend Application

```bash
# Step 1: Navigate to backend directory
cd ../backend/

# Step 2: Build Docker image
docker build -t vineet-task-backend:v1 .

# Step 3: Tag for your registry
# For ECR:
docker tag vineet-task-backend:v1 YOUR_ACCOUNT_ID.dkr.ecr.us-west-2.amazonaws.com/vineet-task-backend:v1

# For Docker Hub:
docker tag vineet-task-backend:v1 your-dockerhub-username/vineet-task-backend:v1

# Step 4: Push to registry
# For ECR:
docker push YOUR_ACCOUNT_ID.dkr.ecr.us-west-2.amazonaws.com/vineet-task-backend:v1

# For Docker Hub:
docker push your-dockerhub-username/vineet-task-backend:v1
```

### Phase 5: Update Kubernetes Manifests

**What we're doing**: Updating our Kubernetes configuration files to use the correct Docker images.

```bash
# Navigate back to project root
cd ../../

# Update image URLs in deployment files
# Edit k8s_manifests/frontend-deployment.yaml
# Edit k8s_manifests/backend-deployment.yaml
# Replace 'vineet-frontend:latest' and 'vineet-backend:latest' with your actual image URLs
```

### Phase 6: Deploy Application to Kubernetes

**What we're doing**: Deploying our three-tier application to the EKS cluster.

#### Create Application Namespace

```bash
# Step 1: Create dedicated namespace
kubectl create namespace vineet-task-app

# Step 2: Set as default namespace
kubectl config set-context --current --namespace vineet-task-app

# Step 3: Verify namespace creation
kubectl get namespaces
```

#### Deploy Database Layer (MongoDB)

```bash
# Navigate to MongoDB manifests
cd k8s_manifests/mongo/

# Step 1: Create database secrets (credentials)
kubectl apply -f secrets.yaml

# Step 2: Deploy MongoDB database
kubectl apply -f deploy.yaml

# Step 3: Create MongoDB service (internal networking)
kubectl apply -f service.yaml

# Step 4: Verify MongoDB is running
kubectl get pods
kubectl get services
```

#### Deploy Backend Layer (Node.js API)

```bash
# Navigate back to k8s_manifests root
cd ../

# Step 1: Deploy backend application
kubectl apply -f backend-deployment.yaml

# Step 2: Create backend service
kubectl apply -f backend-service.yaml

# Step 3: Verify backend deployment
kubectl get deployments
kubectl get pods
kubectl logs deployment/api
```

#### Deploy Frontend Layer (React App)

```bash
# Step 1: Deploy frontend application
kubectl apply -f frontend-deployment.yaml

# Step 2: Create frontend service
kubectl apply -f frontend-service.yaml

# Step 3: Verify frontend deployment
kubectl get deployments
kubectl get pods
kubectl logs deployment/frontend
```

#### Deploy Load Balancer (External Access)

```bash
# Step 1: Create Application Load Balancer
kubectl apply -f full_stack_lb.yaml

# Step 2: Wait for load balancer to be ready (takes 2-3 minutes)
kubectl get ingress

# Step 3: Get your application URL
kubectl get service mainlb -o wide
```

### Phase 7: Verify Complete Deployment

**What we're doing**: Testing that everything is working correctly.

```bash
# Check all resources are running
kubectl get all

# Check pod status
kubectl get pods

# Check services
kubectl get services

# Check ingress/load balancer
kubectl get ingress

# Get application URL
kubectl get service mainlb -o jsonpath='{.status.loadBalancer.ingress[0].hostname}'
```

## 🔍 Monitoring & Troubleshooting Guide

### 📊 Checking Application Health

#### Monitor Pod Status
```bash
# Get all pods with their status
kubectl get pods -o wide

# Describe a specific pod (replace POD_NAME)
kubectl describe pod POD_NAME

# Check pod resource usage
kubectl top pods
```

#### View Application Logs
```bash
# Backend API logs
kubectl logs -f deployment/api

# Frontend application logs
kubectl logs -f deployment/frontend

# MongoDB database logs
kubectl logs -f deployment/mongodb

# Follow logs in real-time
kubectl logs -f deployment/api --tail=50
```

#### Check Services and Networking
```bash
# List all services
kubectl get services

# Check service endpoints
kubectl get endpoints

# Test internal service connectivity
kubectl exec -it POD_NAME -- curl http://api:5000/health
```

### 🔧 Auto Scaling Verification

#### Check Horizontal Pod Autoscaler
```bash
# View HPA status
kubectl get hpa

# Describe HPA configuration
kubectl describe hpa

# Check HPA metrics
kubectl top pods
kubectl top nodes
```

#### Verify Cluster Autoscaler
```bash
# Check cluster autoscaler pods
kubectl get pods -n kube-system | grep cluster-autoscaler

# View autoscaler logs
kubectl logs -f -n kube-system -l app=cluster-autoscaler

# Check node scaling
kubectl get nodes
watch kubectl get nodes
```

### 🌐 Load Balancer & Ingress

#### Check Load Balancer Status
```bash
# View load balancer service
kubectl get service mainlb

# Check load balancer controller logs
kubectl logs -f -n kube-system -l app.kubernetes.io/name=aws-load-balancer-controller

# Test load balancer endpoint
curl -I http://YOUR_LB_URL
```

### 🚨 Common Issues & Solutions

#### Issue 1: Pods Stuck in Pending State
```bash
# Check node resources
kubectl describe nodes

# Check pod events
kubectl describe pod POD_NAME

# Common solutions:
# - Scale up cluster nodes
# - Check resource requests/limits
# - Verify node selectors/taints
```

#### Issue 2: Image Pull Errors
```bash
# Check image pull secrets
kubectl get secrets

# Verify image exists in registry
docker pull YOUR_IMAGE_URL

# Common solutions:
# - Check image URL is correct
# - Verify registry authentication
# - Check image platform compatibility
```

#### Issue 3: Service Not Accessible
```bash
# Check service endpoints
kubectl get endpoints SERVICE_NAME

# Test service internally
kubectl run test-pod --image=busybox --rm -it -- wget -qO- http://SERVICE_NAME:PORT

# Common solutions:
# - Check pod labels match service selector
# - Verify port configuration
# - Check network policies
```

## 📈 Grafana Monitoring Setup

### 🎯 Accessing Grafana Dashboard

```bash
# Method 1: Port forwarding (for testing)
kubectl port-forward service/grafana 3000:80 -n monitoring

# Method 2: Load balancer (for production)
kubectl get service grafana -n monitoring
```

### 🔐 Default Credentials
- **Username**: `admin`
- **Password**: `prom-operator`

### 📊 Recommended Dashboards

1. **Node Exporter Full (ID: 1860)**
   - CPU, Memory, Disk usage
   - Network traffic
   - System load

2. **Kubernetes Cluster Monitoring (ID: 315)**
   - Pod resource usage
   - Deployment status
   - Service health

3. **Application Metrics**
   - Custom application metrics
   - API response times
   - Error rates

### 🔧 Adding Custom Dashboards

1. **Navigate to Grafana** → **+ (Plus icon)** → **Import**
2. **Enter Dashboard ID** (e.g., 1860)
3. **Configure data source**: Select **Prometheus**
4. **Save dashboard**

**Popular Dashboard IDs**:
- `1860` - Node Exporter Full
- `315` - Kubernetes cluster monitoring
- `6417` - Kubernetes Deployment Statefulset Daemonset metrics
- `8588` - 1 Kubernetes Deployment

## 🧪 Testing Your Application

### 🌐 Frontend Testing

```bash
# Get your application URL
FRONTEND_URL=$(kubectl get service mainlb -o jsonpath='{.status.loadBalancer.ingress[0].hostname}')
echo "Frontend URL: http://$FRONTEND_URL"

# Test frontend accessibility
curl -I http://$FRONTEND_URL

# Open in browser
# Navigate to http://$FRONTEND_URL
```

### ⚙️ Backend API Testing

```bash
# Get backend service URL
BACKEND_URL=$(kubectl get service api -o jsonpath='{.spec.clusterIP}'):5000

# Test API health endpoint
kubectl run test-pod --image=curlimages/curl --rm -it -- curl http://api:5000/health

# Test API endpoints
kubectl run test-pod --image=curlimages/curl --rm -it -- curl http://api:5000/api/tasks
```

### 🗄️ Database Testing

```bash
# Connect to MongoDB
kubectl exec -it deployment/mongodb -- mongo

# Inside MongoDB shell:
show dbs
use taskdb
db.tasks.find()

# Exit MongoDB shell
exit
```

## 🧹 Resource Cleanup Guide

### ⚠️ Important Notes
- **Cleanup order matters** - Always delete Kubernetes resources before destroying Terraform infrastructure
- **Double-check region** - Ensure you're cleaning up in the correct AWS region
- **Monitor costs** - Verify all resources are deleted to avoid charges

### 🗑️ Step 1: Remove Kubernetes Resources

```bash
# Delete application namespace (removes all app resources)
kubectl delete namespace vineet-task-app

# Delete monitoring namespace (if created)
kubectl delete namespace monitoring

# Verify resources are deleted
kubectl get all --all-namespaces
```

### 🏗️ Step 2: Destroy Terraform Infrastructure

```bash
# Navigate to terraform directory
cd terraform/

# Preview what will be destroyed
terraform plan -destroy

# Destroy all infrastructure
terraform destroy
# When prompted, type: yes

# Verify destruction
terraform show
```

### 🧽 Step 3: Clean Up Container Images

```bash
# Delete ECR repositories (if using ECR)
aws ecr delete-repository --repository-name vineet-task-frontend --region us-west-2 --force
aws ecr delete-repository --repository-name vineet-task-backend --region us-west-2 --force

# Clean up local Docker images
docker rmi vineet-task-frontend:v1
docker rmi vineet-task-backend:v1
docker system prune -f
```

### 💰 Cost Estimation

**Free Tier Resources** (No charge):
- EKS Control Plane: $0.10/hour (charged)
- t3.micro instances: 750 hours/month free
- Application Load Balancer: $0.0225/hour (charged)

**Estimated Monthly Cost**: $15-25 USD for learning/development

## 🔒 Security Best Practices

### 🛡️ Infrastructure Security

1. **IAM Best Practices**
   ```bash
   # Use least privilege principle
   # Rotate access keys regularly
   aws iam list-access-keys --user-name eks-admin
   ```

2. **Network Security**
   - Private subnets for worker nodes
   - Security groups with minimal required ports
   - VPC endpoints for AWS services

3. **Kubernetes Security**
   ```bash
   # Enable Pod Security Standards
   kubectl label namespace vineet-task-app pod-security.kubernetes.io/enforce=restricted
   
   # Use network policies
   kubectl apply -f network-policy.yaml
   ```

### 🔐 Application Security

1. **Container Security**
   - Use non-root users in containers
   - Scan images for vulnerabilities
   - Keep base images updated

2. **Secrets Management**
   ```bash
   # Use Kubernetes secrets for sensitive data
   kubectl create secret generic app-secrets --from-literal=db-password=yourpassword
   ```

3. **RBAC (Role-Based Access Control)**
   ```bash
   # Apply RBAC policies
   kubectl apply -f rbac-config.yaml
   ```

## 🤝 Contributing to This Project

### 🔄 Development Workflow

1. **Fork the repository**
2. **Create feature branch**
   ```bash
   git checkout -b feature/amazing-feature
   ```
3. **Make changes and commit**
   ```bash
   git commit -m 'Add some amazing feature'
   ```
4. **Push to branch**
   ```bash
   git push origin feature/amazing-feature
   ```
5. **Open Pull Request**

### 📝 Code Standards

- **Terraform**: Follow HashiCorp style guide
- **Kubernetes**: Use recommended labels and annotations
- **Docker**: Multi-stage builds and security best practices
- **Documentation**: Update README for any changes

## 🎓 Learning Resources

### 📚 Recommended Reading

1. **Kubernetes Official Documentation**
   - [https://kubernetes.io/docs/](https://kubernetes.io/docs/)

2. **AWS EKS Workshop**
   - [https://eksworkshop.com/](https://eksworkshop.com/)

3. **Terraform Documentation**
   - [https://learn.hashicorp.com/terraform](https://learn.hashicorp.com/terraform)

### 🎥 Video Tutorials

1. **Kubernetes Crash Course**
2. **AWS EKS Deep Dive**
3. **Terraform for Beginners**

### 🏆 Next Steps

After mastering this project, consider:
- **GitOps with ArgoCD**
- **Service Mesh with Istio**
- **Advanced monitoring with Jaeger**
- **Multi-environment deployments**
- **CI/CD with GitHub Actions**

## 📞 Support & Community

### 🆘 Getting Help

1. **GitHub Issues**: Report bugs and request features
2. **AWS Support**: For AWS-specific issues
3. **Kubernetes Community**: [https://kubernetes.slack.com/](https://kubernetes.slack.com/)

### 🌟 Show Your Support

If this project helped you learn, please:
- ⭐ **Star this repository**
- 🍴 **Fork it** for your own experiments
- 📢 **Share it** with fellow developers
- 💖 **Follow me** for more projects

## 📄 License

This project is licensed under the **MIT License** - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **AWS Community** for excellent documentation
- **Kubernetes Community** for the amazing platform
- **Terraform Community** for Infrastructure as Code
- **React & Node.js Communities** for powerful frameworks
- **Open Source Contributors** worldwide

---

## 📬 Contact Information

**Created by**: Vineet Chaudhari  
**GitHub**: [VineetC137](https://github.com/VineetC137)  
**Email**: [Your Email]  
**LinkedIn**: [Your LinkedIn Profile]

---

**🎯 Project Status**: ✅ Complete and Production Ready  
**🔄 Last Updated**: November 2024  
**📊 Difficulty Level**: Intermediate  
**⏱️ Estimated Setup Time**: 2-3 hours

> **💡 Pro Tip**: Bookmark this README and refer back to it as you work through the deployment. Each section builds upon the previous one, so take your time and don't skip steps!

**Built with ❤️ for learning cloud-native technologies and empowering developers worldwide**