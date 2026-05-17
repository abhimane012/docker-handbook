# 🐳 Introduction to Docker

Docker is an open-source platform used to:
- 📦 Build applications
- 🚀 Run applications
- 📤 Deploy applications

inside containers.

Docker packages the application and all its dependencies together so the application works the same everywhere.

---

# 🧠 Why Docker?

Before Docker:
- ❌ Applications worked on one system but failed on another
- ❌ Dependency management was difficult
- ❌ Environment setup took a lot of time

With Docker:
- ✅ Same environment everywhere
- ✅ Faster deployment
- ✅ Lightweight containers
- ✅ Easy application sharing

---

# 📦 What is a Container?

A container is a lightweight package that contains:
- Application code
- Libraries
- Dependencies
- Configuration files

Containers run consistently across different systems.

---

# 🖥️ What is Docker Engine?

Docker Engine is the core component of Docker.

It is responsible for:
- 📦 Creating containers
- ▶️ Running containers
- 🛠️ Managing containers

Docker Engine works using:
- Docker CLI
- Docker API
- Docker Daemon

---

# ⚙️ Components of Docker Engine

## 1️⃣ Docker Daemon (`dockerd`)

The Docker daemon is a background service.

It:
- Builds containers
- Runs containers
- Manages Docker objects

---

## 2️⃣ Docker CLI

CLI stands for Command Line Interface.

It allows users to interact with Docker using commands.

### Example

```bash
docker ps
docker images
docker run nginx
```

---

## 3️⃣ Docker API

Docker API allows programs and tools to communicate with Docker.

---

# 🏷️ Docker CE and Docker EE

Docker Engine mainly had two editions.

---

# 1️⃣ Docker CE (Community Edition)

Docker CE is the free and open-source version of Docker.

## ✅ Features
- Free to use
- Good for beginners
- Community support

## 🌍 Used For
- Learning Docker
- Small projects
- Development environments

---

# 2️⃣ Docker EE (Enterprise Edition)

Docker EE was the enterprise version of Docker.

## ✅ Features
- Enterprise security
- Official support
- Advanced management features

## 🌍 Used For
- Large companies
- Production environments
- Enterprise applications

> Docker EE is now part of Mirantis after Docker sold its enterprise business.

---

# 💻 What is Docker Desktop?

Docker Desktop is an application that makes Docker easy to use on:
- Windows
- macOS

It includes:
- Docker Engine
- Docker CLI
- Docker Compose
- Kubernetes support

---

# 🚀 Features of Docker Desktop

- ✅ Easy graphical interface
- ✅ One-click Docker setup
- ✅ Integrated Kubernetes
- ✅ Easy container management

---

# 🧩 What is Docker Compose?

Docker Compose is a tool used to run multiple containers together.

Instead of starting containers one by one, Docker Compose uses a YAML file.

---

# 📄 Example

```yaml
version: '3'

services:
  web:
    image: nginx

  database:
    image: mysql
```

This file can start:
- 🌐 Web server
- 🗄️ Database

together using a single command.

---

# ▶️ Docker Compose Command

```bash
docker compose up
```

---

# 🌍 Why Use Docker Compose?

Docker Compose helps:
- Manage multi-container applications
- Simplify development
- Reduce manual work

---

# 🐝 What is Docker Swarm?

Docker Swarm is Docker’s native clustering and orchestration tool.

It allows multiple Docker machines to work together as a single system.

---

# ⚙️ Features of Docker Swarm

- 🔄 Load balancing
- 📈 Scaling containers
- 🛡️ High availability
- 🖥️ Cluster management

---

# 🧠 Simple Understanding

Imagine:
- One Docker host = one worker 👨‍💻
- Docker Swarm = team of workers 👨‍👩‍👧‍👦

All workers together run applications efficiently.

---

# 🏗️ Docker Swarm Components

## 1️⃣ Manager Node

Responsible for:
- Managing the cluster
- Scheduling containers
- Monitoring nodes

---

## 2️⃣ Worker Node

Responsible for:
- Running containers
- Executing tasks

---

# 📦 Docker Ecosystem Overview

| Tool | Purpose |
|---|---|
| Docker Engine | Runs containers |
| Docker Desktop | Easy Docker application for Windows/macOS |
| Docker Compose | Manages multi-container apps |
| Docker Swarm | Container orchestration and clustering |

---

# ⚖️ Docker Swarm vs Kubernetes

| Docker Swarm | Kubernetes |
|---|---|
| Easy to learn | More complex |
| Simple setup | Advanced features |
| Docker native | Industry standard orchestration |
| Good for small setups | Good for large-scale systems |

---

# 📝 Key Points to Remember

- 🐳 Docker is used to build and run containers
- 📦 Containers package applications and dependencies together
- ⚙️ Docker Engine is the core runtime
- 💻 Docker Desktop makes Docker easy on Windows/macOS
- 🧩 Docker Compose manages multiple containers
- 🐝 Docker Swarm manages clusters of Docker hosts
- 🚀 Docker improves portability and deployment