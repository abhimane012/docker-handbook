# ⏹️ `STOPSIGNAL` Instruction in Dockerfile

## 🤔 What is `STOPSIGNAL`?

`STOPSIGNAL` defines which signal is sent to the container when it is stopped.

It tells Docker:
> "How should the container be stopped?"

---

# 🧾 Syntax

```dockerfile
STOPSIGNAL <signal>
```

---

# ✅ Example

```dockerfile
STOPSIGNAL SIGTERM
```

---

# 📌 Common Signals

| Signal | Meaning |
|---|---|
| `SIGTERM` | 🛑 Graceful stop |
| `SIGKILL` | 💥 Force kill |
| `SIGINT` | ⌨️ Interrupt (Ctrl+C) |

---

# ⚠️ Important Notes

- 🧠 Default is usually `SIGTERM`
- 🚀 Used for graceful shutdown
- 🧪 Mostly used in production systems

---

# 📝 Example

```dockerfile
FROM nginx

STOPSIGNAL SIGTERM
```

---

# ❤️ `HEALTHCHECK` Instruction in Dockerfile

## 🤔 What is `HEALTHCHECK`?

`HEALTHCHECK` tells Docker how to check if a container is healthy or not.

It helps detect:
- ❌ Broken apps
- ❌ Hung services
- ❌ Unresponsive containers

---

# 🧾 Syntax

```dockerfile
HEALTHCHECK CMD <command>
```

---

# ✅ Example

```dockerfile
HEALTHCHECK CMD curl -f http://localhost/ || exit 1
```

---

# ⏱️ With Timing Options

```dockerfile
HEALTHCHECK --interval=30s --timeout=5s --retries=3 CMD curl -f http://localhost/ || exit 1
```

---

# 📊 Health Status Types

| Status | Meaning |
|---|---|
| 🟢 healthy | Container is working |
| 🟡 starting | Container is initializing |
| 🔴 unhealthy | Container is broken |

---

# ⚙️ Example Dockerfile

```dockerfile
FROM nginx

HEALTHCHECK --interval=30s --timeout=5s --retries=3 \
  CMD curl -f http://localhost/ || exit 1
```

---

# 📋 Check Health Status

```bash
docker ps
```

Output:

```text
STATUS
Up 2 minutes (healthy)
```

or

```text
Up 2 minutes (unhealthy)
```

---

# ⚠️ Important Notes

- ❤️ Helps monitor running containers
- 🔄 Useful in production systems
- 🧪 Works with Docker restart policies
- 📄 Does NOT fix the container automatically

---

# 📝 Common Examples

```dockerfile
HEALTHCHECK CMD curl -f http://localhost || exit 1
HEALTHCHECK --interval=10s CMD wget --spider http://localhost
HEALTHCHECK CMD python healthcheck.py
```