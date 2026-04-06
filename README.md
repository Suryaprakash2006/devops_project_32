# 🔐 Secure Cloud Deployment System

A modern cloud-native application deployment demonstrating **secure, scalable, and cost-effective architecture** using Kubernetes and Cloudflare.

---

## 🚀 Project Overview

This project showcases how to deploy an application securely on the cloud using:

* **Kubernetes** for orchestration
* **Docker** for containerization
* **NGINX Ingress** for routing
* **Cloudflare Tunnel** for secure exposure

It replaces traditional AWS WAF and Load Balancer with a **free and secure alternative**.

---

## 🏗️ Architecture

```
User
  ↓
Cloudflare Tunnel (Security Layer)
  ↓
NGINX Ingress (Routing)
  ↓
Kubernetes Service
  ↓
Pod (Application Container)
```

---

## 🧰 Technology Stack

* 🐳 Docker – Containerization
* ☸️ Kubernetes – Container orchestration
* 🌐 NGINX Ingress – Traffic routing
* 🔐 Cloudflare Tunnel – Secure access (WAF-like protection)
* ☁️ AWS EC2 – Infrastructure

---

## ⚙️ Implementation Steps

### 1. Setup EC2 & Install Docker

```bash
sudo apt update
sudo apt install docker.io -y
sudo systemctl start docker
```

### 2. Create & Run Application

```bash
npm install -g serve
serve -p 3000
```

### 3. Dockerize Application

```bash
docker build -t project-site .
docker run -d -p 3000:3000 project-site
```

### 4. Push to Docker Hub

```bash
docker tag project-site suryaprakash736/project-site
docker push suryaprakash736/project-site
```

### 5. Setup Kubernetes Cluster

* Install `kubeadm`, `kubelet`, `kubectl`
* Initialize cluster
* Install Calico network plugin

### 6. Deploy Application

```bash
kubectl apply -f deployment.yaml
kubectl apply -f service.yaml
```

### 7. Setup Ingress

```bash
kubectl apply -f ingress.yaml
```

### 8. Setup Cloudflare Tunnel

```bash
cloudflared tunnel --url http://localhost:32058 --http-host-header myapp.local
```

---

## 🔐 Security Features

* ✅ Cloudflare acts as **Web Application Firewall (WAF)**
* ✅ Protection against:

  * SQL Injection
  * Cross-Site Scripting (XSS)
  * DDoS attacks
* ✅ No direct public IP exposure
* ✅ HTTPS enabled automatically

---

## 💥 Attack Simulation

### 🔹 SQL Injection

```
?id=1' OR '1'='1
```

### 🔹 XSS

```
?q=<script>alert(1)</script>
```

### 🔹 DoS Simulation

```bash
for i in {1..10}; do curl https://your-link; done
```

---

## 📊 Results

* Application remained stable under simulated attacks
* No crashes or downtime
* Secure routing via Cloudflare Tunnel
* Clean architecture without exposing infrastructure

---

## ⚠️ Limitations

* Single-node Kubernetes cluster
* No custom WAF rules (Cloudflare free tier)
* Temporary tunnel (URL changes on restart)

---

## 🚀 Future Improvements

* Multi-node Kubernetes cluster
* Custom domain + full Cloudflare WAF rules
* Monitoring (Prometheus, Grafana)
* CI/CD pipeline integration

---

## 👨‍💻 Team

* Surya Prakash Ullamparthi
* Sai Praneeth Palakala
* Shashank Koduru

---

## 🧠 Key Takeaway

This project demonstrates how **secure cloud deployment can be achieved without expensive infrastructure**, using modern DevOps tools and smart architectural decisions.

---

⭐ If you found this project useful, consider giving it a star!
