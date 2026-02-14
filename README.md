# Goose Demo

## Databricks Terraform Management

This repo demonstrates how to use Terraform to manage Databricks resources.

### Getting Started
1. Copy `main.tf` to your workspace.
2. Create a `terraform.tfvars` file or supply variables via CLI:
    - `databricks_host` (your workspace URL)
    - `databricks_token` (your personal access token)

### Using S3 as the Terraform Backend
This project is configured to use an [S3 backend](https://developer.hashicorp.com/terraform/language/settings/backends/s3). Configure your backend as follows in your `main.tf` or `backend` block:

```hcl
terraform {
  backend "s3" {
    bucket         = "<YOUR_BUCKET_NAME>"
    key            = "<YOUR_STATE_PATH>"
    region         = "<YOUR_BUCKET_REGION>"
    dynamodb_table = "<OPTIONAL_DDB_FOR_LOCKING>"
    encrypt        = true
  }
}
```

Initialize Terraform:
```sh
terraform init
```

Apply the template:
```sh
terraform apply
```

Make sure your AWS credentials are available in your environment.
