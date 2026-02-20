# 🛒 Deploy Microservices Application on Kubernetes (Production & Security Best Practices)

## 📌 Project Overview
This project demonstrates deploying a **cloud-native microservices e-commerce application** to a **managed Kubernetes cluster (Linode LKE)** using production-ready and security-focused best practices.

The application consists of multiple independent microservices that communicate internally and are exposed via a frontend LoadBalancer service.

---

## 🚀 Technologies Used
- Kubernetes
- Linode LKE (Managed Kubernetes)
- Redis
- Docker containers
- Linux
- gRPC & HTTP health checks

---

## 🧱 Architecture Overview

### Microservices Deployed
- Frontend (public entry point)
- Checkout Service
- Product Catalog Service
- Recommendation Service
- Cart Service
- Redis (cart storage)
- Currency Service
- Payment Service
- Shipping Service
- Email Service
- Ad Service

### Service Communication
- Internal communication via **ClusterIP services**
- External access via **LoadBalancer (Frontend)**
- Redis used for cart persistence
- Services communicate using **gRPC & HTTP**

---

## ⚙️ Kubernetes Configuration

### Deployments
Each microservice includes:

✅ Containerized service  
✅ Replica configuration for high availability  
✅ Resource requests & limits  
✅ Environment variable configuration  
✅ Liveness & readiness probes  
✅ Label selectors for service discovery  

### Services
- **ClusterIP** → internal service communication
- **LoadBalancer** → expose frontend externally

---

## 🔐 Production & Security Best Practices Implemented

### ✔ High Availability
- Multiple replicas for critical services
- Stateless microservices design

### ✔ Health Monitoring
- Liveness probes restart unhealthy containers
- Readiness probes prevent traffic to unhealthy pods

### ✔ Resource Management
- CPU & memory requests prevent resource starvation
- Limits prevent noisy neighbor issues

### ✔ Network Security
- Internal services exposed only via ClusterIP
- Only frontend exposed externally

### ✔ Fault Tolerance
- Redis health checks ensure reliability
- Kubernetes self-healing replaces failed containers

---

## 📦 Redis Cart Storage
- Redis deployed inside cluster
- Persistent volume mount for data directory
- Used by cart service for session storage
