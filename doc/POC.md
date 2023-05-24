# Отримання доступу до ArgoCD Dashboard

## Встановлення k3d

Для встановлення k3d використовуйте офіційну документацію: https://k3d.io/v5.5.1/#installation

## Створення кластера

```bash
k3d cluster create testcluster
```

![Image](k3d-poc-demo.gif)

## Встановлення ArgoCD

```bash
kubectl create namespace argocd
kubectl apply -n argocd -f https://raw.githubusercontent.com/argoproj/argo-cd/stable/manifests/install.yaml
```

![Image](argocd-install-demo.gif)