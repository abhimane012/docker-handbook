# ⚙️ Resource Limits on Docker Containers

## 🤔 Why Do We Need Resource Limits?

By default, a container can use as many system resources as the host allows.

Without limits, one container may consume:

- 🧠 Too much memory
- ⚡ High CPU usage
- 💾 Excessive disk I/O
- 🚀 Too many processes

This can affect other containers and the host machine ⚠️

Docker allows setting limits to control resource usage.

---

# 🎯 Common Resource Limits

Docker can limit:

1. 🧠 Memory  
2. ⚡ CPU  
3. 🚀 Processes (PIDs)  
4. 💾 Block I/O  
5. 🔄 Swap Memory  
6. 🧩 CPU Cores  
7. 🔢 CPU Shares  

---

# 🧠 Limit Memory

```bash
docker run -m 512m nginx
```

Container can use:

```text
512 MB RAM
```

---

# 🧠 Memory + Swap Limit

```bash
docker run -m 512m --memory-swap 1g nginx
```

Meaning:

- RAM → `512MB`
- Total RAM + Swap → `1GB`

---

# ⚡ Limit CPU Usage

```bash
docker run --cpus="1.5" nginx
```

Container can use:

```text
1.5 CPU cores
```

---

# 🧩 Use Specific CPU Cores

```bash
docker run --cpuset-cpus="0,1" nginx
```

Container can run only on:

```text
CPU 0 and CPU 1
```

---

# 🔢 CPU Shares

```bash
docker run --cpu-shares=512 nginx
```

Higher value:

```text
Gets more CPU priority
```

Default:

```text
1024
```

---

# 🚀 Limit Number of Processes

```bash
docker run --pids-limit=100 nginx
```

Container cannot create more than:

```text
100 processes
```

---

# 💾 Block I/O Weight

```bash
docker run --blkio-weight=500 nginx
```

Controls disk I/O priority.

Range:

```text
10–1000
```

---

# 📋 Check Resource Usage

```bash
docker stats
```

Example:

```bash
CONTAINER    CPU %    MEM USAGE
nginx        10%      150MB
```

Shows live usage 📊

---

# 🧭 High-Level View

```text
Container 📦
      ↓
cgroups ⚙️
      ↓
CPU ⚡
Memory 🧠
Disk 💾
Processes 🚀
```

Docker uses Linux **cgroups** internally to enforce limits.

---

# 🌍 Real Example

Run Nginx:

```bash
docker run \
-m 1g \
--cpus=2 \
--pids-limit=200 \
nginx
```

Limits:

- 🧠 RAM → 1GB
- ⚡ CPU → 2 cores
- 🚀 Processes → 200

---

# 🚨 Common Beginner Mistakes

## ❌ 1. Forgetting Memory Limits

Unlimited containers may consume all RAM.

---

## ❌ 2. Setting Very Small Limits

Bad:

```bash
docker run -m 32m nginx
```

Application may crash.

---

## ❌ 3. Confusing CPU Shares with CPU Limits

CPU shares:

```text
Priority only
```

Not a hard limit.

---

## ❌ 4. Assuming Docker Limits Without Configuration

By default:

```text
No strict limits
```

---

# 📝 Quick Summary

| Option | Purpose |
|---|---|
| `-m` | 🧠 Memory limit |
| `--memory-swap` | 🔄 Swap limit |
| `--cpus` | ⚡ CPU limit |
| `--cpuset-cpus` | 🧩 Specific CPUs |
| `--cpu-shares` | 🔢 CPU priority |
| `--pids-limit` | 🚀 Process limit |
| `docker stats` | 📊 Monitor usage |

---

# 🎯 Final Understanding

```text
Container 📦
      ↓
Docker + cgroups ⚙️
      ↓
Resource Limits 🧠⚡💾
```

Resource limits prevent containers from consuming all system resources.