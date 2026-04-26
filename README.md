# platformctl-templates

Template registry for `platformctl`.

## Templates

### `platformctl/aws-eks-standard`

Standard AWS EKS developer platform with:

- VPC
- EKS managed node group
- `dev`, `staging`, and `production` namespaces
- ArgoCD
- kube-prometheus-stack
- Prometheus
- Grafana
- ingress-nginx
- baseline quotas, limits, and network policies

Use it from `platform.yaml`:

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

Do not put secrets in template manifests. Store secrets in external systems such as AWS Secrets Manager.
