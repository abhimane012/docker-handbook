# 💾 Docker Volume Mount

## 🤔 What is a Volume Mount?

A volume mount connects a Docker volume to a directory inside a container.

It allows the container to:
- 💾 Store persistent data
- 🔄 Keep data even after container removal
- 📂 Share data between containers

Instead of storing data inside the container, Docker stores it outside the container lifecycle.

---

# 🧾 Basic Syntax

```bash
docker run -v <volume-name>:<container-path> <image>
```

or modern syntax:

```bash
docker run --mount source=<volume-name>,target=<container-path> <image>
```

---

# ✅ Example Using `-v`

```bash
docker run -v my-volume:/data nginx
```

Here:

- 💾 `my-volume` → Docker volume name
- 📂 `/data` → Folder inside container

Docker mounts the volume into `/data`.

---

# ✅ Example Using `--mount`

```bash
docker run --mount source=my-volume,target=/data nginx
```

This does the same thing but uses a clearer syntax.

---

# ⚙️ What Happens Internally?

When container starts:

1. 🔍 Docker checks if volume exists
2. 📁 Creates volume if missing
3. 🔗 Attaches volume to container path
4. 💾 Data is stored outside container

---

# 🧭 High-Level View

```text
Container 📦
     │
     │ writes data
     ↓
Mounted Path (/data)
     ↓
Docker Volume 💾
     ↓
Host Machine 🖥️
```

---

# 📋 Check Existing Volumes

```bash
docker volume ls
```

Example output:

```bash
DRIVER    VOLUME NAME
local     my-volume
```

---

# 🔍 Inspect Volume Details

```bash
docker volume inspect my-volume
```

Shows:
- 📁 Mount location
- ⚙️ Driver details
- 📝 Metadata

---

# 🗑️ Remove Volume

```bash
docker volume rm my-volume
```

---

# 🧪 Real Example with Database

```bash
docker run -d \
-v mysql-data:/var/lib/mysql \
mysql
```

Here:

- Database files go into volume 💾
- Data survives container deletion ✅

---

# 🔄 Share Same Volume Across Containers

```bash
docker run -v shared-data:/data nginx

docker run -v shared-data:/data ubuntu
```

Both containers use same storage 📂

---

# 🚨 Common Beginner Mistakes

## ❌ 1. Thinking Data Lives Inside Container

Container data may disappear after removal.

Use volumes for important data 💾

---

## ❌ 2. Removing Container Removes Data

```bash
docker rm my-container
```

Container removed ❌

Volume data still exists ✅

---

## ❌ 3. Forgetting to Clean Unused Volumes

Unused volumes consume disk space.

Remove them:

```bash
docker volume prune
```

---

# 📝 Quick Summary

| Command | Purpose |
|---|---|
| `docker volume ls` | 📋 List volumes |
| `docker volume inspect my-volume` | 🔍 Show details |
| `docker volume rm my-volume` | 🗑️ Remove volume |
| `docker volume prune` | 🧹 Remove unused volumes |

---

# 🎯 Final Understanding

```text
Container 📦
      ↓
Volume Mount 🔗
      ↓
Docker Volume 💾
      ↓
Persistent Data ✅
```

Volume mounts help keep data safe even when containers are deleted.