# Learn Terraform - Provision an EKS Cluster

This repo is a companion repo to the [Provision an EKS Cluster tutorial](https://developer.hashicorp.com/terraform/tutorials/kubernetes/eks), containing
Terraform configuration files to provision an EKS cluster on AWS.


# 🚀 Terraform EKS Infrastructure – GitHub Actions (Beginner Friendly Guide)

This repository helps you **create and destroy AWS EKS infrastructure** using **Terraform** and **GitHub Actions**.

⚠️ This guide assumes **NO prior knowledge** of:
- Terraform
- GitHub Actions
- AWS IAM
- CI/CD pipelines

Follow the steps in order.

---

## 📌 What This Project Does

This project:
- Uses **Terraform** to define AWS infrastructure (EKS cluster)
- Uses **GitHub Actions** to run Terraform commands
- Validates and scans infrastructure code
- **Destroys AWS resources safely**

---

## 🧱 Repository Structure

```text
.
├── terraform/                  # Terraform infrastructure code
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
│       └── destroy-eks.yml     # GitHub Actions pipeline
│
└── README.md                   # This documentation


