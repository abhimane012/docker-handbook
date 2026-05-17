# 📦 `FROM` Instruction in Dockerfile

## 🤔 What is `FROM`?

`FROM` specifies the base image for the Docker image.

It is usually the **first instruction** in a Dockerfile.

Docker starts building the image from this base image.

---

# 🧾 Basic Syntax

```dockerfile
FROM <image>
```

---

# ✅ Example

```dockerfile
FROM ubuntu
```

Uses the Ubuntu image as the base.

---

# 🏷️ Using Specific Version

```dockerfile
FROM python:3.12
```

Here:
- 📦 `python` → Image name
- 🏷️ `3.12` → Version/tag

---

# 🏗️ Multi-Stage Build Example

```dockerfile
FROM golang:1.24 AS builder
```

Here:
- `builder` → Stage name

---

# 🪶 Lightweight Base Image

```dockerfile
FROM alpine
```

`alpine` is a very small Linux image 💾

---

# 🚫 Scratch Image

```dockerfile
FROM scratch
```

`scratch` means:
- Empty base image
- No OS files
- Used for minimal containers

---

# ⚠️ Important Notes

- 📄 Every Dockerfile must start with `FROM`
- 🏷️ Always prefer fixed versions over `latest`
- 💾 Smaller base images reduce image size

---

# 📝 Common Examples

```dockerfile
FROM nginx
FROM ubuntu:24.04
FROM node:22
FROM python:3.12
FROM alpine
FROM scratch
```