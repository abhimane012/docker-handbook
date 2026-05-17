# 🚀 Docker Container Creation Workflow

## 🤔 What Happens When We Run a Container?

When you run:

```bash
docker run nginx
```

many components work together behind the scenes to create and start the container.

Docker does NOT create containers alone.

It uses:
- 🐳 Docker CLI
- 🔌 Docker API
- ⚙️ Docker Daemon
- 📦 containerd
- 🏃 runc
- 📁 OCI Bundle
- 🧩 Namespaces
- 📊 Cgroups
- 🛠️ libcontainer

---

# 🧭 High-Level Workflow

```text
Docker CLI
    ↓
Docker API
    ↓
Docker Daemon (dockerd)
    ↓
containerd
    ↓
containerd-shim
    ↓
runc
    ↓
Linux Kernel Features
(namespaces + cgroups)
    ↓
Container Starts 🚀
```

---

# 🖥️ Step 1: Docker CLI

Command:

```bash
docker run nginx
```

The Docker CLI:
- 📥 Takes your command
- 📤 Sends request to Docker Daemon

The CLI itself does NOT create containers.

---

# 🔌 Step 2: Docker API Call

The Docker CLI communicates with Docker Daemon using:
- REST API
- Unix socket

Example socket:

```text
/var/run/docker.sock
```

Think of it like:
- 🧑 User gives order
- 📞 API sends message to Docker engine

---

# ⚙️ Step 3: Docker Daemon (`dockerd`)

Docker Daemon is the main background service.

Its job:
- 📦 Manage images
- 🚀 Manage containers
- 🌐 Manage networks
- 💾 Manage volumes

`dockerd` receives the API request and starts container creation.

---

# 📦 Step 4: containerd

Docker uses **containerd** to manage the container lifecycle.

containerd handles:
- 📥 Pulling images
- 💾 Image storage
- 🚀 Container execution
- ⏹️ Starting/stopping containers

Think of containerd as:
> 📦 A container manager

Docker tells containerd:
> "Please create this container."

---

# 🔄 Step 5: containerd-shim

containerd creates a small helper process called:

```text
containerd-shim
```

Its job:
- 🔗 Keep container running
- 📝 Handle container IO
- 🔄 Manage container independently

Why needed?
- If Docker daemon crashes ❌
- Container still keeps running ✅

---

# 🏃 Step 6: runc

containerd uses:

```text
runc
```

to actually create the container.

`runc` is a lightweight OCI runtime.

Its job:
- 📁 Read OCI bundle
- 🧩 Create namespaces
- 📊 Apply cgroups
- 🚀 Start container process

Think of runc as:
> 🏗️ The actual container builder

---

# 📁 Step 7: OCI Bundle

Before starting the container, Docker creates an:

```text
OCI Bundle
```

OCI = Open Container Initiative

The bundle contains:
- 📄 `config.json`
- 📂 Root filesystem
- ⚙️ Runtime configuration

Example:

```text
bundle/
├── config.json
└── rootfs/
```

The OCI bundle tells runc:
- Which process to run
- What filesystem to use
- Which namespaces to create
- Resource limits

---

# 🧩 Step 8: Namespaces

Namespaces provide isolation 🔒

They make the container think:
> "I have my own system."

Types of namespaces:

| Namespace | Purpose |
|---|---|
| PID | 🆔 Separate processes |
| NET | 🌐 Separate networking |
| MNT | 📁 Separate filesystem mounts |
| IPC | 💬 Separate inter-process communication |
| UTS | 🖥️ Separate hostname |
| USER | 👤 Separate users/IDs |

Example:
- Container cannot see host processes easily.

---

# 📊 Step 9: Cgroups

Cgroups = Control Groups

They limit resource usage.

Cgroups control:
- 🧠 CPU usage
- 💾 Memory usage
- 📀 Disk IO
- 🌐 Network usage

Example:
- Prevent one container from using all RAM.

---

# 🛠️ Step 10: libcontainer

`runc` internally uses:

```text
libcontainer
```

libcontainer is a Go library.

Its job:
- 🧩 Work with namespaces
- 📊 Configure cgroups
- ⚙️ Interact with Linux kernel

Think of it as:
> 🔧 The low-level engine behind runc

---

# 🎉 Final Result

After all setup:
- 📦 Filesystem is mounted
- 🧩 Isolation is created
- 📊 Limits are applied
- 🚀 Main application process starts

Example:

```bash
nginx
```

Now the container is running 🎉

---

# 🧠 Important Roles Summary

| Component | Role |
|---|---|
| Docker CLI | 🖥️ Takes user command |
| Docker API | 🔌 Communication layer |
| dockerd | ⚙️ Main Docker daemon |
| containerd | 📦 Container lifecycle manager |
| containerd-shim | 🔄 Keeps container alive |
| runc | 🏃 Creates and starts container |
| OCI Bundle | 📁 Runtime configuration |
| Namespaces | 🔒 Isolation |
| Cgroups | 📊 Resource limits |
| libcontainer | 🛠️ Kernel interaction library |

---

# 📌 Simple Real-World Analogy

| Docker Part | Real-World Example |
|---|---|
| Docker CLI | 🧑 Customer placing order |
| Docker API | 📞 Phone call |
| dockerd | 🏢 Restaurant manager |
| containerd | 👨‍🍳 Kitchen supervisor |
| runc | 🍳 Chef cooking food |
| OCI Bundle | 📜 Recipe |
| Namespaces | 🚪 Private room |
| Cgroups | 🍽️ Food portion control |
| Container | 🍔 Final meal |

---

# 📝 Quick Summary

```text
docker run nginx
        ↓
Docker CLI
        ↓
Docker API
        ↓
dockerd
        ↓
containerd
        ↓
containerd-shim
        ↓
runc
        ↓
OCI Bundle
        ↓
Namespaces + Cgroups
        ↓
Container Starts 🚀
```