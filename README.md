# 🛒 Kubernetes Microservices Deployment with Helm & Helmfile

Production-ready deployment of a distributed microservices application on Kubernetes using **Helm charts** and **Helmfile orchestration**.

This project demonstrates secure service exposure, replica-based availability, protocol-aware health checks, and modular release management — reflecting real-world cloud-native deployment practices.

---

## 📌 Project Overview

This repository deploys a cloud-native e-commerce microservices application to a Kubernetes cluster using:

- **Helm** for modular packaging  
- **Helmfile** for declarative multi-chart orchestration  
- Kubernetes Deployments & Services  
- Replica-based high availability  
- Protocol-aware health checks (gRPC, HTTP, TCP)  

The goal is not just to run containers — but to model production-style architecture patterns.

---

## 🧱 Architecture

The system consists of multiple independent microservices communicating internally via Kubernetes service discovery.

### 🔹 Traffic Flow

- External traffic enters through a **LoadBalancer** service.
- The **Frontend** routes requests internally via **ClusterIP** services.
- Backend services communicate using **gRPC and HTTP**.
- Redis supports cart session storage within the cluster.

### 🔹 Services Deployed

- Frontend (public entry point)
- Checkout Service
- Product Catalog Service
- Recommendation Service
- Cart Service
- Redis (cart session storage)
- Currency Service
- Payment Service
- Shipping Service
- Email Service
- Ad Service

---

## ⚙️ Deployment Strategy

Each service is deployed as a Kubernetes **Deployment** with:

- Replica configuration (2 replicas for core services)
- Liveness and readiness probes
- Environment-based service discovery
- Label selectors for routing
- Resource requests and limits (applied to selected services)

### Service Types

- `LoadBalancer` → Frontend (public access)
- `ClusterIP` → Internal services (secure internal communication)

---

## 🩺 Health Checks

Health probes are aligned with service protocols:

- gRPC probes for backend services
- HTTP probes for Frontend
- TCP socket probes for Redis

This enables Kubernetes self-healing and accurate availability checks.

---

## 📦 Helm Chart Structure

```
charts/
├── microservice/
│   ├── templates/
│   ├── Chart.yaml
│   └── values.yaml
├── redis/
│   ├── templates/
│   ├── Chart.yaml
│   └── values.yaml
```

- `microservice` chart packages application services  
- `redis` chart handles the stateful component  

This modular structure enables reusable deployments and environment-based customization.

---

## 📜 Helmfile Orchestration

Instead of installing charts manually, deployments are managed declaratively using **Helmfile**.

The entire stack is deployed with:

```bash
helmfile sync
```

Helmfile provides:

- Centralized multi-release management  
- Declarative infrastructure state  
- Reproducible deployments  
- Simplified upgrades and synchronization  

This mirrors production-style release management for multi-service applications.

---

## 🛟 High Availability & Fault Tolerance

- Core services run with multiple replicas  
- Kubernetes automatically replaces failed pods  
- Readiness probes prevent traffic to unhealthy containers  
- Redis uses in-cluster mounted storage (`emptyDir`) for cart session state  

> **Note:** `emptyDir` provides runtime storage. This can be upgraded to a PersistentVolumeClaim (PVC) for durable storage in production environments.

---

## 🎯 What This Project Demonstrates

- Distributed microservices deployment on Kubernetes  
- Secure service exposure strategy  
- Replica-based availability  
- Protocol-aware health monitoring  
- Helm-based modular packaging  
- Helmfile-driven orchestration  
- Stateful component integration  

---

## 🚀 Potential Improvements

- Add PersistentVolumeClaim (PVC) for Redis durability  
- Implement Horizontal Pod Autoscaling (HPA)  
- Add Ingress controller with TLS termination  
- Integrate Prometheus & Grafana for observability  
- Standardize resource policies across all services  

---

## 💡 Key Takeaway

Deploying containers is straightforward.  
Designing resilient, modular, production-aware systems requires architectural discipline.

This project reflects not just deployment — but structured system design using Kubernetes, Helm, and Helmfile.

---

## 👤 Author

**Priscilla Salvador**  
Cloud & DevOps Engineer
