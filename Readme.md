# Kubernetes Docker for Mac

## Introduction

This should help you start using Kubernetes on your Docker for Mac installation

## Contents

- [Install](#install)
- [Run](#run)

## Install

```bash
brew cask install docker
brew install kubernetes-cli kubernetes-helm
```

### Enable Kubernetes

- Docker Preference
- Kubernetes
- Enable Kubernetes
- Appply and Restart

### Initialize Helm

```bash
helm init
```

## Run

```bash
# Initialize

# List your current nodes
kubectl get nodes

# Deploy dashboard
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/master/src/deploy/recommended/kubernetes-dashboard.yaml

kubectl get pods --all-namespaces
kubectl get deployments --all-namespaces

# Deploy mysql
helm install stable/mysql
helm ls
```


