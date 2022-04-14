# WordPress

## How to apply manually

```bash
# generates locally the manifest
helm template . --name-template=devpro-samples-wordpress --include-crds > temp.yaml

# applies the manifest
kubectl apply -f temp.yaml -n kube-system
```

## How to update the version

```bash
# adds the helm repository
helm repo add bitnami https://charts.bitnami.com/bitnami

# looks for the latest chart
helm repo update
helm search repo wordpress

# creates or updates 
helm dependency update
```
