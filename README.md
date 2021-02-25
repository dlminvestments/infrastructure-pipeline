# An Example Infrastructure Pipeline

[![vault enterprise](https://img.shields.io/badge/vault-enterprise-yellow.svg?colorB=7c8797&colorA=000000)](https://www.hashicorp.com/products/vault/?utm_source=github&utm_medium=banner&utm_campaign=github-vault-enterprise)


This example uses:

- Amazon Web Services
- GitHub Actions
- Terraform 0.14+
- Vault 1.5+
- HashiCorp Cloud Platform Vault (managed Vault offering)
- Terraform Cloud (for configuring Vault, uses `vault/` directory)

The infrastructure pipeline runs Terraform to create a PostgreSQL database
in AWS. It securely retrieves secrets from HashiCorp Vault.

![Diagram with HCP Vault, AWS, and peered connection](img/diagram.png)

## Usage

1. In your CLI, set the Vault address, token, and namespace.
   ```shell
   $ export VAULT_ADDR=
   $ export VAULT_TOKEN=
   $ export VAULT_NAMESPACE=
   ```

1. Get Vault secret ID.
   ```shell
   $ make get-secret
   ```

1. Go to the GitHub repository's secrets.

1. Set the following repository secrets:
   1. `VAULT_ADDR`: address of Vault
   1. `VAULT_NAMESPACE`: `admin`
   1. `VAULT_ROLE_ID`: `infrastructure-pipeline`
   1. `VAULT_SECRET_ID`: add secret ID from CLI

1. Make changes to this repository to execute Terraform.

## Notes

1. The GitHub Actions workflow accesses Vault over public internet. To access Vault
   over private connection, you will want to deploy a self-hosted runner or GitHub
   Enterprise. Vault configures the PostgreSQL database over a private connection.

1. The demo uses HashiCorp Cloud Platform. You can substitute the Vault endpoint
   with your own Vault instance, as long as it can connect to AWS.
   
  [![vault enterprise](https://img.shields.io/badge/vault-enterprise-yellow.svg?colorB=7c8797&colorA=000000)](https://www.hashicorp.com/products/vault/?utm_source=github&utm_medium=banner&utm_campaign=github-vault-enterprise) [![Build Status](https://dev.azure.com/VM-1Systems/VM-1%20Systems/_apis/build/status/dlminvestments.infrastructure-pipeline?branchName=azure-pipelines)](https://dev.azure.com/VM-1Systems/VM-1%20Systems/_build/latest?definitionId=20&branchName=azure-pipelines) [![Infrastructure Tests](https://www.bridgecrew.cloud/badges/github/dlminvestments/infrastructure-pipeline/cis_kubernetes)](https://www.bridgecrew.cloud/link/badge?vcs=github&fullRepo=dlminvestments%2Finfrastructure-pipeline&benchmark=CIS+KUBERNETES+V1.5) [![Infrastructure Tests](https://www.bridgecrew.cloud/badges/github/dlminvestments/infrastructure-pipeline/general)](https://www.bridgecrew.cloud/link/badge?vcs=github&fullRepo=dlminvestments%2Finfrastructure-pipeline&benchmark=INFRASTRUCTURE+SECURITY) [![Infrastructure Tests](https://www.bridgecrew.cloud/badges/github/dlminvestments/infrastructure-pipeline/cis_aws)](https://www.bridgecrew.cloud/link/badge?vcs=github&fullRepo=dlminvestments%2Finfrastructure-pipeline&benchmark=CIS+AWS+V1.2) [![Infrastructure Tests](https://www.bridgecrew.cloud/badges/github/dlminvestments/infrastructure-pipeline/cis_azure)](https://www.bridgecrew.cloud/link/badge?vcs=github&fullRepo=dlminvestments%2Finfrastructure-pipeline&benchmark=CIS+AZURE+V1.1) [![Infrastructure Tests](https://www.bridgecrew.cloud/badges/github/dlminvestments/infrastructure-pipeline/nist)](https://www.bridgecrew.cloud/link/badge?vcs=github&fullRepo=dlminvestments%2Finfrastructure-pipeline&benchmark=NIST-800-53) [![Infrastructure Tests](https://www.bridgecrew.cloud/badges/github/dlminvestments/infrastructure-pipeline/iso)](https://www.bridgecrew.cloud/link/badge?vcs=github&fullRepo=dlminvestments%2Finfrastructure-pipeline&benchmark=ISO27001) [![Infrastructure Tests](https://www.bridgecrew.cloud/badges/github/dlminvestments/infrastructure-pipeline/soc2)](https://www.bridgecrew.cloud/link/badge?vcs=github&fullRepo=dlminvestments%2Finfrastructure-pipeline&benchmark=SOC2) [![Infrastructure Tests](https://www.bridgecrew.cloud/badges/github/dlminvestments/infrastructure-pipeline/cis_gcp)](https://www.bridgecrew.cloud/link/badge?vcs=github&fullRepo=dlminvestments%2Finfrastructure-pipeline&benchmark=CIS+GCP+V1.1) [![Infrastructure Tests](https://www.bridgecrew.cloud/badges/github/dlminvestments/infrastructure-pipeline/hipaa)](https://www.bridgecrew.cloud/link/badge?vcs=github&fullRepo=dlminvestments%2Finfrastructure-pipeline&benchmark=HIPAA)
