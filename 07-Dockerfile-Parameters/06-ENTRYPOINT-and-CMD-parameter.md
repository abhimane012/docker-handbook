# 🚀 `ENTRYPOINT` Instruction in Dockerfile

## 🤔 What is `ENTRYPOINT`?

`ENTRYPOINT` defines the main command that always runs when the container starts.

Used when:
- Container should behave like a fixed executable
- Main process should always run

---

# 🧾 Syntax

```dockerfile
ENTRYPOINT ["command"]
```

---

# ✅ Example

```dockerfile
ENTRYPOINT ["nginx"]
```

---

# 🐍 Python Example

```dockerfile
ENTRYPOINT ["python"]
```

---

# ⚠️ Important Notes

- 🚀 Always executes when container starts
- 🔒 Harder to override than `CMD`
- 📌 Best for fixed startup behavior

---

# 📝 Common Examples

```dockerfile
ENTRYPOINT ["nginx"]
ENTRYPOINT ["python", "app.py"]
ENTRYPOINT ["java", "-jar", "app.jar"]
```

---

# ▶️ `CMD` Instruction in Dockerfile

## 🤔 What is `CMD`?

`CMD` provides the default command or arguments for the container.

It runs when no command is provided during `docker run`.

---

# 🧾 Syntax

```dockerfile
CMD ["command"]
```

---

# ✅ Example

```dockerfile
CMD ["python", "app.py"]
```

---

# 🌐 Nginx Example

```dockerfile
CMD ["nginx", "-g", "daemon off;"]
```

---

# ⚠️ Important Notes

- 📄 Only one `CMD` should exist
- 📝 Last `CMD` overrides previous ones
- 🔄 Easy to override during `docker run`

Example:

```bash
docker run ubuntu ls
```

Here:
- `ls` overrides `CMD`

---

# 🔄 `ENTRYPOINT` vs `CMD`

| Feature | `ENTRYPOINT` | `CMD` |
|---|---|---|
| 🚀 Main executable | ✅ | ❌ |
| 📝 Default arguments | ❌ | ✅ |
| 🔒 Hard to override | ✅ | ❌ |
| 🔄 Easily replaceable | ❌ | ✅ |

---

# 🤝 Using `ENTRYPOINT` and `CMD` Together

```dockerfile
ENTRYPOINT ["python"]
CMD ["app.py"]
```

Final executed command:

```bash
python app.py
```

---

# 🔄 Override CMD

```bash
docker run my-image test.py
```

Result:

```bash
python test.py
```

`ENTRYPOINT` stays same ✅  
`CMD` changes ✅

---

# 📝 Common Examples

```dockerfile
CMD ["node", "server.js"]

ENTRYPOINT ["python"]

ENTRYPOINT ["java", "-jar"]
CMD ["app.jar"]
```