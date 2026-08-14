# ☸️ Microservices on Kubernetes with Jenkins

A hands-on Kubernetes and CI/CD project demonstrating how a containerized microservices application can be deployed to an **Amazon EKS cluster using Jenkins and Kubernetes manifests**.

> **Portfolio focus:** Kubernetes • Amazon EKS • Docker • Jenkins • CI/CD • Microservices • Linux

---

## 🎯 Project Overview

This project focuses on the operational side of a microservices workload: packaging services as containers, defining Kubernetes workloads and services, deploying them to EKS, and verifying the deployment through a Jenkins pipeline.

The repository contains Kubernetes deployment/service definitions and a Jenkins pipeline that applies those manifests to an EKS cluster and verifies the resulting services.

## 🏗️ Architecture

```text
                         Developer
                             │
                             ▼
                        Git / GitHub
                             │
                             ▼
                          Jenkins
                             │
                    kubectl apply -f
                             │
                             ▼
                    ┌─────────────────┐
                    │   Amazon EKS    │
                    │                 │
                    │  Microservices  │
                    │  Deployments    │
                    │  + Services     │
                    └────────┬────────┘
                             │
                             ▼
                    Deployment Verification
```

## 🔄 CI/CD Workflow

```text
Developer pushes code/configuration
                ↓
        Jenkins pipeline starts
                ↓
     Connect to Kubernetes/EKS
                ↓
 kubectl apply -f deployment-service.yml
                ↓
 Kubernetes creates/updates workloads
                ↓
       Verify Kubernetes services
                ↓
       Application runs on EKS
```

The Jenkins pipeline contains deployment and verification stages. It uses Jenkins Kubernetes credentials and `kubectl` to apply the manifest and check Kubernetes services.

## ☸️ Kubernetes Implementation

The Kubernetes manifest demonstrates several production-oriented practices, including:

- Kubernetes Deployments
- ClusterIP Services
- Multiple microservices
- Readiness probes
- Liveness probes
- CPU/memory requests and limits
- Non-root container execution for selected workloads
- Dropped Linux capabilities
- Disabled privilege escalation
- Read-only root filesystem for selected workloads
- Internal service-to-service communication

The manifest includes workloads such as `emailservice`, `checkoutservice`, `recommendationservice`, and `frontend`, with health probes and resource configuration.

## 🛠️ Technology Stack

| Category | Technologies |
|---|---|
| Cloud | AWS, Amazon EKS |
| Kubernetes | Kubernetes, kubectl |
| CI/CD | Jenkins |
| Containers | Docker |
| Deployment | Kubernetes YAML |
| Source Control | Git, GitHub |
| OS / Automation | Linux, Shell |

## 📁 Repository Structure

```text
microservices-project/
├── Jenkinsfile
├── deployment-service.yml
└── README.md
```

### `Jenkinsfile`

Defines the deployment workflow used to apply the Kubernetes manifest to the EKS cluster and verify the deployed services.

### `deployment-service.yml`

Contains Kubernetes Deployments and Services for the microservices workload.

## 🔍 DevOps Skills Demonstrated

- Deploying workloads to Amazon EKS
- Kubernetes manifest management
- Jenkins-to-Kubernetes integration
- CI/CD-based Kubernetes deployment
- Kubernetes service discovery
- Application health checks
- Resource requests and limits
- Container security context configuration
- Microservices operational concepts
- Deployment verification and troubleshooting

## 💡 Interview Discussion Points

This project can be used to discuss:

- How Jenkins authenticates with an EKS cluster
- How `kubectl apply` performs declarative deployment
- Difference between Deployment and Service
- ClusterIP and internal service discovery
- Readiness vs liveness probes
- Kubernetes resource requests and limits
- Running containers as non-root
- Kubernetes troubleshooting when a pod is not Ready
- How to improve this pipeline with image scanning, immutable image tags, Helm, Argo CD, and automated rollback

## ⚠️ Production Improvements

The current repository demonstrates the core deployment workflow. A production-grade evolution would include:

- Immutable container image tags instead of `latest`
- Externalized configuration and secrets
- Image security scanning
- Helm or Kustomize
- GitOps with Argo CD
- Automated rollback
- CI validation and policy checks
- Centralized monitoring and logging

## 👨‍💻 Author

**Sandeep Reddy** — AWS Cloud & DevOps Engineer

Focused on AWS, Kubernetes, Docker, Terraform, Jenkins, Helm, GitOps, monitoring, security, and cloud automation.
