# Experiment 07: Kubernetes Deployment and Management

## Aim
To deploy and manage a containerized Flask application using Kubernetes.

## Technologies Used
- Docker
- Kubernetes
- Minikube
- kubectl
- Flask

## Project Files
- `deployment.yaml` – Defines the application deployment and replicas.
- `service.yaml` – Exposes the application using a NodePort service.

## Kubernetes Setup

```bash
minikube start --driver=docker
kubectl get nodes
```

## Load Docker Image

```bash
minikube image load mywebapp:2.0
```

## Deploy the Application

```bash
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
```

## Verify Resources

```bash
kubectl get deployments
kubectl get pods
kubectl get services
```

## Access the Application

```bash
minikube service mywebapp-service --url
```

Keep the terminal open while using the generated URL on Windows with the Docker driver.

## Scaling

```bash
kubectl scale deployment mywebapp-deployment --replicas=4
kubectl get deployments
kubectl get pods
```

## Self-Healing

Delete one pod using its actual name from `kubectl get pods`:

```bash
kubectl delete pod <pod-name>
kubectl get pods
```

Kubernetes should create a replacement pod to maintain the desired replica count.

## Conclusion

This experiment demonstrates deploying a Flask application using Kubernetes, exposing it through a NodePort service, scaling replicas, and observing pod self-healing.