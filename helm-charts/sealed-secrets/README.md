# Helm chart for Bitnami Sealed Secrets

[Sealed Secrets](https://github.com/bitnami-labs/sealed-secrets) gives the ability to store protected secrets ("sealed") in git.

## How to apply manually

```bash
# generates locally the manifest
helm template . --name-template=devpro-samples-sealedsecrets --include-crds > temp.yaml

# applies the manifest
kubectl apply -f temp.yaml -n kube-system
```

## How to update the version

```bash
# adds the helm repository
helm repo add sealed-secrets https://bitnami-labs.github.io/sealed-secrets

# looks for the latest chart
helm repo update
helm search repo sealed-secrets

# creates or updates 
helm dependency update
```
