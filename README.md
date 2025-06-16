# Example Three-Tier Kubernetes Application

This repository contains an example of a very basic three-tier architecture set
up using Kubernetes. Each tier runs as its own Deployment with a corresponding
Service so the components can communicate with one another inside the cluster.

## Tiers

1. **Frontend** – an `nginx` container that serves static content on port 80.
2. **Backend** – a minimal Python HTTP server that listens on port 8000.
3. **Database** – a PostgreSQL instance listening on port 5432.

All manifests are located in [`k8s/three-tier.yaml`](k8s/three-tier.yaml). To
apply everything at once run:

```bash
kubectl apply -f k8s/three-tier.yaml
```

> The manifests use `ClusterIP` services which means they are only reachable
> within the cluster. If you want to expose the frontend externally, change its
> service type to `LoadBalancer` or `NodePort` depending on your environment.

To remove the resources run:

```bash
kubectl delete -f k8s/three-tier.yaml
```
