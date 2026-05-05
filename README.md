# Roboshop Deployment on Kubernetes (K8s)

This repository demonstrates deploying the **Roboshop microservices application** on a Kubernetes cluster using YAML manifests.

It showcases how to manage, scale, and expose a multi-service application using Kubernetes — a core skill for DevOps and Site Reliability Engineering roles.

---

## Project Overview

Roboshop is a **microservices-based e-commerce application** consisting of services like:

- Web (Frontend)
- Catalogue
- User
- Cart
- Shipping
- Payment
- Dispatch

Each service is containerized and deployed as Kubernetes workloads, enabling scalability and high availability.

---

## Architecture

The application follows a Kubernetes-based architecture:

- Each service runs as a **Deployment (Pods)**
- Services are exposed via **ClusterIP / NodePort / LoadBalancer**
- Databases like MongoDB, MySQL, Redis, and RabbitMQ support backend services
- Internal communication happens via Kubernetes Services

---

## Tech Stack

- Kubernetes
- Docker (Container Images)
- YAML (K8s Manifests)
- kubectl CLI
- Linux

---

## Key Concepts Covered

- Kubernetes Deployments
- Pod lifecycle & scaling
- Service types (ClusterIP, NodePort, LoadBalancer)
- Ingress (for routing external traffic)
- ConfigMaps & Secrets (if used)
- Persistent storage (PVC)

---

## Setup & Execution

### Start Kubernetes Cluster

- Minikube / Kind / Cloud Kubernetes (EKS, AKS, GKE)

---

### Apply Namespace

```bash
kubectl apply -f namespace.yaml
```

---

### Deploy All Services

```bash
kubectl apply -f .
```

---

### Verify Resources

```bash
kubectl get pods
kubectl get svc
kubectl get deployments
```

---

### Access Application

```bash
kubectl get svc web
```

Then open:

```
http://<node-ip>:<node-port>
```

---

## Example Deployment

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: catalogue
spec:
  replicas: 2
  selector:
    matchLabels:
      app: catalogue
  template:
    metadata:
      labels:
        app: catalogue
    spec:
      containers:
      - name: catalogue
        image: catalogue:v1
        ports:
        - containerPort: 8080
```

---

## Example Service

```yaml
apiVersion: v1
kind: Service
metadata:
  name: catalogue
spec:
  selector:
    app: catalogue
  ports:
    - port: 80
      targetPort: 8080
  type: ClusterIP
```

---

## Key Features

- Microservices deployment on Kubernetes
- Scalable and self-healing architecture
- Service discovery and networking
- Declarative infrastructure using YAML
- Real-world DevOps use case

---

## Learning Outcomes

Through this project, I gained hands-on experience in:

- Deploying applications on Kubernetes
- Managing containerized workloads
- Understanding service networking
- Scaling and troubleshooting pods

---

## Future Enhancements

- Use Helm charts for templating
- Add Horizontal Pod Autoscaler (HPA)
- Integrate CI/CD pipeline
- Deploy on AWS EKS

---

## Note

This project is part of my DevOps learning journey, focusing on deploying real-world microservices applications using Kubernetes.

