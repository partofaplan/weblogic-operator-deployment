# WebLogic Operator Helm Deployment

This repository packages the upstream Oracle WebLogic Kubernetes Operator Helm chart and keeps it aligned with the official container image published by Oracle. Custom Resource Definitions (CRDs) required by the operator are bundled so a single Helm install sets up the full control plane. You can install the chart straight from this repository or adapt the values file for your cluster.

## Structure

- `weblogic-operator/` – the Helm chart (templates, values, and helper configs).
- `weblogic-operator/crds/` – CRDs applied automatically with the chart.
- `README.md` – this file.

## Usage

```bash
helm dependency update weblogic-operator
helm install weblogic-operator ./weblogic-operator \
  --namespace weblogic-operator \
  --create-namespace
```

Override any value from `weblogic-operator/values.yaml`, for example to point to a different tag or registry:

```bash
helm install weblogic-operator ./weblogic-operator \
  --set image=ghcr.io/oracle/weblogic-kubernetes-operator:4.3.3
```

> ℹ️ The chart still exposes all the knobs from the upstream Oracle chart, so you can configure domain namespaces, RBAC scope, REST access, logging, and other operator features in the usual way.
