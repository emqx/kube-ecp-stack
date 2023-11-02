# kube-ecp-stack

This repository contains the Helm chart for deploying emqx-ecp on Kubernetes.

## Prerequisites
Before you begin, ensure you have the following installed and set up:

- Kubernetes cluster
- Helm (v3.0+)
- kubectl CLI

## Installation
Here are the steps to deploy emqx-ecp using the Helm chart:

1. Clone this repository:

```bash
git clone https://github.com/emqx/kube-ecp-stack.git
cd kube-ecp-stack
```
2. Configure image registry
```bash
global:
  images:
    registry: <your_image_registry>
    imageCredentials:
      username: <your_user_name>
      password: <your_user_password>
```

3. Update subchart dependencies:

```bash
helm dependency update
```

4. Install the Helm chart:

```bash
helm upgrade --install emqx-ecp . \
  --namespace emqx-ecp \
  --create-namespace \
  --set global.storage.storageClassName=<your-storageclass> \
  --set postgresql.global.storageClass=<your-storageclass>
```


## Uninstalling the Chart

```bash
helm uninstall emqx-ecp -n emqx-ecp
```

