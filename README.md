# platformctl-templates

Template registry for [`platformctl`](https://github.com/GCICHON-DEV/platformctl).

Templates are YAML manifests that define:

- required input values
- default values
- required local tools
- files rendered into `generated/`
- `steps.plan` preview workflow (optional)
- `steps.apply` provisioning workflow
- `steps.destroy` cleanup workflow
- success messages
- notes and next steps

The current template contract is `apiVersion: platformctl.io/v1beta1`.

## Templates

- `platformctl/aws-eks-standard`
- `platformctl/azure-aks-standard`
- `platformctl/local-kind-standard`

Use a template from `platform.yaml`:

```yaml
template:
  source: platformctl/aws-eks-standard
  version: v1.1.0

values:
  project_name: demo
  region: eu-central-1
  aws_profile: default
  cluster_name: demo-platform
```

For Azure:

```yaml
template:
  source: platformctl/azure-aks-standard
  version: v1.1.0

values:
  project_name: demo
  region: westeurope
  cluster_name: demo-aks
```

For local Kind:

```yaml
template:
  source: platformctl/local-kind-standard
  version: v1.1.0

values:
  project_name: demo
  cluster_name: demo-local
```

Do not put secrets in template manifests. Store secrets in external systems such as AWS Secrets Manager, Azure Key Vault, Vault, or SOPS-managed files.

## Development

See [CONTRIBUTING.md](CONTRIBUTING.md) for delivery rules and the [project audit and backlog](https://github.com/GCICHON-DEV/platformctl/blob/main/docs/project-audit.md) for completion criteria. CI validates and renders manifests with a pinned CLI revision; it does not provision cloud resources.
