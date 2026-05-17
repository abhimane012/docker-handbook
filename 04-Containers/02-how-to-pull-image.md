# 📥 How to Pull a Docker Image

## 🤔 What is "Pulling an Image"?

Pulling an image means downloading a Docker image from a remote registry (usually Docker Hub) to your local machine.

Think of it like downloading an app from an app store 📱

Docker images contain everything needed to run a container:
- 📦 Application code
- 📚 Libraries
- 🔧 Dependencies
- 🛠️ Required tools

---

# 🧾 Basic Command

```bash
docker pull <image-name>
```

---

# ✅ Example

```bash
docker pull nginx
```

This command downloads the official Nginx image from Docker Hub 🌐

---

# ⚙️ What Happens Internally?

When you run:

```bash
docker pull nginx
```

Docker:
1. 🌍 Connects to Docker Hub
2. 🔍 Finds the `nginx` image
3. 📥 Downloads all required layers
4. 💾 Stores the image locally

---

# 📋 Check Downloaded Images

```bash
docker images
```

Example output:

```bash
REPOSITORY   TAG       IMAGE ID       CREATED       SIZE
nginx        latest    abc123xyz      2 days ago    192MB
```

---

# 🏷️ Pull a Specific Version

```bash
docker pull nginx:1.27
```

Here:
- 📦 `nginx` → Image name
- 🏷️ `1.27` → Image tag/version

If no tag is provided, Docker uses:

```text
latest
```

by default.

---

# ⭐ Why Use Specific Versions?

Using a fixed version is better because:
- ✅ Your setup becomes stable
- 🚫 Avoids unexpected changes
- 🐞 Easier to debug problems

Example:

```bash
docker pull redis:7
```

---

# 🌐 Pull Images from Other Registries

Docker can also pull images from:
- 🔒 Private registries
- ☁️ Cloud registries
- 🏢 Company registries

Example:

```bash
docker pull ghcr.io/user/app:latest
```

---

# 🛠️ Useful Commands

## 📥 Pull Image

```bash
docker pull ubuntu
```

## 📋 List Images

```bash
docker images
```

## ❌ Remove Image

```bash
docker rmi ubuntu
```

---

# 🚨 Common Beginner Mistakes

## ❌ 1. Wrong Image Name

```bash
docker pull ngnix
```

This fails because the correct name is:

```bash
nginx
```

---

## 🌐 2. Internet Not Working

Docker needs internet access to download images.

---

## 🏷️ 3. Typing Wrong Tag

```bash
docker pull nginx:abc
```

This fails if the tag does not exist.

---

# 📝 Quick Summary

| Command | Purpose |
|---|---|
| `docker pull nginx` | 📥 Download image |
| `docker images` | 📋 List local images |
| `docker rmi nginx` | ❌ Remove image |
| `docker pull nginx:1.27` | 🏷️ Pull specific version |