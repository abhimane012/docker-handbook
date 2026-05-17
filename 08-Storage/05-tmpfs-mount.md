# 🧠 Docker tmpfs Mount

## 🤔 What is a tmpfs Mount?

A tmpfs mount stores data only in **system memory (RAM)** instead of writing it to disk.

This means:

- ⚡ Very fast access
- 💾 No disk usage
- 🔐 Good for temporary sensitive data
- ❌ Data disappears after container stops

Think of it like writing notes on a whiteboard 📝  
When power is gone, everything is erased.

---

# 🧾 Basic Syntax

```bash
docker run --tmpfs <container-path> <image>
```

or

```bash
docker run --mount type=tmpfs,target=<container-path>
```

---

# ✅ Example Using `--tmpfs`

```bash
docker run --tmpfs /app/temp nginx
```

Here:

- 🧠 `/app/temp` → Stored in RAM
- 💾 No data written to disk

---

# ✅ Example Using `--mount`

```bash
docker run --mount type=tmpfs,target=/cache nginx
```

This creates a tmpfs mount at:

```text
/cache
```

---

# ⚙️ What Happens Internally?

When container starts:

1. 🧠 Docker allocates memory
2. 🔗 Creates tmpfs mount
3. 📂 Container writes data into RAM
4. ⛔ Data never reaches disk

---

# 🧭 High-Level View

```text
Container 📦
      ↓
tmpfs Mount 🧠
      ↓
RAM 💾
```

No hard disk involved 🚫

---

# 🌍 Real-World Example

Suppose an application stores:

- 🔑 Temporary authentication tokens
- 📝 Session files
- ⚡ Cache data

You may not want these written to disk.

Use:

```bash
docker run --tmpfs /sessions nginx
```

---

# ⚡ Why Use tmpfs?

Benefits:

- 🚀 Faster read/write speed
- 🔐 Sensitive data avoids disk storage
- 💾 Reduces disk usage
- 🧹 Temporary data cleanup happens automatically

---

# 📏 Limit Memory Size

You can limit tmpfs size:

```bash
docker run --tmpfs /cache:size=200m nginx
```

Here:

- `200m` → Maximum RAM usage

---

# 🚨 Common Beginner Mistakes

## ❌ 1. Thinking Data Persists

tmpfs data is temporary.

Container stops:

```text
Data disappears ❌
```

---

## ❌ 2. Storing Database Data

Bad idea:

```text
MySQL data → tmpfs
```

Container restart:

```text
Database lost 💥
```

---

## ❌ 3. Using Too Much RAM

Large tmpfs allocations can consume system memory quickly ⚠️

---

# 🔄 tmpfs vs Volume vs Bind Mount

| Feature | tmpfs 🧠 | Volume 📁 | Bind Mount 🔗 |
|---|---:|---:|---:|
| Uses RAM | ✅ | ❌ | ❌ |
| Persists Data | ❌ | ✅ | ✅ |
| Managed by Docker | ❌ | ✅ | ❌ |
| Fast Access | ✅ | ❌ | ❌ |

---

# 📝 Quick Summary

| Command | Purpose |
|---|---|
| `docker run --tmpfs /data nginx` | 🧠 Create tmpfs mount |
| `--mount type=tmpfs` | 🔗 Modern syntax |
| `size=200m` | 📏 Limit RAM usage |

---

# 🎯 Final Understanding

```text
Container 📦
      ↓
tmpfs Mount 🧠
      ↓
RAM ⚡
      ↓
Temporary Data ❌💾
```

tmpfs mounts are best for fast, temporary, and sensitive data storage.