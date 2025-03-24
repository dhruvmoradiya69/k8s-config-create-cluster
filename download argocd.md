# Install ArgoCD

## Create Namespace and Install ArgoCD

ArgoCD requires a dedicated namespace for deployment. The following commands create the `argocd` namespace and apply the necessary manifests to install ArgoCD:

```sh
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

## Install ArgoCD CLI

The ArgoCD CLI is required for managing applications and interacting with the ArgoCD API. The following commands fetch and install the latest stable version of the CLI:

```sh
VERSION=$(curl -L -s https://raw.githubusercontent.com/argoproj/argo-cd/stable/VERSION)
curl -sSL -o argocd-linux-amd64 https://github.com/argoproj/argo-cd/releases/download/v$VERSION/argocd-linux-amd64
sudo install -m 555 argocd-linux-amd64 /usr/local/bin/argocd
rm argocd-linux-amd64
```

## Configure Custom Port for ArgoCD

By default, ArgoCD runs on a specific internal port. To make it accessible externally, modify the `argocd-server` service to use a `NodePort` type and assign a specific external port:

```sh
kubectl patch svc argocd-server -n argocd -p '{"spec": {"type": "NodePort", "ports": [{"port": 443, "targetPort": 443, "nodePort": 30005}]}}'
```

## Retrieve ArgoCD Initial Admin Password

To log in for the first time, retrieve the default admin password stored in a Kubernetes secret:

```sh
kubectl get secret argocd-initial-admin-secret -n argocd -o jsonpath="{.data.password}" | base64 -d
```

## Port Forward ArgoCD Server

If external access is not configured, use port forwarding to access the ArgoCD UI locally:

```sh
kubectl port-forward svc/argocd-server -n argocd 8081:443
```

This command forwards traffic from the local machine's port `8081` to the ArgoCD server running on port `443`.

You can now access the ArgoCD UI at [https://localhost:8081](https://localhost:8081).
