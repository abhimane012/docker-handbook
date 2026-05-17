# 🗑️ How to Remove a Docker Container

## 🤔 What Does "Remove Container" Mean?

Removing a container means permanently deleting it from your system.

After removing:
- ❌ The container no longer exists
- 📦 The image still remains
- 🚀 You cannot start that container again

---

# 🧾 Basic Command

```bash
docker rm <container-id>
```

or

```bash
docker rm <container-name>
```

---

# ✅ Example Using Container ID

```bash
docker rm abc123
```

---

# ✅ Example Using Container Name

```bash
docker rm my-nginx
```

---

# 📋 Check All Containers

Before removing a container:

```bash
docker ps -a
```

Example output:

```bash
CONTAINER ID   IMAGE   NAMES       STATUS
abc123         nginx   my-nginx    Exited
```

---

# ⚠️ Important Rule

You cannot remove a running container.

First stop it:

```bash
docker stop my-nginx
```

Then remove it:

```bash
docker rm my-nginx
```

---

# 🚀 Stop and Remove in One Command

```bash
docker rm -f my-nginx
```

Here:
- `-f` → Force remove

Docker:
1. ⏹️ Stops the container
2. 🗑️ Removes it immediately

---

# 🧹 Remove Multiple Containers

```bash
docker rm container1 container2
```

Example:

```bash
docker rm my-nginx my-redis
```

---

# 🗑️ Remove All Stopped Containers

```bash
docker container prune
```

Docker asks for confirmation before deleting.

---

# ⚙️ What Happens Internally?

When you run:

```bash
docker rm my-nginx
```

Docker:
1. 🔍 Finds the container
2. 🗑️ Deletes container metadata
3. 💾 Frees container storage

The Docker image is NOT deleted.

---

# 📦 Difference Between Image and Container Removal

## 🗑️ Remove Container

```bash
docker rm my-nginx
```

Deletes only the container.

---

## 🗑️ Remove Image

```bash
docker rmi nginx
```

Deletes the image.

---

# 🚨 Common Beginner Mistakes

## ❌ 1. Trying to Remove Running Container

Wrong:

```bash
docker rm my-nginx
```

if container is running.

Correct:

```bash
docker stop my-nginx
docker rm my-nginx
```

or:

```bash
docker rm -f my-nginx
```

---

## ❌ 2. Confusing `rm` and `rmi`

- 🗑️ `docker rm` → Remove container
- 📦 `docker rmi` → Remove image

---

## ❌ 3. Thinking Image Gets Deleted Too

Removing a container does NOT remove the image.

---

# 📝 Quick Summary

| Command | Purpose |
|---|---|
| `docker ps -a` | 📋 Show all containers |
| `docker rm <id>` | 🗑️ Remove container |
| `docker rm -f <id>` | ⚡ Force remove running container |
| `docker stop <id>` | ⏹️ Stop container |
| `docker container prune` | 🧹 Remove all stopped containers |
| `docker rmi <image>` | 📦 Remove image |