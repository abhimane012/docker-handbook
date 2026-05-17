# 🌐 Introduction to Docker Networking

## 🤔 Why Do We Need Docker Networking?

Containers are isolated by default 🔒

This means:
- Containers cannot automatically talk to each other ❌
- Containers cannot automatically talk to the outside world ❌
- Users cannot access container applications directly ❌

Docker networking solves this problem by allowing communication between:

- 📦 Container ↔ Container
- 📦 Container ↔ Host machine
- 📦 Container ↔ Internet
- 📦 Container ↔ External systems

---

# 🎯 Goals of Docker Networking

Docker networking helps with:

- 🌐 Container communication
- 🔌 Exposing applications
- 🔄 Service discovery
- 🔒 Network isolation
- 🚀 Multi-container applications

---

# 🌍 Real-World Example

Suppose you have:

- 🌐 Frontend container
- ⚙️ Backend container
- 🗄️ Database container

For the application to work:

```text
Frontend → Backend → Database
```

All containers must communicate with each other.

Docker networking makes this possible ✅

---

# 🧭 High-Level View

```text
Container A 📦
      ↕
Docker Network 🌐
      ↕
Container B 📦
      ↕
Internet 🌍
```

---

# 🧱 Docker Network Types

Docker mainly provides:

1. 🌉 Bridge Network  
2. 🖥️ Host Network  
3. 🚫 None Network  
4. 🧩 Overlay Network  
5. 🌍 Macvlan Network  

(Topics explained separately)

---

# ⚙️ What Happens Internally?

When a container starts:

- Docker creates networking interfaces 🔌
- Assigns IP addresses 🌐
- Connects container to a network
- Configures routing and communication

---

# 📋 Useful Commands

## List Networks

```bash
docker network ls
```

---

## Inspect Network

```bash
docker network inspect <network-name>
```

---

## Create Network

```bash
docker network create my-network
```

---

# 📝 Quick Summary

- 📦 Containers are isolated by default
- 🌐 Docker networking enables communication
- 🔌 Helps containers talk to each other and outside systems
- 🚀 Required for multi-container applications
- 🧱 Docker provides multiple networking types