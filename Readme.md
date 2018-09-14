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

Deploy the hello world server:

```bash
kubectl apply -f hello-world.yml
kubectl get deployments
kubectl get services
kubectl get pods

curl localhost/hello-worldddd

kubectl delete -f hello-world.yml
```

Deploy and view the dashboard:

```bash
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/master/src/deploy/recommended/kubernetes-dashboard.yaml
open http://localhost:8001/api/v1/namespaces/kube-system/services/https:kubernetes-dashboard:/proxy/
kubectl proxy

kubectl delete -f https://raw.githubusercontent.com/kubernetes/dashboard/master/src/deploy/recommended/kubernetes-dashboard.yaml
```

Play with helm:

```bash
# Add CloudPosse-Incubator repo
helm repo add cpi https://charts.cloudposse.com/incubator/

# Install the chart
helm install cpi/monochart -f values.yml

# Look around
helm ls
kubectl get deployments
kubectl get services
kubectl get pods

# Curl
curl localhost/hello-worldddd

# Cleanup
helm delete $(helm ls -q)
```
