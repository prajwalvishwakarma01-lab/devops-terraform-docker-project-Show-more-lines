# Task 3: Infrastructure as Code (IaC) with Terraform
 
## Objective
 
Provision a Docker container locally using Terraform and manage the infrastructure through Infrastructure as Code (IaC).
 
---
 
## Technologies Used
 
- Terraform
- Docker Desktop
- Nginx Docker Image
- Windows 11
- PowerShell
 
---
 
## Project Architecture
 
Terraform → Docker Provider → Docker Engine → Nginx Container
 
---
 
## Prerequisites
 
### Install Docker Desktop
 
Verify installation:
 
```powershell
docker --version
```
 
### Install Terraform
 
Verify installation:
 
```powershell
terraform --version
```
 
---
 
## Terraform Configuration
 
File: `main.tf`
 
```hcl
terraform {
required_providers {
docker = {
source = "kreuzwerker/docker"
version = "~> 3.0"
}
}
}
 
provider "docker" {}
 
resource "docker_image" "nginx_image" {
name = "nginx:latest"
}
 
resource "docker_container" "nginx_container" {
name = "terraform-nginx"
image = docker_image.nginx_image.image_id
 
ports {
internal = 80
external = 8081
}
}
```
 
---
 
## Execution Steps
 
### Initialize Terraform
 
```powershell
terraform init
```
 
---
 
### Validate Configuration
 
```powershell
terraform validate
```
 
---
 
### View Execution Plan
 
```powershell
terraform plan
```
 
---
 
### Create Infrastructure
 
```powershell
terraform apply
```
 
Type:
 
```text
yes
```
 
---
 
### Verify Running Container
 
```powershell
docker ps
```
 
---
 
### Check Terraform State
 
```powershell
terraform state list
```
 
---
 
### Destroy Infrastructure
 
```powershell
terraform destroy
```
 
Type:
 
```text
yes
```
 
---
 
## Screenshots
 
### Terraform Init
 
(Add screenshot here)
 
### Terraform Plan
 
(Add screenshot here)
 
### Terraform Apply
 
(Add screenshot here)
 
### Docker Container Running
 
(Add screenshot here)
 
### Nginx Welcome Page
 
(Add screenshot here)
 
### Terraform State
 
(Add screenshot here)
 
### Terraform Destroy
 
(Add screenshot here)
 
---
 
## Outcome
 
- Successfully provisioned infrastructure using Terraform.
- Pulled Docker image automatically.
- Created and managed Docker container through code.
- Verified state management using Terraform state commands.
- Destroyed infrastructure using Terraform destroy.
 
---
 
## Key Learnings
 
- Infrastructure as Code (IaC)
- Terraform Providers
- Terraform Resources
- Terraform State Management
- Docker Integration
- Infrastructure Lifecycle Management
 
---