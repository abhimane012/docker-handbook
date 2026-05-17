# 📁 Check Docker Root Directory Status

## 🤔 Why Check Docker Root Directory?

Docker stores all its data inside the Docker root directory:

```text
/var/lib/docker
```

or your custom path if changed.

Checking it helps you:

- 💾 Monitor disk usage
- 🔍 Verify current Docker location
- 📦 Check storage consumption
- ⚠️ Detect low disk space issues

---

# 📋 Check Current Docker Root Directory

Run:

```bash
docker info | grep "Docker Root Dir"
```

Example output:

```text
Docker Root Dir: /var/lib/docker
```

or:

```text
Docker Root Dir: /data/docker
```

---

# 💾 Check Disk Usage of Docker Root Directory

```bash
sudo du -sh /var/lib/docker
```

Example output:

```text
15G    /var/lib/docker
```

Meaning:

- Docker currently uses `15GB`

---

# 📊 Check Disk Space Availability

```bash
df -h
```

Example:

```bash
Filesystem      Size   Used   Avail
/dev/sda1       100G    85G     15G
```

Shows:
- 💾 Total disk size
- 📦 Used space
- ✅ Available space

---

# 🔍 Check Detailed Docker Usage

```bash
docker system df
```

Example:

```bash
TYPE            TOTAL     ACTIVE     SIZE
Images          10        3          2GB
Containers      5         2          400MB
Volumes         3         3          5GB
```

Shows Docker storage usage.

---

# 🔎 Detailed Breakdown

```bash
docker system df -v
```

Shows:

- 📦 Individual image size
- 🚀 Container usage
- 💾 Volume usage

---

# 🧭 High-Level View

```text
Docker Root Directory 📁
        ↓
Images 📦
Containers 🚀
Volumes 💾
Networks 🌐
Logs 📝
```

---

# 🚨 Common Beginner Mistakes

## ❌ 1. Using `du` on Wrong Path

If Docker root changed:

Wrong:

```bash
du -sh /var/lib/docker
```

Use:

```bash
docker info
```

first.

---

## ❌ 2. Ignoring Volumes

Volumes often consume huge storage.

Check:

```bash
docker volume ls
```

---

## ❌ 3. Forgetting Cleanup

Unused images and containers consume disk space.

Clean:

```bash
docker system prune
```

---

# 📝 Quick Summary

| Command | Purpose |
|---|---|
| `docker info` | 📁 Show root directory |
| `du -sh` | 💾 Directory size |
| `df -h` | 📊 Disk usage |
| `docker system df` | 📦 Docker storage usage |
| `docker system df -v` | 🔍 Detailed usage |

---

# 🎯 Final Understanding

```text
docker info
      ↓
Find Docker Root Directory 📁
      ↓
Check Size & Disk Usage 💾
```

Monitoring Docker root directory helps prevent storage issues and full disks.