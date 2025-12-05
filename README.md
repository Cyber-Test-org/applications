# ArgoCD Test Application

Simple nginx deployment for testing ArgoCD GitOps workflow.

## Structure

```
argocd/
├── application.yaml # ArgoCD Application manifest
└── project.yaml     # ArgoCD Project manifest
k8s/
├── deployment.yaml  # Nginx deployment (4 replicas)
└── service.yaml     # LoadBalancer service
```

## ArgoCD Declarative Configuration

The `argocd/` directory contains declarative configuration for ArgoCD:

- **project.yaml**: Defines the ArgoCD Project with source and destination restrictions
- **application.yaml**: Defines the ArgoCD Application that syncs the `k8s/` manifests

### Deploying the ArgoCD Configuration

Apply the ArgoCD manifests to your cluster:

```bash
kubectl apply -f argocd/project.yaml
kubectl apply -f argocd/application.yaml
```

### Sync Policy

The application is configured with automated sync:
- **Prune**: Automatically removes resources that are no longer in Git
- **Self-heal**: Automatically reverts manual changes made to the cluster

## Application Details

This application is managed by ArgoCD on Civo Kubernetes cluster.

- **Replicas:** 4
- **Image:** nginx:1.27-alpine
- **Service Type:** LoadBalancer
