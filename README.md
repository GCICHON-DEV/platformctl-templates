# platformctl-templates

Template registry for [`platformctl`](https://github.com/GCICHON-DEV/platformctl).

Templates are YAML manifests that define:

- required input values
- default values
- required local tools
- files rendered into `generated/`
- `up` workflow steps
- `down` workflow steps
- success messages

## Templates

- `platformctl/aws-eks-standard`
- `platformctl/azure-aks-standard`
- `platformctl/local-kind-standard`

Use a template from `platform.yaml`:

```yaml
template:
  source: platformctl/aws-eks-standard
  version: v1.0.0

values:
  project_name: demo
  aws_region: eu-central-1
  aws_profile: default
  cluster_name: demo-platform
```

For Azure:

```yaml
template:
  source: platformctl/azure-aks-standard
  version: v1.0.0

values:
  project_name: demo
  azure_location: westeurope
  resource_group: demo-platform-rg
  cluster_name: demo-aks
```

For local Kind:

```yaml
template:
  source: platformctl/local-kind-standard
  version: v1.0.0

values:
  project_name: demo
  cluster_name: demo-local
```

Do not put secrets in template manifests. Store secrets in external systems such as AWS Secrets Manager, Azure Key Vault, Vault, or SOPS-managed files.
