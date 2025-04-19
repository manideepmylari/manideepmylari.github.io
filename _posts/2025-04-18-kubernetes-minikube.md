---
title: "Kubernetes"
date: 2025-04-18 20:00:00
categories: [ Miscellaneous ]
tags: [ Miscellaneous ]
---

{% include toc title="Index" %}

- Start Docker Desktop
- Start minikube
  ```shell
  minikube start
  ```
- pull the docker image
- deploy the docker image on k8s (Also start minikube TUNNEL)
    ```shell
    kubectl create deployment hello-service --image=nitinkc/k8s-helloworld
    kubectl expose deployment hello-service --type=LoadBalancer --port=4012 --target-port=8080
    kubectl scale deployment hello-service  --replicas=5
    minikube tunnel
    kubectl get svc
    kubectl scale deployment hello-service  --replicas=2
    ```
- Stop minikube
  ```shell
  minikube stop
  ```
- Stop docker