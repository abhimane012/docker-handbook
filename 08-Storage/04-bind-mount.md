# 🔗 Docker Bind Mount

## 🤔 What is a Bind Mount?

A bind mount connects a folder or file from your **host machine** directly into a container.

Instead of Docker creating and managing storage, you provide the exact path from your system.

This allows:
- 📂 Sharing files between host and container
- ⚡ Live file updates
- 💻 Easier development workflow

---

# 🧾 Basic Syntax

```bash
docker run -v <host-path>:<container-path> <image>
```

or modern syntax:

```bash
docker run --mount type=bind,source=<host-path>,target=<container-path> <image>
```

---

# ✅ Example Using `-v`

```bash
docker run -v /home/user/project:/app nginx
```

Here:

- 🖥️ `/home/user/project` → Folder on host machine
- 📂 `/app` → Folder inside container

Docker connects both folders 🔗

---

# ✅ Example Using `--mount`

```bash
docker run --mount type=bind,source=/home/user/project,target=/app nginx
```

This does the same thing using a more readable syntax.

---

# ⚙️ What Happens Internally?

When container starts:

1. 🔍 Docker checks host path
2. 🔗 Mounts host folder into container
3. 📂 Container directly uses host files

No Docker-managed volume is created.

---

# 🧭 High-Level View

```text
Host Folder 🖥️
(/home/user/project)
        ↓
Bind Mount 🔗
        ↓
Container Folder 📦
(/app)
```

Both locations point to the same files.

---

# ✍️ Live Update Example

Host machine:

```text
index.html
```

Mounted into:

```text
/app/index.html
```

If you edit file on host:

```text
Hello Docker
```

Container immediately sees changes ✅

No restart needed.

---

# 💻 Common Use Cases

- 👨‍💻 Development environments
- 📂 Share source code
- 📝 Edit files without rebuilding image
- ⚡ Live code updates

---

# 📁 Mount Single File Example

```bash
docker run -v /home/user/config.json:/app/config.json nginx
```

This mounts one file instead of a directory.

---

# 🔒 Read-Only Bind Mount

```bash
docker run -v /home/user/project:/app:ro nginx
```

`ro` means:

```text
read-only
```

Container can read files 👀  
Container cannot modify files ✍️❌

---

# 🚨 Common Beginner Mistakes

## ❌ 1. Host Path Does Not Exist

Wrong:

```bash
docker run -v /abc/xyz:/app nginx
```

If path is invalid, Docker may create unexpected directories.

---

## ❌ 2. Accidentally Modifying Host Files

Container changes can directly affect your local files ⚠️

---

## ❌ 3. Confusing Bind Mount and Volume

- 📁 Volume → Managed by Docker
- 🔗 Bind Mount → Uses host path directly

---

# 🔄 Bind Mount vs Volume

| Feature | Bind Mount 🔗 | Volume 📁 |
|---|---:|---:|
| Managed by Docker | ❌ | ✅ |
| Uses Host Path | ✅ | ❌ |
| Great for Development | ✅ | ❌ |
| Great for Databases | ❌ | ✅ |

---

# 📝 Quick Summary

| Command | Purpose |
|---|---|
| `-v /host:/container` | 🔗 Create bind mount |
| `--mount type=bind...` | 📂 Modern syntax |
| `:ro` | 🔒 Read-only access |

---

# 🎯 Final Understanding

```text
Host Folder 🖥️
      ↓
Bind Mount 🔗
      ↓
Container Folder 📦
```

Bind mounts directly connect your machine files with the container for easy sharing and live updates.