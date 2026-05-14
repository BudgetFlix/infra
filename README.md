
<br />
<div align="center">

<h3 align="center">BudgetFlix Infra</h3>

  <p align="center">
    Infrastructure and local development environment for the BudgetFlix ecosystem.
    <br />
    <br />
    <a href="https://github.com/BudgetFlix/infra">View Repository</a>
    ·
    <a href="https://github.com/BudgetFlix/infra/issues">Report Bug</a>
    ·
    <a href="https://github.com/BudgetFlix/infra/issues">Request Feature</a>
  </p>
</div>

---

<!-- TABLE OF CONTENTS -->
<details>
  <summary>📚 Table of Contents</summary>
  <ol>
    <li>
      <a href="#about-the-project">About The Project</a>
    </li>
    <li>
      <a href="#infrastructure-overview">Infrastructure Overview</a>
    </li>
    <li>
      <a href="#built-with">Built With</a>
    </li>
    <li>
      <a href="#getting-started">Getting Started</a>
      <ul>
        <li><a href="#prerequisites">Prerequisites</a></li>
        <li><a href="#installation">Installation</a></li>
      </ul>
    </li>
    <li><a href="#services">Services</a></li>
    <li><a href="#development-workflow">Development Workflow</a></li>
    <li><a href="#roadmap">Roadmap</a></li>
  </ol>
</details>

---

# About The Project

BudgetFlix Infra contains the infrastructure configuration and local orchestration environment used across the BudgetFlix ecosystem.

This repository is responsible for:

- Local development environments
- Docker orchestration
- Service networking
- RabbitMQ setup
- Shared infrastructure services
- Environment configuration
- Future deployment automation

The goal of this repository is to provide a reproducible and scalable development environment for all BudgetFlix services.

---

# Infrastructure Overview

```mermaid
flowchart TD

    DEV[Developer Machine]

    subgraph Docker Environment
        MQ[RabbitMQ]
        API[Gateway / API]
        WORKER[Workers]
    end
        DB[(Databases)]

    DEV --> UI
    UI --> API
    API --> MQ
    MQ --> WORKER
    WORKER --> DB
````

---

# Built With

<div align="left">

![Docker](https://img.shields.io/badge/Docker-2496ED?style=for-the-badge\&logo=docker\&logoColor=white)
![Docker Compose](https://img.shields.io/badge/Docker_Compose-2496ED?style=for-the-badge\&logo=docker\&logoColor=white)
![RabbitMQ](https://img.shields.io/badge/RabbitMQ-FF6600?style=for-the-badge\&logo=rabbitmq\&logoColor=white)
![Linux](https://img.shields.io/badge/Linux-FCC624?style=for-the-badge\&logo=linux\&logoColor=black)


</div>

---

# Getting Started

## Prerequisites

Before starting make sure you have:

* Docker
* Docker Compose
* Git

---

## Installation

Clone the repository:

```bash
git clone https://github.com/BudgetFlix/infra.git
```

Enter the project:

```bash
cd infra
```

Start infrastructure services:

```bash
docker compose up -d
```

Check running containers:

```bash
docker ps
```

---

# Services

Current and planned infrastructure services:

| Service           | Purpose                    |
| ----------------- | -------------------------- |
| RabbitMQ          | Queue-based communication  |
| Gateway           | API routing and entrypoint |
| Worker Containers | Background processing      |
| Databases         | Persistent storage         |
| Monitoring Stack  | Metrics and logging        |
| Reverse Proxy     | Traffic management         |

---

# Development Workflow

The infrastructure repository follows a centralized container workflow.

Whenever changes are pushed to the `main` branch of a service repository:

1. GitHub Actions automatically builds the Docker image
2. The image is pushed to the container registry
3. The infrastructure stack can pull the latest image
4. Updated services are deployed through Docker Compose

```mermaid
flowchart LR

    CODE[Code Changes]
    PUSH[Push To Main]
    ACTIONS[GitHub Actions]
    BUILD[Docker Image Build]
    REGISTRY[Container Registry]
    INFRA[Infra Docker Compose]
    DEPLOY[Updated Services]

    CODE --> PUSH
    PUSH --> ACTIONS
    ACTIONS --> BUILD
    BUILD --> REGISTRY
    REGISTRY --> INFRA
    INFRA --> DEPLOY
```
Typical deployment update:

```bash
docker compose pull
docker compose up -d
```

---

# Roadmap

* [x] Docker Compose setup
* [x] RabbitMQ integration
* [x] Shared Docker networking
* [ ] Monitoring stack
* [ ] Centralized logging
* [ ] Production deployment configs
* [ ] Kubernetes manifests
* [ ] CI/CD integration
* [ ] Multi-environment support
* [ ] Secret management
* [ ] Infrastructure automation

---

<div align="center">
Infrastructure powering the BudgetFlix ecosystem ⚙️
</div>
