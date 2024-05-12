# Terraform Cheat-Sheet

## Format and Validate

| Command | Description |
| --- | --- |
| `terraform fmt` | Reformat your configuration in the standard style |
| `terraform validate` | Check whether the configuration is valid |

## Initialize Working Directory

| Command | Description |
| --- | --- |
| `terraform init` | Prepare your working directory for other commands |

## Plan, Deploy and Cleanup

| Command | Description |
| --- | --- |
| `terraform apply --auto-approve` | Create or update infrastructure without confirmation prompt |
| `terraform destroy --auto-approve` | Destroy previously-created infrastructure without confirmation prompt |
| `terraform plan -out plan.out` | Output the deployment plan to plan.out |
| `terraform apply plan.out` | Use the plan.out to deploy infrastructure |
| `terraform plan -destroy` | Outputs a destroy plan |
| `terraform apply -target=aws_instance.myinstance` | Only apply/deploy changes to targeted resource |
| `terraform apply -var myregion=us-east-1` | Pass a variable via CLI while applying a configuration |
| `terraform apply -lock=true` | Lock the state file so it can't be modified |
| `terraform apply refresh=false` | Do not reconcile state file with real-world resources |
| `terraform apply --parallelism=5` | Number of simultaneous resource operations |
| `terraform refresh` | Reconcile the state in Terraform state file with real-world resources |
| `terraform providers` | Get informatino about providers used in the current configuration |

## Workspaces

| Command | Description |
| --- | --- |
| `terraform workspace new <workspace>` | Create a new workspace |
| `terraform workspace select default` | Change to a workspace |
| `terraform workspace list` | List all workspaces |

## State Manipulation

| Command | Description |
| --- | --- |
| `terraform state show aws_instance.myinstance` | Show details stored in the Terraform state file |
| `terraform state pull > terraform.tfstate` | Output Terraform state to a file |
| `terraform state mv aws_iam_role.my_ssm_role module.mymodule` | Move a resource tracked via state to different module |
| `terraform state replace-provider hashicorp/aws registry.custom.com/aws` | Replace an existing provider with another |
| `terraform state list` | List all resources tracked in the Terraform state file |
| `terraform state rm aws_instance.myinstance` | Unmanage a resource, delete it from the Terraform state file |

## Import and Outputs

| Command | Description |
| --- | --- |
| `terraform import <resource_type>.<resource> <id>` | Import a Resource |
| `terraform output` | List all outputs |
| `terraform output <output>` | List a specific output |
| `terraform output -json` | List all outputs in JSON format |

## Terraform Cloud

| Command | Description |
| --- | --- |
| `terraform login` | Login to Terraform Cloud with an API token |
| `terraform logout` | Logout from Terraform Cloud |
