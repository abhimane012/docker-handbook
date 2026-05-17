# 💾 Disk Utilization of Docker Containers and Images

## 🤔 Why Does Docker Use Disk Space?

Docker stores:
- 📦 Images
- 🚀 Containers
- 📁 Volumes
- 🌐 Networks metadata
- 📝 Logs
- 📚 Image layers

Over time, Docker can consume a lot of disk space ⚠️

---

# 📦 Disk Usage by Docker Images

Docker images take disk space because they contain:
- 📄 Application code
- 📚 Libraries
- ⚙️ Runtime
- 🐧 OS filesystem

Example:

```bash
docker images
```

Output:

```bash
REPOSITORY   TAG       SIZE
ubuntu       latest    78MB
nginx        latest    192MB
```

Here:
- 📦 Ubuntu image uses `78MB`
- 📦 Nginx image uses `192MB`

---

# 🧱 Images Use Layers

Docker images are built using layers 📚

Example:

```text
Ubuntu Base Layer
        ↓
Python Layer
        ↓
Application Layer
```

Docker reuses layers to save disk space 💾

Example:
- Two Python apps can share same Ubuntu layer.

---

# 🚀 Disk Usage by Containers

Containers add a small writable layer ✍️ on top of images.

This layer stores:
- 📝 Logs
- 📂 Temporary files
- ⚙️ Runtime changes

Containers usually use less space than images.

---

# 📋 Check Docker Disk Usage

## 🧾 Main Command

```bash
docker system df
```

Example output:

```bash
TYPE            TOTAL     ACTIVE    SIZE
Images          5         2         1.2GB
Containers      3         1         120MB
Volumes         2         2         500MB
```

---

# 🔍 Detailed Disk Usage

```bash
docker system df -v
```

This shows:
- 📦 Individual image sizes
- 🚀 Container sizes
- 📁 Volume usage

---

# 📦 Check Image Sizes

```bash
docker images
```

Example:

```bash
REPOSITORY   TAG       SIZE
redis        latest    117MB
postgres     latest    438MB
```

---

# 🚀 Check Container Sizes

```bash
docker ps -s
```

Example output:

```bash
CONTAINER ID   SIZE
abc123         12MB
```

This size is usually:
- ✍️ Writable layer size
- NOT full image size

---

# 📁 Where Docker Stores Data?

On Linux 🐧:

```text
/var/lib/docker
```

Docker stores:
- 📦 Images
- 🚀 Containers
- 📚 Layers
- 📁 Volumes

---

# 🧹 Remove Unused Data

Docker may keep:
- Unused images
- Stopped containers
- Old build cache

These consume disk space ⚠️

---

# 🗑️ Remove Stopped Containers

```bash
docker container prune
```

---

# 🗑️ Remove Unused Images

```bash
docker image prune
```

---

# 🧹 Remove Everything Unused

```bash
docker system prune
```

This removes:
- 🗑️ Stopped containers
- 📦 Unused images
- 🌐 Unused networks
- 🧠 Build cache

---

# ⚠️ Remove Everything Including Unused Images

```bash
docker system prune -a
```

Be careful 🚨

This may delete many downloaded images.

---

# 📁 Volumes Can Use Huge Space

Docker volumes store persistent data 💾

Examples:
- 🗄️ Databases
- 📂 Uploaded files
- 📝 Application data

Check volumes:

```bash
docker volume ls
```

Remove unused volumes:

```bash
docker volume prune
```

---

# ⚙️ What Happens Internally?

## 📦 Images

Stored as:
- 📚 Read-only layers

---

## 🚀 Containers

Stored as:
- ✍️ Small writable layer
- Linked to image layers

---

## 💾 Overlay Filesystem

Docker commonly uses:

```text
overlay2
```

storage driver.

It combines:
- 📦 Image layers
- ✍️ Container writable layer

into one filesystem view.

---

# 🌍 Real-World Example

Suppose:
- Ubuntu image = `80MB`
- Python layer = `120MB`
- App layer = `20MB`

Final image:

```text
80 + 120 + 20 = 220MB
```

If another app uses same Ubuntu + Python layers:
- Docker reuses them ✅
- Saves disk space 💾

---

# 🚨 Common Beginner Mistakes

## ❌ 1. Forgetting Old Containers

Stopped containers still use disk space.

Check:

```bash
docker ps -a
```

---

## ❌ 2. Keeping Large Unused Images

Unused images can consume many GBs ⚠️

---

## ❌ 3. Ignoring Volumes

Volumes often become the biggest storage consumer.

Especially databases 🗄️

---

## ❌ 4. Using Huge Base Images

Example:

```text
ubuntu
```

may be larger than:

```text
alpine
```

Smaller images save:
- 💾 Disk space
- ⚡ Download time

---

# 📝 Quick Summary

| Command | Purpose |
|---|---|
| `docker system df` | 📋 Show Docker disk usage |
| `docker system df -v` | 🔍 Detailed disk usage |
| `docker images` | 📦 Show image sizes |
| `docker ps -s` | 🚀 Show container sizes |
| `docker system prune` | 🧹 Clean unused data |
| `docker image prune` | 🗑️ Remove unused images |
| `docker volume prune` | 📁 Remove unused volumes |

---

# 🎯 Final Understanding

```text
Docker Images 📦
        ↓
Use disk space for layers

Docker Containers 🚀
        ↓
Add writable layer

Volumes 📁
        ↓
Store persistent data
```

Over time, unused Docker resources can consume large amounts of storage 💾