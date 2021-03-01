## Usage

Creates a KMS Key for use with AWS SSM.

```hcl
module "ssm_kms_key" {
  source = "dod-iac/ssm-kms-key/aws"

  name = format("alias/app-%s-ssm-%s", var.application, var.environment)
  description = format("A KMS key used to encrypt SSM volumes for %s:%s.", var.application, var.environment)
  tags = {
    Application = var.application
    Environment = var.environment
    Automation  = "Terraform"
  }
}
```

## Terraform Version

Terraform 0.13. Pin module version to ~> 1.0.0 . Submit pull-requests to master branch.

Terraform 0.11 and 0.12 are not supported.

## License

This project constitutes a work of the United States Government and is not subject to domestic copyright protection under 17 USC § 105.  However, because the project utilizes code licensed from contributors and other third parties, it therefore is licensed under the MIT License.  See LICENSE file for more information.

## Requirements

| Name | Version |
|------|---------|
| terraform | >= 0.12 |
| aws | >= 2.55.0 |

## Providers

| Name | Version |
|------|---------|
| aws | >= 2.55.0 |

## Inputs

| Name | Description | Type | Default | Required |
|------|-------------|------|---------|:--------:|
| description | n/a | `string` | `"A KMS key used to encrypt SSM volumes."` | no |
| key\_deletion\_window\_in\_days | Duration in days after which the key is deleted after destruction of the resource, must be between 7 and 30 days. | `string` | `30` | no |
| name | The display name of the alias. The name must start with the word "alias" followed by a forward slash (alias/). | `string` | n/a | yes |
| tags | Tags applied to the KMS key. | `map(string)` | `{}` | no |

## Outputs

| Name | Description |
|------|-------------|
| aws\_kms\_alias\_arn | The Amazon Resource Name (ARN) of the key alias. |
| aws\_kms\_alias\_name | The display name of the alias. |
| aws\_kms\_key\_arn | The Amazon Resource Name (ARN) of the key. |

