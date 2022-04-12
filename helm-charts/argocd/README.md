# Helm chart for ArgoCD

## How to apply manually

```bash
# generates locally the manifest
helm template . --name-template=devpro-samples-argocd --include-crds -n cdtools > temp.yaml

# applies the manifest and wait for the deployments to be available
kubectl create ns cdtools
kubectl apply -f temp.yaml -n cdtools
kubectl get deploy -n cdtools

# retrieves admin password
kubectl get secret argocd-initial-admin-secret -n cdtools -o jsonpath="{.data.password}" | base64 -d

# opens a port forward to access the web UI on http://localhost:8080
kubectl port-forward svc/devpro-samples-argocd-server 8080:443 -n cdtools
```

## How to update the version

```bash
# adds the Helm repository
helm repo add argo https://argoproj.github.io/argo-helm

# looks for the latest chart
helm repo update
helm search repo argo

# creates or updates 
helm dependency update
```
