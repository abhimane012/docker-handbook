# 📦 What is a Docker Image?

## 🤔 Simple Definition

A Docker image is a **read-only template** used to create containers.

It contains everything needed to run an application:
- 📄 Application code
- 📚 Libraries
- 🔧 Dependencies
- ⚙️ Runtime
- 🛠️ Tools

Think of it like:
- 📦 Image = Blueprint/template
- 🚀 Container = Running instance of that image

---

# 🎂 Real-World Analogy

| Docker Concept | Real-World Example |
|---|---|
| 📦 Image | Cake recipe |
| 🚀 Container | Actual baked cake |

You can create many cakes 🍰 from the same recipe 📄

Similarly:
- One Docker image can create multiple containers.

---

# 🧾 Example

## Pull an Image

```bash
docker pull nginx
```

This downloads the Nginx image 📥

---

## Run a Container from Image

```bash
docker run nginx
```

Docker creates a running container using the image 🚀

---

# ⚙️ What Does an Image Contain?

A Docker image usually contains:

```text
Application
+ Dependencies
+ Libraries
+ Runtime
+ OS Files
```

Example:
- Python image contains:
  - 🐍 Python runtime
  - 📚 Required system libraries
  - ⚙️ Basic Linux filesystem

---

# 🧱 Images Are Built in Layers

Docker images use layers 📚

Example:

```text
Ubuntu Layer
   ↓
Python Layer
   ↓
Application Layer
```

Benefits:
- ⚡ Faster downloads
- 💾 Saves storage
- 🔄 Reuse existing layers

---

# 📋 Check Local Images

```bash
docker images
```

Example output:

```bash
REPOSITORY   TAG       IMAGE ID
nginx        latest    abc123
ubuntu       24.04     xyz789
```

---

# 🏷️ Image Name and Tag

Example:

```bash
nginx:latest
```

Here:
- 📦 `nginx` → Image name
- 🏷️ `latest` → Tag/version

---

# 🌐 Where Do Images Come From?

Images are usually downloaded from:
- 🌍 Docker Hub
- ☁️ Cloud registries
- 🏢 Private company registries

---

# 🛠️ Common Docker Image Commands

## 📥 Pull Image

```bash
docker pull nginx
```

---

## 📋 List Images

```bash
docker images
```

---

## 🗑️ Remove Image

```bash
docker rmi nginx
```

---

# 🔒 Images Are Read-Only

Docker images cannot change while running.

When a container starts:
- Docker adds a writable layer ✍️
- Changes happen inside container layer

The original image remains unchanged 📦

---

# 🔄 Image vs Container

| Docker Image 📦 | Docker Container 🚀 |
|---|---|
| Template | Running instance |
| Read-only | Writable |
| Static | Running process |
| Used to create containers | Created from image |

---

# ⚙️ What Happens Internally?

When you run:

```bash
docker run nginx
```

Docker:
1. 🔍 Finds the image locally
2. 📥 Pulls it if missing
3. 📦 Creates writable layer
4. 🚀 Starts container process

---

# 🚨 Common Beginner Mistakes

## ❌ 1. Confusing Image and Container

- 📦 Image = Template
- 🚀 Container = Running app

---

## ❌ 2. Thinking Changes Modify Image

Changes inside container do NOT automatically update image.

You must create a new image using:

```bash
docker commit
```

or Dockerfile.

---

## ❌ 3. Using `latest` in Production

```bash
nginx:latest
```

can change anytime ⚠️

Better:

```bash
nginx:1.27
```

---

# 📝 Quick Summary

| Command | Purpose |
|---|---|
| `docker pull nginx` | 📥 Download image |
| `docker images` | 📋 List images |
| `docker rmi nginx` | 🗑️ Remove image |
| `docker run nginx` | 🚀 Create container from image |

---

# 🎯 Final Understanding

```text
Docker Image 📦
        ↓
Used to create
        ↓
Docker Container 🚀
```

Without images, containers cannot exist.