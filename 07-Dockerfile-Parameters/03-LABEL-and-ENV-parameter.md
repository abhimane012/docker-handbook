# 🏷️ `LABEL` Instruction in Dockerfile

## 🤔 What is `LABEL`?

`LABEL` adds metadata to a Docker image.

Used for:
- 👤 Author info
- 📄 Project details
- 🏷️ Version information
- 🔗 Documentation links

---

# 🧾 Syntax

```dockerfile
LABEL key=value
```

---

# ✅ Example

```dockerfile
LABEL maintainer="Abhishek Mane"
```

---

# 📝 Multiple Labels

```dockerfile
LABEL app="my-app" version="1.0"
```

---

# 🌍 Common Examples

```dockerfile
LABEL maintainer="admin@example.com"
LABEL version="1.0"
LABEL description="Python application"
```

---

# ⚠️ Important Notes

- 🏷️ Labels are metadata only
- 🚀 They do NOT affect container execution

---

# 🌐 `ENV` Instruction in Dockerfile

## 🤔 What is `ENV`?

`ENV` sets environment variables inside the container.

Used for:
- ⚙️ Configuration
- 🌐 Application settings
- 🔑 Runtime variables

---

# 🧾 Syntax

```dockerfile
ENV KEY=value
```

---

# ✅ Example

```dockerfile
ENV APP_ENV=production
```

---

# 📝 Multiple Variables

```dockerfile
ENV APP_ENV=production PORT=8080
```

---

# 🐍 Python Example

```dockerfile
ENV PYTHONUNBUFFERED=1
```

---

# 🌍 Access Environment Variable

Inside container:

```bash
echo $APP_ENV
```

---

# ⚠️ Important Notes

- 🌐 Environment variables are available inside container
- 🔒 Avoid storing secrets directly in Dockerfile

---

# 📝 Common Examples

```dockerfile
ENV NODE_ENV=production
ENV PORT=3000
ENV JAVA_HOME=/usr/lib/jvm/java-17
ENV PATH="/app/bin:$PATH"
```