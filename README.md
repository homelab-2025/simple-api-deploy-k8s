# SIMPLE API Deploy k8s

This is a repo to deploy simple-api on kubernetes.

## HELM

### Prerequisites

- Access to the Kubernetes cluster
- Helm installed

### Deploying with Helm

1. Clone the repository:

```bash
git clone https://github.com/homelab-2025/simple-api-deploy-k8s.git
```

2. Change directory into the cloned repository:

```bash
cd simple-api-deploy-k8s
```

3. Install the Helm chart:

```bash
helm install myfirstrelease ./charts/simple-api
```

### Deleting the Release

To delete the release, run:

```bash
helm uninstall myfirstrelease
```

## ArgoCD

### Prerequisites

- Access to the Kubernetes cluster with ArgoCD installed
- ArgoCD CLI installed

### Deploying with ArgoCD


1. Create an ArgoCD application:

```bash
argocd app create simple-api  \
  --repo https://github.com/homelab-2025/simple-api-deploy-k8s.git \
  --path chart \
  --dest-server https://kubernetes.default.svc \
  --dest-namespace app
  --helm-set replicaCount=2
```

2. Sync the application:

```bash
argocd app sync simple-api
```
