# ArgoCD Test Application

Simple nginx deployment for testing ArgoCD GitOps workflow.

## Structure

```
k8s/
├── deployment.yaml  # Nginx deployment (2 replicas)
└── service.yaml     # LoadBalancer service
```

## Deployment

This application is managed by ArgoCD on Civo Kubernetes cluster.

- **Replicas:** 2
- **Image:** nginx:1.27-alpine
- **Service Type:** LoadBalancer
