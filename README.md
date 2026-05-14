
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
        UI[Frontend Apps]
        DB[(Databases)]
    end

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
![GitHub Actions](https://img.shields.io/badge/GitHub_Actions-2088FF?style=for-the-badge\&logo=githubactions\&logoColor=white)

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

Typical local workflow:

```mermaid
flowchart LR

    CODE[Code Changes]
    BUILD[Docker Build]
    START[Compose Up]
    TEST[Test Services]
    DEBUG[Logs & Monitoring]

    CODE --> BUILD
    BUILD --> START
    START --> TEST
    TEST --> DEBUG
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
