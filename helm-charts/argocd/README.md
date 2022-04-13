# Helm chart for ArgoCD

## How to apply manually

```bash
# creates namespace
ns_tools=cdtools
kubectl create ns $ns_tools

# generates locally the manifest
helm template . --name-template=devpro-samples-argocd --include-crds -n $ns_tools > temp.yaml

# applies the manifest
kubectl apply -f temp.yaml -n $ns_tools

# checks when all deployments are available
kubectl get deploy -n $ns_tools

# retrieves admin password
kubectl get secret argocd-initial-admin-secret -n $ns_tools -o jsonpath="{.data.password}" | base64 -d

# opens a port forward to access the web UI on http://localhost:8080
kubectl port-forward svc/devpro-samples-argocd-server 8080:443 -n $ns_tools
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
