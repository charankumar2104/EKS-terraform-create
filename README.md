# Learn Terraform - Provision an EKS Cluster

This repo is a companion repo to the [Provision an EKS Cluster tutorial](https://developer.hashicorp.com/terraform/tutorials/kubernetes/eks), containing
Terraform configuration files to provision an EKS cluster on AWS.


# 🚀 Terraform EKS Infrastructure Automation (Beginner Friendly)

This repository demonstrates how to **manage AWS EKS infrastructure** using **Terraform** and **GitHub Actions**.

This README is written for **people with zero prior knowledge** of:
- Terraform
- GitHub Actions
- AWS IAM
- CI/CD pipelines

Follow each step in order.

---

## 📌 What This Project Does

This project:
- Uses Terraform to define AWS infrastructure (EKS cluster)
- Uses GitHub Actions to run Terraform commands
- Validates, lints, and scans infrastructure code
- **Destroys AWS infrastructure safely**

⚠️ **Warning**  
This pipeline performs `terraform destroy` and **will delete AWS resources**.

---

## 🧱 Repository Structure

```
.
├── terraform/
│   ├── main.tf
│   ├── variables.tf
│   ├── outputs.tf
│   ├── providers.tf
│   └── modules/
│       └── eks/
│           ├── cluster.tf
│           ├── nodegroup.tf
│           └── iam.tf
│
├── .github/
│   └── workflows/
│       └── destroy-eks.yml
│
└── README.md
```

---

## 🔧 Prerequisites

- AWS account
- GitHub account
- Git installed locally
- Basic terminal knowledge

---

## 🔐 Step 1: Create AWS IAM User (For GitHub Actions)

### Why This Is Required
GitHub Actions must authenticate with AWS to manage infrastructure.

### Steps
1. Login to AWS Console
2. Open **IAM**
3. Go to **Users → Create user**
4. User name: `github-actions-terraform`
5. Select **Programmatic access**
6. Attach policy: `AdministratorAccess`
7. Create user and download:
   - Access Key ID
   - Secret Access Key

⚠️ Save the secret key securely. It cannot be recovered later.

---

## 🔑 Step 2: Add GitHub Secrets (AWS Credentials)

### Why This Is Required
GitHub Actions cannot access your AWS account without credentials.

### Steps
1. Open your GitHub repository
2. Go to **Settings**
3. Click **Secrets and variables → Actions**
4. Click **New repository secret**

#### Add Secret 1
- Name: `AWS_ACCESS_KEY_ID`
- Value: AWS Access Key ID

#### Add Secret 2
- Name: `AWS_SECRET_ACCESS_KEY`
- Value: AWS Secret Access Key

---

## 🔽 Step 3: Clone the Repository

```
git clone https://github.com/<your-username>/<your-repo-name>.git
cd <your-repo-name>
```

---

## 🛠️ Step 4: Customize Terraform Infrastructure

All Terraform code is inside the `terraform/` directory.

### 4.1 Update EKS Cluster Name
File: `terraform/main.tf`

```
cluster_name = "dev-eks-cluster"
```

### 4.2 Update Node Group Configuration
File: `terraform/modules/eks/nodegroup.tf`

Change:
- instance type
- desired, min, max nodes

---

## ⚙️ Step 5: Customize GitHub Actions Pipeline

File: `.github/workflows/destroy-eks.yml`

### Runner
```
runs-on: ubuntu-latest
```

You may change to:
- ubuntu-22.04
- self-hosted

### AWS Region
```
aws-region: ap-northeast-1
```

---

## 📤 Step 6: Commit and Push Changes

```
git add .
git commit -m "Customize Terraform and pipeline"
git push origin main
```

---

## ▶️ Step 7: Run the GitHub Actions Pipeline

1. Open your GitHub repository
2. Click **Actions**
3. Select workflow **Create EKS Cluster**
4. Click **Run workflow**
5. Monitor execution logs

---

## 🔍 Step 8: Verify Results

Check AWS Console:
- EKS clusters
- EC2 instances
- VPC resources

---

## ⚠️ Critical Warnings

🚨 This pipeline runs `terraform destroy`.

- Deletes AWS resources
- Use only in non-production environments
- Always verify AWS account and region

---

## 🧠 Summary

1. Create AWS IAM user  
2. Add GitHub secrets  
3. Clone repository  
4. Customize Terraform  
5. Customize pipeline  
6. Push changes  
7. Run workflow  

---

## 📚 Next Steps

- Create separate `terraform apply` pipeline
- Use remote Terraform state (S3 + DynamoDB)
- Add approval gates



