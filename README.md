# Cloud Data Platform IaC

<p align="center">
  <img src="https://img.shields.io/badge/Terraform-7B42BC?style=for-the-badge&logo=terraform&logoColor=white" alt="Terraform" />
  <img src="https://img.shields.io/badge/Bicep-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white" alt="Bicep" />
  <img src="https://img.shields.io/badge/Azure-0078D4?style=for-the-badge&logo=microsoftazure&logoColor=white" alt="Azure" />
  <img src="https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge&logo=githubactions&logoColor=white" alt="GitHub Actions" />
  <img src="https://img.shields.io/badge/PowerShell-5391FE?style=for-the-badge&logo=powershell&logoColor=white" alt="PowerShell" />
</p>

> 🚧 **Planned**.... Modules and workflows will land as the project takes shape.

Infrastructure-as-code for provisioning and deploying cloud data platforms, Azure data services, Microsoft Fabric configuration, and the CI/CD that ties them together across environments.

## What this is

Reusable infrastructure modules and deployment workflows for standing up a cloud data platform end to end:

- **Azure provisioning** - Storage, Key Vault, Synapse, Data Factory, Databricks, Event Hubs via Bicep and Terraform
- **Fabric configuration** - workspace setup, capacity assignment, and item deployment via REST API and PowerShell
- **Environment separation** - consistent dev / test / prod deployments with parameterised config
- **CI/CD** - GitHub Actions workflows for plan, validate, apply, and tear-down
- **Secrets and identity** - managed identities, Key Vault references, and service principals wired through from the start

Each module is self-contained and composable. The point isn't "here's a Terraform file", it's "here's how these pieces fit together so you can deploy a working platform, not just isolated resources."

## Why this exists

Provisioning a data platform is rarely one tool. Azure resources go through Bicep or Terraform, but Microsoft Fabric workspaces and items don't have first-class IaC coverage the way other Azure services do, so you end up stitching ARM, REST APIs, and PowerShell together just to get a repeatable deployment.

On the support side, I've seen what happens when infrastructure isn't codified: environments drift, configs are undocumented, and "it works in dev" becomes a standing joke. This repo is the setup I'd want to inherit, reproducible, versioned, and honest about where the tooling gaps are.

## Planned Structure

```
cloud-data-platform-iac/
├── README.md
├── terraform/
│   ├── modules/
│   │   ├── storage/
│   │   ├── keyvault/
│   │   ├── synapse/
│   │   ├── datafactory/
│   │   └── databricks/
│   └── environments/
│       ├── dev/
│       ├── test/
│       └── prod/
├── bicep/
│   └── (parallel module set, where Bicep is the better fit)
├── fabric/
│   ├── workspaces/
│   └── deployment/
├── scripts/
│   └── powershell/
└── .github/
    └── workflows/
```

## Related

- [Predictive Maintenance Pipeline](https://github.com/SonOfElle/predictive-maintenance-pipeline) - the platform this IaC is designed to deploy
- [PySpark Troubleshooting Lab](https://github.com/SonOfElle/pyspark-troubleshooting-lab) - the compute environment provisioned by these modules

*Status: planned. Modules, workflows, and documentation will be committed as the project develops.*
