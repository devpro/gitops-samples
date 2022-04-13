# ArgoCD applications Helm chart sample

## How to deploy

```bash
# creates manifest file
helm template . > temp.yaml

# applies the manifest
kubectl apply -f temp.yaml
```
