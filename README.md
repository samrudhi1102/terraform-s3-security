
# Terraform S3 Security

A hands-on AWS Infrastructure as Code project that provisions and secures an Amazon S3 bucket using Terraform.

## Project Overview

This project demonstrates how to automate S3 bucket creation and apply essential security and data-management configurations.

## AWS Services and Tools

- Amazon S3
- AWS IAM and AWS CLI
- Terraform
- Git and GitHub

## Security Features

- **Public Access Block:** Enables all four S3 public-access protection settings.
- **Server-Side Encryption:** Uses AES-256 encryption by default.
- **Bucket Versioning:** Keeps multiple versions of objects to support recovery.
- **Lifecycle Management:** Expires noncurrent object versions after 30 days.

## Architecture

Terraform configuration → AWS Provider → Amazon S3 bucket → Security, encryption, versioning, and lifecycle settings.

## How to Run

Prerequisites: Terraform, AWS CLI, and AWS credentials with the required permissions.

```powershell
terraform init
terraform fmt
terraform validate
terraform plan
terraform apply
```

Review the plan before approving `terraform apply`.

## Verify Configuration

```powershell
aws s3api get-public-access-block --bucket YOUR_BUCKET_NAME --region ap-south-1

aws s3api get-bucket-encryption --bucket YOUR_BUCKET_NAME --region ap-south-1

aws s3api get-bucket-versioning --bucket YOUR_BUCKET_NAME --region ap-south-1

aws s3api get-bucket-lifecycle-configuration --bucket YOUR_BUCKET_NAME --region ap-south-1
```

Replace `YOUR_BUCKET_NAME` with the bucket name printed by Terraform.

## Cleanup

Only when you intentionally want to remove the infrastructure, review the consequences and run:

```powershell
terraform plan -destroy
terraform destroy
```

Do not destroy the bucket if you need to retain its data or version history. S3 bucket deletion may require removing all stored object versions first.

## Learning Outcomes

- Infrastructure as Code with Terraform
- AWS S3 security configuration
- Encryption and versioning
- Lifecycle-based storage management
- Infrastructure change review and Git version control
