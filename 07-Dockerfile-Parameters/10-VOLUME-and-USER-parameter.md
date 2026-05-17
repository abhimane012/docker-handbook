# 💾 `VOLUME` Instruction in Dockerfile

## 🤔 What is `VOLUME`?

`VOLUME` creates a mount point inside the container for persistent storage.

It is used to:
- 💾 Store data outside container lifecycle
- 🗄️ Persist database files
- 📁 Share data between containers

---

# 🧾 Syntax

```dockerfile
VOLUME ["/path"]
```

---

# ✅ Example

```dockerfile
VOLUME ["/data"]
```

---

# 📊 Multiple Volumes

```dockerfile
VOLUME ["/data", "/logs"]
```

---

# ⚙️ What Happens Internally?

- Docker creates a storage area outside container
- Data written in `/data` survives container removal
- Managed by Docker volume system

---

# 🧪 Example Use Case

```dockerfile
FROM nginx

VOLUME ["/usr/share/nginx/html"]
```

This ensures website files persist 💾

---

# ⚠️ Important Notes

- 💾 Data is NOT deleted when container is removed
- 🔄 Used for databases and persistent apps
- 📦 Volume location is managed by Docker

---

# 📝 Common Examples

```dockerfile
VOLUME ["/data"]
VOLUME ["/var/lib/mysql"]
VOLUME ["/app/logs"]
```

---

# 👤 `USER` Instruction in Dockerfile

## 🤔 What is `USER`?

`USER` sets the user that runs container processes.

By default, Docker runs as `root`.

---

# 🧾 Syntax

```dockerfile
USER <username | uid>
```

---

# ✅ Example

```dockerfile
USER appuser
```

---

# 🔢 Using UID

```dockerfile
USER 1001
```

---

# ⚙️ Example Dockerfile

```dockerfile
FROM ubuntu

RUN useradd -m appuser

USER appuser

CMD ["bash"]
```

---

# 🔒 Why Use `USER`?

- 🔐 Security (avoid running as root)
- 🧑 Limit container permissions
- 🛡️ Reduce risk of system damage

---

# 📊 Before vs After

| Mode | Behavior |
|---|---|
| root (default) | 🔓 Full access |
| user (appuser) | 🔒 Limited access |

---

# ⚠️ Important Notes

- 👤 Must exist in image before using
- 🔐 Best practice for production containers
- 🚫 Avoid running apps as root

---

# 📝 Common Examples

```dockerfile
USER root
USER appuser
USER 1000
```

---

# 🧠 Quick Summary

| Instruction | Purpose |
|---|---|
| `VOLUME` | 💾 Persistent storage |
| `USER` | 👤 Set container user |

---

# 🎯 Final Understanding

```text
VOLUME 💾 → Keeps data safe outside container
USER 👤 → Controls who runs the container
```

Together they improve:
- 🔐 Security
- 💾 Data persistence
- ⚙️ Production readiness