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
cd monochart
helm repo add common https://kubernetes-charts-incubator.storage.googleapis.com/
helm repo add dockercfg https://charts.cloudposse.com/incubator/
helm dependency update
cd ..
```

## Run

Deploy the hello world server

```bash
kubectl apply -f hello-world.yml
kubectl get deployments
kubectl get services
kubectl get pods

curl localhost/hello-worldddd

kubectl delete -f hello-world.yml
```

Deploy and view the dashboard

```bash
kubectl apply -f https://raw.githubusercontent.com/kubernetes/dashboard/master/src/deploy/recommended/kubernetes-dashboard.yaml
open http://localhost:8001/api/v1/namespaces/kube-system/services/https:kubernetes-dashboard:/proxy/
kubectl proxy

kubectl delete -f https://raw.githubusercontent.com/kubernetes/dashboard/master/src/deploy/recommended/kubernetes-dashboard.yaml
```

Play with helm [COPIED FROM CLOUDPOSSE](https://github.com/cloudposse/charts)

```bash
helm install ./monochart -f values.yaml
helm ls
kubectl get deployments
kubectl get services
kubectl get pods

curl localhost/hello-worldddd

helm delete $(helm ls -q)
```
