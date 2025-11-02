# WebLogic Operator Helm Deployment

This repository packages the upstream Oracle WebLogic Kubernetes Operator Helm chart and updates it to use the Docker Hub image `partofaplan/weblogic-base` by default.  You can install the chart straight from this repository or adapt the values file for your cluster.

## Structure

- `weblogic-operator/` – the Helm chart (templates, values, and helper configs).
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
  --set image=docker.io/partofaplan/weblogic-base:v1.0.0
```

> ℹ️ The chart still exposes all the knobs from the upstream Oracle chart, so you can configure domain namespaces, RBAC scope, REST access, logging, and other operator features in the usual way.

