# 🔄 Emart GitOps Repository
![GitOps](https://img.shields.io/badge/Model-GitOps-green?style=for-the-badge)
![ArgoCD](https://img.shields.io/badge/CD-ArgoCD-orange?logo=argo&style=for-the-badge)
![Kubernetes](https://img.shields.io/badge/Platform-Kubernetes-blue?logo=kubernetes&style=for-the-badge)
![IaC](https://img.shields.io/badge/IaC-Kubernetes%20YAML-blueviolet?style=for-the-badge)
![Monitoring](https://img.shields.io/badge/Observability-Prometheus%20%7C%20Grafana-red?style=for-the-badge)
![License](https://img.shields.io/github/license/josephmj0303/emart-gitops?style=for-the-badge)

This repository contains **Kubernetes manifests** for deploying the Emart application using a **GitOps workflow with ArgoCD**.
## 📦 Project Components

- 🚀 App + CI Pipeline: https://github.com/josephmj0303/emart-devops-platform  
- 🔄 GitOps + Kubernetes: https://github.com/josephmj0303/emart-gitops  
---

## 🧠 Purpose

This repo acts as the **single source of truth for cluster state**.

All deployments are automated via:

```
GitHub Actions (CI) → Updates this repo → ArgoCD syncs → Kubernetes updated
```

---

## 🔗 Application Source Repository

This repository is part of a larger DevOps system.

👉 Application source code, CI pipeline, and Docker builds are handled in:

➡️ https://github.com/josephmj0303/emart-devops-platform

---

### 🔁 GitOps Flow

```text
Application Repo (CI Pipeline)
        ↓
Docker Images Built & Pushed
        ↓
This GitOps Repo Updated
        ↓
ArgoCD Detects Change
        ↓
Kubernetes Cluster Updated
```

---

## 📁 Repository Structure

```
k8s/
├── frontend/
├── node-api/
├── java-api/
├── databases/
│   ├── mongo/
│   └── mysql/
├── ingress/
├── monitoring/
└── observability-addons/
```

---

## ☸️ Kubernetes Components

### Applications

* Frontend (Angular via Nginx)
* Node API (Node.js)
* Java API (Spring Boot)

---

### Databases

* MongoDB (for Node API)
* MySQL (for Java API)

---

### Ingress

* Managed via Traefik
* Routes:

  * `/` → frontend
  * `/api` → node-api
  * `/webapi` → java-api

---

### Monitoring

* Grafana Ingress
* Prometheus Ingress
* Alertmanager config

---

### Observability Add-ons

* Slack alert integration proxy

---

## 🔄 GitOps Workflow

1. Developer pushes code to app repo
2. CI builds and pushes Docker images
3. CI updates image tags in this repo
4. ArgoCD detects changes
5. Cluster auto-syncs

---

## 🧪 Example Image Update

```yaml
image: yourname/emart-node-api:abc1234
```

---

## 🚀 ArgoCD Configuration

* Auto Sync: Enabled
* Self Heal: Enabled
* Prune: Enabled

---

## 🌐 Ingress Configuration

Example:

```yaml
host: yourdomain.com
```

Subdomains:

* grafana.yourdomain.com
* prometheus.yourdomain.com

---

## 🔐 Secrets Management (Current)

Currently using:

* Environment variables (basic)

Planned:

* Kubernetes Secrets
* External Secrets / Vault

---

## 📊 Monitoring Stack

* Prometheus
* Grafana
* Alertmanager

---

## 🚨 Alerts

Configured for:

* High CPU usage
* Pod restarts
* Node health

Slack integration available via:

```
observability-addons/slack/
```

---

## 🧠 Design Principles

* Declarative infrastructure
* Immutable deployments
* Git as single source of truth
* Automated reconciliation (ArgoCD)

---

## 📌 Future Improvements

* Helm/Kustomize standardization
* Secret management upgrade
* Multi-environment overlays (dev/stage/prod)
* Canary deployments

---

## 📜 License

MIT License
