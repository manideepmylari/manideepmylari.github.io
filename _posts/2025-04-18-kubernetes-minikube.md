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


---

Running kubectl apply for a service without a deployment means that you've created a Kubernetes service, but there might not be any pods for the service to route traffic to. Essentially, the service exists, but it won't have any endpoints to direct traffic unless there are pods that match the service's selector.

If it worked without errors, it means Kubernetes accepted the service configuration. However, to make the service functional, you'll need to create a deployment or pods that the service can manage.


### **Solution Summary**:

2. **Accessing the Application**:
  - The `LoadBalancer` service required running `minikube tunnel` to create a network tunnel.
  - The correct URL to access the application  can be found by the `minikube service springboot-service --url` command.
  - ex `http://127.0.0.1:50491`

- **NodePort**: Exposes the application on a specific port on each Node. 
- **LoadBalancer**: Provides an external IP and port, accessible via `minikube tunnel`. 

Great job on deploying your Spring Boot application! Your YAML files look good. Here's a quick overview of what each part does:

### Deployment YAML
- **apiVersion**: Specifies the API version.
- **kind**: Defines the type of Kubernetes object, which is a Deployment.
- **metadata**: Contains the name of the deployment.
- **spec**: Defines the desired state of the deployment.
  - **replicas**: Specifies the number of pod replicas.
  - **selector**: Matches the pods with the label `app: springboot`.
  - **template**: Describes the pods to be created.
    - **metadata**: Labels the pods.
    - **spec**: Defines the container specifications.
      - **containers**: Lists the containers in the pod.
        - **name**: Names the container.
        - **image**: Specifies the container image.
        - **ports**: Defines the container port.

### Service YAML
- **apiVersion**: Specifies the API version.
- **kind**: Defines the type of Kubernetes object, which is a Service.
- **metadata**: Contains the name of the service.
- **spec**: Defines the desired state of the service.
  - **selector**: Matches the pods with the label `app: springboot`.
  - **ports**: Defines the service ports.
    - **protocol**: Specifies the protocol (TCP).
    - **port**: Defines the port on which the service is exposed.
    - **targetPort**: Specifies the port on the container to which traffic should be directed.
  - **type**: Specifies the service type (NodePort).

With these configurations, your service should route traffic to the Spring Boot pods on port 8080. If everything is set up correctly, you should be able to access your application via the NodePort.

kubectl get nodes -o wide


kubectl describe service springboot-service


